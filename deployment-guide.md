# 🛡️ Palo Alto VM-Series Firewall Deployment on AWS 

## 🧩 Overview
This guide explains how to launch and configure a **Palo Alto VM-Series firewall** from **AWS Marketplace**, including interface setup and admin password configuration — all via **AWS GUI** and **firewall CLI**.

---

## 🪜 Steps

### 1️⃣ Launch from AWS Marketplace
1. Open [AWS Marketplace](https://aws.amazon.com/marketplace).  
2. Search for **“Palo Alto Networks VM-Series Next-Generation Firewall”**.  
3. Choose the version:  
   - **BYOL** (Bring Your Own License)  
   - **PAYG** (Hourly / Annual subscription)  
4. Click **Continue to Subscribe → Continue to Configuration → Continue to Launch**.  
5. In **Launch from EC2**, configure:  
   - **Instance type:** `m5.large`(depending on your requirements)  
   - **VPC & Subnet:** Choose your deployment network  
   - **Auto-assign Public IP:** **Enabled**  (better to assign EIP later)
   - **Security Group:** Allow inbound **HTTPS (443)** and **SSH (22)**  
6. Click **Launch Instance**.

---

### 2️⃣ Connect via SSH
1. Find the **Public IP** of the firewall in the EC2 console.  
2. Connect using your keypair:

`ssh -i <keypair.pem> admin@<EIP>`

3. Default login:  
   - **Username:** `admin`  
   - **Password:** `<blank>` (press Enter)  

4. Configure admin password:

1) configure
2) set mgt-config users admin password <new_password>
3) commit



---

### 3️⃣ Verify and Access Web GUI
1. Open the firewall web interface in your browser: `https://<EIP>`  
2. Login using your new **admin credentials**.  
3. Complete any post-deployment setup as needed.

---

### ✅ Tips
- Use **strong admin passwords** for security.  
- Ensure your **security groups** allow access from your management IP.  
- For production, consider **multi-AZ deployment** and **high availability**.


