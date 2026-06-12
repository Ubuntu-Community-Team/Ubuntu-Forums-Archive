---
title: "Enabling BIOS pasword protected SSD drive in Ubuntu 12.10"
date: 2013-02-24
forum: Hardware
---

### Post by jnelken on 2013-02-24
I have IBM Thinkpad laptop with OCZ Vertex 4 SSD drive with Windows 7 - /dev/sda. This drive when using HD password in Bios (which I am) is automatically encrypted.

When UBUNTU 12.10 is installed on second hard drive - /dev/sdb - (USB attached) and booted from it - it cannot even mount Windows 7 SSD drive.

How can I make UBUNTu "see" my SSD drive? I am assuming that somehow entering somewhere HDD password would be sufficient. I would like *NOT* to lose my Windows 7 installation.

Any suggestions will be appreciated

---

### Post by thermion on 2013-02-24
Are you sure this SSD is not encrypetd/decrypted within Windows 7 (using bitlocker)?
How do you exactly decrypt this drive?

---

### Post by jnelken on 2013-02-24
I am *not* using bitlocker. This SSD drive uses AES256 encryption.

BIOS disk password - when set - triggers encryption in firmware of the drive. Whole disk is encrypted - including partition table and MBR.

Ubuntu can see this drive only when BIOS disk password is disabled - but this unfortunately is in violation of the company policy :-(

---

