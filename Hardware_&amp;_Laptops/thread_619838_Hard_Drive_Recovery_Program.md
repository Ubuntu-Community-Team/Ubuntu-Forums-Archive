---
title: "Hard Drive Recovery Program??"
date: 2007-11-21
forum: Hardware &amp; Laptops
---

### Post by whos2know on 2007-11-21
Hi, 

My 160GB hard drive has crashed..... It's a NTFS format and Ubuntu can read how big it is but cannot mount it.  I am pretty sure it's in bad shape... I need a program to recover my information.... what programs are there that will help me out that can help me??? PLEASE!!

thank you!!

---

### Post by taurus on 2007-11-21
What is the error message when you try to mount that ntfs harddrive by hand?

---

### Post by whos2know on 2007-11-22
hi, thank you for the response!! I used testdisk and I found out in fact it isn't a ntfs drive but a fat 32.  The error I get is a read/write error.  Any idea's how I can get my info back?  Thanks!!

Bobby

ps happy turkey day!!!

---

### Post by taurus on 2007-11-22
What's the output of this command from a terminal?

```
sudo fdisk -l
```

---

### Post by whos2know on 2007-11-23
this is what comes up.... 

> Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x94e494e4

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9402    75521533+  83  Linux
/dev/hda2            9403        9729     2626627+   5  Extended
/dev/hda5            9403        9729     2626596   82  Linux swap / Solaris

Unable to read /dev/sda



thank you!!

Bobby

---

### Post by whos2know on 2007-12-11
bump

---

### Post by froy02 on 2007-12-11
I use western digital and maxtor drives.  They come with installation disks where one of their utilities is restore mbr.  It looks like your mbr is corrupted.

But I do not know if this will make you recover your data.

Maybe this something i should experiment with since my hard drives are plugged-in from the front of my computers.

---

### Post by whos2know on 2007-12-14
this drive is a maxtor.... i don't have any software with it... is there anywhere i can retrieve some?  thanks for you help!! :)

---

### Post by psusi on 2007-12-14
After the fdisk -l, check the last few lines of the output of dmesg for errors.  It looks like your disk is toast though.

---

