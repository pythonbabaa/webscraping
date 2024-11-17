# Web Scraping Tool for Faculty Emails and Links

This project is a **web scraping tool** built in Python, designed to extract email addresses and links from university faculty webpages. The tool uses libraries such as `BeautifulSoup`, `re`, and `requests` to navigate web pages, filter relevant content, and scrape faculty contact information.

---

## **Features**
- Extracts all unique **hyperlinks** and **email addresses** from specified web pages.
- Filters links based on specific keywords to avoid unnecessary pages (e.g., `.pdf`, `students-resource`, etc.).
- Uses **regex** to match and retrieve email addresses from HTML content.
- Scrapes multiple faculty pages efficiently and handles errors gracefully.

---

## **Dependencies**
This project relies on the following Python libraries:
- `re` for regular expressions to match email patterns.
- `requests` to fetch web pages.
- `urllib` for handling URLs.
- `BeautifulSoup` from `bs4` for parsing HTML content.
- `pandas` (optional) for structured data handling.

To install the required libraries, run:
```bash
pip install requests beautifulsoup4 pandas
git clone <your-repository-url>
cd <your-directory-name>
python scraper.py
url = "https://www.bahria.edu.pk/bulc/management-sciences-faculty/"
r = requests.get(url)
html_content = r.content
soup = BeautifulSoup(html_content, 'html.parser')
anchors = soup.find_all('a')
all_links = set()
for link in anchors:
    if (link.get('href') != '#'):
        link = link.get('href')
        all_links.add(link)
def scrape(url):
    r = requests.get(url)
    html_content = r.content.decode()
    email_addresses = re.findall("[\w._%+-]{1,20}@[\w.-]{2,20}.[A-Za-z]{2,3}", html_content)
    for items in email_addresses:
        all_emails.add(items)
    return all_emails
substring1 = "https://www.bahria.edu.pk"
substring2 = ".pdf"
substring3 = "students-resource"
for i in all_links:
    if (substring2 not in i) & (substring3 not in i):
        scrape(i)
