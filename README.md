
# Samba Server Setup

A step-by-step guide to setting up a Samba server for file sharing on Ubuntu 20.04. This project is open source and licensed under GNU GPL v3.0.

---

## 🚀 Quick Start

### 1. Install Ubuntu 20.04 Server
Set up your server with Ubuntu 20.04.

### 2. Update & Install Samba
```bash
sudo apt-get update
sudo apt-get install samba
```

### 3. Backup the Default Samba Config
```bash
sudo cp /etc/samba/smb.conf /etc/samba/smb.conf.org
```

### 4. Create Shared Directories
```bash
sudo mkdir /home/sharefolder
sudo mkdir /media/fileserver/shareusb
```
- `/home/sharefolder` is for main memory sharing.
- `/media/fileserver/shareusb` is for external storage (e.g., USB drives).

### 5. Configure Samba Shares
Edit the Samba config file:
```bash
sudo nano /etc/samba/smb.conf
```
Scroll to the end and add:
```ini
[sharefolder]
   comment = 1st folder
   path = /home/sharefolder
   browsable = yes
   read only = no
   writeable = yes

[shareusb]
   comment = usb folder
   path = /media/fileserver/shareusb
   browsable = yes
   read only = no
   writeable = yes
```
Save and exit (`Ctrl+X`, then `Y`, then `Enter`).

### 6. Restart Samba Service
```bash
sudo service smbd restart
```

### 7. Set Samba Password for User
```bash
sudo smbpasswd -a root
```

### 8. Allow Samba Through Firewall
```bash
sudo ufw allow samba
```

### 9. Check Your Server's IP Address
```bash
ifconfig
# or
ip addr
```

---

## 📝 Documentation
- See `samba server.docx` for a comprehensive, step-by-step guide with screenshots and troubleshooting tips.

## 📄 License
This project is licensed under the GNU General Public License v3.0. See the LICENSE file for details.

---

*Created and maintained by Xhon Pelushi. Contributions and suggestions are welcome!*
