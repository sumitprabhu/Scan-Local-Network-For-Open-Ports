# Scan-Local-Network-For-Open-Ports

# Task - Local Network Port Scanner using Nmap

## Objective

This project teaches you how to scan your **local network for open ports** to understand network exposure and potential vulnerabilities. You'll use **Nmap** to identify active devices, open ports, and services running on your local network.

---

## Tools Required

- [Nmap](https://nmap.org/download.html) – for network scanning  
- [Wireshark](https://www.wireshark.org/) – for packet analysis

---

## Task Steps

### 1. Install Nmap

Download and install the latest version of Nmap from:  
[https://nmap.org/download.html](https://nmap.org/download.html)

Ensure Npcap is installed when prompted during installation (required for SYN scans on Windows).

---

### 2. Find Your Local IP Range

To determine your IP address and subnet:

- **Windows:**
  ```powershell
  ipconfig

### 3. Perform a TCP SYN Scan
Use a SYN scan (-sS) to find open TCP ports quickly and discreetly.

- **Windows:**
  ```powershell
  nmap -sS <IP address/24>

### 4. Record Open Ports and IPs
Once Nmap completes the scan:
-Note active devices
-List open ports per IP
-Identify service names

### 5. Analyze with Wireshark
To go deeper, open Wireshark during the Nmap scan to capture traffic.

tcp.flags.syn == 1 && tcp.flags.ack == 0 – SYN packets
ip.addr == 192.168.1.x – filter specific devices

### 6. Research Common Services
For every open port/service:
- Understand what it does (e.g., SSH = secure remote login)
- Look up its default port number
- Search for known vulnerabilities (CVEs)

### 7. Identify Security Risks
135 -> MS-RPC -> Exploited by Malware
139 -> NetBIOS -> Name spoofing, data leaks
445 -> SMB -> Ransomware like WannaCry, Password Hash Capture
Take action:
- Close unused ports
- Update outdated software
- Restrict access via firewall
- Use encryption and strong auth

### 8. Save Scan Results
nmap -sS 192.168.1.0/24 -oN scan_results.txt
