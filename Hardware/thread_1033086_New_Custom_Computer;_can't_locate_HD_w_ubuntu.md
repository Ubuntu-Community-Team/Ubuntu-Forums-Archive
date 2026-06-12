---
title: "New Custom Computer; can't locate HD w/ ubuntu"
date: 2009-01-07
forum: Hardware
---

### Post by Krauzy on 2009-01-07
Any info will be appreciated. I built my first computer and I'm currently running ubuntu 7.10 from disk in order to transfer files from my external hard drive to the internal hard drive of the new computer. I can see the internal HD in bios but not through ubuntu. The external HD shows up on the desktop fine.

---

### Post by linux_tech on 2009-01-07
what is output of:
```
sudo fdisk -l
```

---

### Post by Krauzy on 2009-01-07
Sorry I'm new to ubuntu how do i find the output? do i type that code in the terminal?

---

### Post by smurfgod on 2009-01-07
yea...just go to apps>accessories>then terminal



smurf   :D

---

### Post by Liquid 2 on 2009-01-07
Yeah, in the terminal.  It will prompt you for your password since it's a sudo command.

---

### Post by Krauzy on 2009-01-07
when i type it in i get 
Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors

---

### Post by Krauzy on 2009-01-07
In the system monitor it lists zero bytes for available disk space. I have a 150gb western digital HD inst i just cant access it.

---

### Post by linux_tech on 2009-01-07
Are you typing in 
sudo fdisk -l   <--- Thats a lowercase L

---

### Post by Krauzy on 2009-01-07
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sda doesn't contain a valid partition table

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641    c  W95 FAT32 (LBA)
**This is what i get**

---

### Post by Krauzy on 2009-01-07
what's the valid partition table?

---

### Post by linux_tech on 2009-01-07
Is the internal drive 150 GB?

---

### Post by melojo on 2009-01-07
Is this a new hardrive?

If so it needs to be partitioned and then formated.  Whatever operating system you plan on installing will partion and format before installation.

---

