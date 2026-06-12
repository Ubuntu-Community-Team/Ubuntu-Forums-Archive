---
title: "Can't find NEW SATA drive."
date: 2008-07-02
forum: Hardware
---

### Post by trappleye on 2008-07-02
I've been running Ubuntu on my laptop and desktop for about a year now. Today I installed a Western Digital Caviar SE16 500GB SATA Hard Drive into my desktop (model# WD50000KSRTL). I have my OS installed on a second P-ATA drive, so this new HD is strictly for storage. However when I boot to Ubuntu (Hardy), I can't find it in the /media, /dev, or /mnt directories. I'd like to make a shortcut to it on the desktop, but I need to find it first. When I boot to bios both HD's are recognized, and displayed and configured properly.

---

### Post by logos34 on 2008-07-02
Use gparted to format the drive ext3.  Follow this guide:
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

To use 'UUID=' instead of '/dev/drive' format in /etc/fstab, get the UUID for the new drive with any of these commands:

sudo blkid

sudo vol_id /dev/drive

ls -l /dev/disk/by-uuid

Good luck.

---

