# Task3 Cybersecurity internship 

🔐 Vulnerability Assessment Report
🧾 Overview
This report documents the process and results of conducting a vulnerability assessment using tools like OpenVAS/GVM on a target system (e.g., localhost or a remote IP). It includes installation steps, scanning procedure, findings, severity ratings, and recommended remediation steps.

📚 Table of Contents
Prerequisites

Installation & Setup

Running the Scan

Understanding the Results

Recommendations & Mitigations

Next Steps

Contributing

✅ Prerequisites
A Linux OS (e.g., Ubuntu or Kali Linux)

Terminal access with sudo privileges

Active internet connection to download packages and vulnerability feeds

⚙️ Installation & Setup
🔧 On Ubuntu (e.g., 18.04 or newer)
sudo apt update && sudo apt upgrade -y
sudo apt install software-properties-common sqlite3 -y
sudo add-apt-repository ppa:mrazavi/openvas
sudo apt update
sudo apt install openvas -y
sudo openvas-nvt-sync
sudo openvas-scapdata-sync
sudo openvas-certdata-sync
sudo service openvas-scanner restart
sudo service openvas-manager restart
sudo service openvas-gsa restart
sudo openvasmd --rebuild --progress
This setup installs OpenVAS using a PPA, fetches required vulnerability databases, and restarts relevant services.

🐍 On Kali Linux
sudo apt install gvm -y  # GVM is the newer OpenVAS
sudo gvm-setup
sudo gvm-check-setup
sudo gvm-start
🚀 Running the Scan
Open your browser and go to: https://127.0.0.1:9392

Log in using your GVM admin credentials

Create a new scan task targeting:

localhost

A specific IP address

Virtual Machine (VM)

Start the scan and wait for it to complete

Export and save the scan report (PDF, XML, or HTML format)

🧠 Understanding the Results
Each report entry includes:

Description of the issue

Severity level (Low, Medium, High, Critical)

CVSS score

CVE reference, if applicable

Mitigation recommendations

🩺 Recommendations & Mitigations
Issue	Severity	Recommendation
DCE/RPC Enumeration on port 135	Medium	Block port 135 via internal/external firewall
Spooler Service on port 49668	Medium	Disable or patch the vulnerable print spooler
Event Log Service, KeyIso, etc.	Low/Med	Review settings and enforce least privilege policy
🔄 Next Steps
Apply all recommended security fixes

Re-scan the system to verify mitigations

Save new scan results for version tracking

Consider using GitHub Actions or CI/CD pipelines for automated recurring scans

🤝 Contributing
You can contribute by:

Improving the mitigation steps

Adding shell scripts for automated setup and scanning

Embedding badges or links to live dashboards
