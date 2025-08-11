<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe and inspect various network traffic to and from Azure Virtual Machines using Wireshark. This project also involves experimenting with Azure Network Security Groups (NSGs) to control traffic and analyzing different types of traffic protocols such as ICMP, SSH, DHCP, DNS, and RDP.

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>Actions and Observations</h2>

**1. Observing ICMP Traffic**
- Install Microsoft Remote Desktop on your Mac and connect to the Windows 10 VM.
- Install [Wireshark](https://www.wireshark.org) within the Windows 10 VM.
- Open Wireshark and start a packet capture.
- Filter for ICMP traffic in Wireshark.
- Retrieve the private IP address of the Ubuntu VM and attempt to ping it from the Windows 10 VM.
- Observe ping requests and replies in Wireshark.
- From the Windows 10 VM, open Command Line or PowerShell, and ping a public website (e.g., `www.google.com`).
- Observe the ICMP traffic in Wireshark.

<img width="330" alt="Screenshot 2025-01-23 at 8 37 43 PM" src="https://github.com/user-attachments/assets/ca8cf10f-8484-4004-bd93-577c7cb58cd2" />
<img width="1125" alt="Screenshot 2025-01-23 at 8 39 35 PM" src="https://github.com/user-attachments/assets/9909a9be-310e-48e5-843d-f7af9c0d32e7" />
<img width="348" alt="Screenshot 2025-01-23 at 8 40 11 PM" src="https://github.com/user-attachments/assets/0a218b2e-cf77-4c51-82f9-3cbcd945b44f" />
<img width="1203" alt="Screenshot 2025-01-23 at 8 41 26 PM" src="https://github.com/user-attachments/assets/d0954a80-3928-4df9-a5ee-6c2d45d616bc" />
<img width="1062" alt="Screenshot 2025-01-23 at 8 41 43 PM" src="https://github.com/user-attachments/assets/9070aab0-441e-486e-9bbc-bbc7d5ade299" />
<img width="1021" alt="Screenshot 2025-01-23 at 8 42 07 PM" src="https://github.com/user-attachments/assets/a9ad6c52-9c64-4daf-b4d5-f3a293b8bb2b" />
<img width="408" alt="Screenshot 2025-01-23 at 8 42 34 PM" src="https://github.com/user-attachments/assets/be42169a-bde0-4cf3-88fe-9ae1a74bffda" />
<img width="973" alt="Screenshot 2025-01-23 at 8 42 40 PM" src="https://github.com/user-attachments/assets/10f7458a-3cf3-41a8-9c71-64c47ffc770b" />


**2. Configuring a Firewall (Network Security Group)**
- Initiate a perpetual/non-stop ping from the Windows 10 VM to the Ubuntu VM.
- Open the Network Security Group (NSG) associated with the Ubuntu VM and disable inbound ICMP traffic.
- Return to the Windows 10 VM and observe the ICMP traffic and command line ping activity in Wireshark.
- Re-enable inbound ICMP traffic in the NSG.
- Back in the Windows 10 VM, observe the ICMP traffic and ping activity resuming in Wireshark.
- Stop the ping activity.

<img width="530" alt="Screenshot 2025-01-23 at 8 43 51 PM" src="https://github.com/user-attachments/assets/a5783f9e-04fc-49c2-bbee-15fb136dca64" />
<img width="1031" alt="Screenshot 2025-01-23 at 8 44 51 PM" src="https://github.com/user-attachments/assets/f1203b08-9d32-4a0c-b879-1f09eb7b1065" />
<img width="595" alt="Screenshot 2025-01-23 at 8 45 15 PM" src="https://github.com/user-attachments/assets/5afb5a10-235c-429c-b0fc-8c84c86dbc5f" />
<img width="1073" alt="Screenshot 2025-01-23 at 8 45 41 PM" src="https://github.com/user-attachments/assets/ca10540d-e486-44a1-8242-974abc88717f" />
<img width="651" alt="Screenshot 2025-01-23 at 8 45 51 PM" src="https://github.com/user-attachments/assets/bde2cd31-5183-4876-922d-1e0859b31a6f" />


**3. Observing SSH Traffic**
- In the Windows 10 VM, open Wireshark and start a packet capture.
- Filter for SSH traffic in Wireshark.
- Using PowerShell in the Windows 10 VM, SSH into the Ubuntu VM using its private IP address:
  - `ssh labuser@<private IP address>`
- Type commands (e.g., username, password) in the Linux SSH session and observe SSH traffic in Wireshark.
- Exit the SSH connection by typing `exit` and pressing [Enter].

<img width="769" alt="Screenshot 2025-01-23 at 8 51 34 PM" src="https://github.com/user-attachments/assets/b45ae71b-c8c4-416d-9552-1c01d1ba1f46" />
<img width="643" alt="Screenshot 2025-01-23 at 8 52 03 PM" src="https://github.com/user-attachments/assets/7081f687-49e5-46c7-8ac7-b3abe72c10d6" />
<img width="1213" alt="Screenshot 2025-01-23 at 8 52 15 PM" src="https://github.com/user-attachments/assets/be9e50ce-9ab2-4c6e-9325-0949854a3149" />


**4. Observing DHCP Traffic**
- Back in Wireshark, filter for DHCP traffic.
- In the Windows 10 VM, attempt to issue a new IP address using the Command Line:
  - `ipconfig /renew`
- Observe DHCP traffic appearing in Wireshark.

<img width="737" alt="Screenshot 2025-01-23 at 8 53 19 PM" src="https://github.com/user-attachments/assets/d1918c31-508f-4f35-b7c5-f179827af4f1" />
<img width="910" alt="Screenshot 2025-01-23 at 8 53 42 PM" src="https://github.com/user-attachments/assets/e4daa4b5-fff0-4e7f-9738-6feecbb805cf" />


**5. Observing DNS Traffic**
- Back in Wireshark, filter for DNS traffic.
- In the Windows 10 VM, use `nslookup` to resolve the IP addresses of `google.com` and `disney.com`:
  - `nslookup google.com`
  - `nslookup disney.com`
- Observe DNS traffic in Wireshark.

<img width="430" alt="Screenshot 2025-01-23 at 8 55 00 PM" src="https://github.com/user-attachments/assets/d2cc1904-7add-4e08-84c5-5e9460ebfed4" />
<img width="771" alt="Screenshot 2025-01-23 at 8 54 42 PM" src="https://github.com/user-attachments/assets/7b93d32e-4454-4952-bf8e-f82dd3305d9e" />


**6. Observing RDP Traffic** 
- Back in Wireshark, filter for RDP traffic using the filter `tcp.port == 3389`.
- Observe the non-stop traffic being transmitted.
  - Explanation: RDP traffic constantly transmits because it streams a live view from one computer to another, leading to continuous traffic.

<img width="678" alt="Screenshot 2025-01-23 at 8 55 42 PM" src="https://github.com/user-attachments/assets/cd9bc603-1094-4c42-940b-a19a2df14e2b" />


<h2>Purpose</h2>

The purpose of this project is to enhance understanding of network traffic flow and security configurations within cloud environments, providing foundational knowledge for managing and troubleshooting Azure-based networked systems.
