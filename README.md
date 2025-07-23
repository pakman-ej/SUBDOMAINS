✅ Essential Tools to Enumerate Subdomains
🔧 1. Subfinder
Fast passive subdomain enumerator

Pulls from public sources (e.g. VirusTotal, Shodan, etc.)

bash
Copy
Edit
go install -v github.com/projectdiscovery/subfinder/v2/cmd/subfinder@latest
🔧 2. Amass
Active + passive enumeration

Brute-force, DNS scraping, scraping certs, and more

bash
Copy
Edit
go install -v github.com/owasp-amass/amass/v3/...@latest
🔧 3. Assetfinder
Very fast, passive, minimal output

bash
Copy
Edit
go install github.com/tomnomnom/assetfinder@latest
🔧 4. dnsx
Mass DNS resolution (after collecting subdomains)

bash
Copy
Edit
go install -v github.com/projectdiscovery/dnsx/cmd/dnsx@latest
🔧 5. shuffledns
Brute-force subdomain discovery using a wordlist and resolvers

bash
Copy
Edit
go install -v github.com/projectdiscovery/shuffledns/cmd/shuffledns@latest
🧱 Dependencies
To use all above tools, you’ll need:

✅ Go (Golang) installed:

bash
Copy
Edit
sudo apt install golang -y  # Ubuntu/Debian
✅ resolvers.txt (good public DNS resolvers for brute-force)

✅ wordlist.txt (top subdomain prefixes like login, api, dev, etc.)

Examples:

Resolvers: https://raw.githubusercontent.com/trickest/resolvers/main/resolvers.txt

Wordlist: https://github.com/danielmiessler/SecLists/blob/master/Discovery/DNS/subdomains-top1million-5000.txt

✅ Example Workflow
bash
Copy
Edit
# 1. Passive enum
subfinder -d x.com -o subfinder-x.txt

# 2. Brute-force using shuffledns
shuffledns -d x.com -w subdomains.txt -r resolvers.txt -o shuffledns-x.txt

# 3. Resolve live domains
dnsx -l shuffledns-x.txt -o live-x.txt
