---
title: "GRUB loads with XP CD in, error without the CD"
date: 2009-08-16
forum: Installation &amp; Upgrades
---

### Post by B-Ry on 2009-08-16
I get the No NTLDR Error when booting up normally, but if I have the Windows XP CD in the drive, GRUB loads fine. I have used the Recovery Console several times to copy the ntldr and ntdetect.com files to the Windows drive (and used fixboot and fixmbr). However, after I bootup without the CD, I get the error again! What's the deal?

---

### Post by presence1960 on 2009-08-16
Boot from the Ubuntu Live CD and choose "try ubuntu without any changes", when desktop loads open Firefox and come back here. Download to the desktop the Boot Info Script 0.32 from my signature line. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
```
This will create a RESULTS.txt file on the desktop. paste the entire contents of that file back here. Once pasted here highlight all text and click the # sign on the toolbar to place code tags around the text.

The info from that script will provide your setup details and boot process info.

---

