---
title: "[SOLVED] Cannot copy files FROM External USB Drive"
date: 2008-12-09
forum: Hardware
---

### Post by firespydr on 2008-12-09
Hello,

I have a Western Digital WDC3200 320gb external hdd. I believe it's formated in Fat32 (how can I check?). I am running the latest kernel (updated yesterday) and Ubuntu 8.10 Intrepid Ibex on a Dell Inspiron 1501. I am unable to copy files from the hdd to the filesystem, I am attempting to copy my lampp htdocs folder backup, onto the filesystem. I can open files off the externa; drive, copy files from the Ubuntu to the external. 

It sounds like a permissions issue, but I am new to this and not sure how to fix it. 

Here is the Lsusb output:

lsusb
**Bus 006 Device 004: ID 1058:0910 Western Digital Technologies, Inc. **
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 045e:008a Microsoft Corp. Wireless Keyboard and Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 046d:08d8 Logitech, Inc. QuickCam for Notebook Deluxe
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by taurus on 2008-12-09
Can you post the outputs of these commands from a terminal?

```
sudo fdisk -l
df -h
```

---

### Post by firespydr on 2008-12-09
> **taurus said:**
> Can you post the outputs of these commands from a terminal?

```
sudo fdisk -l
df -h
```
I figured it out. I ran gksudo nautilus and I was able to fix it. I was trying it as a normal user.

---

### Post by taurus on 2008-12-09
You can write it to as a regular user if you unmount it first and then remount it with the "-o umask=000" option.

---

