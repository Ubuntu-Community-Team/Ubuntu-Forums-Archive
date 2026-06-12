---
title: "Unifying a Partitioned USB stick"
date: 2009-11-06
forum: Hardware
---

### Post by CheshireMac on 2009-11-06
Hey folks. I'm trying to get my 2gb usb stick back to a single partition instead of what was a failed attempt at creating a boot-stick from two years ago. I can't seem to do it in Gparted, and I'm wondering if I'm just not doing something properly. Any thoughts would be appreciated.

---

### Post by Fire_Chief on 2009-11-06
Should be as straightforward as deleting all of the existing partitions on the USB stick and then creating a new one that is the full size of the drive. What kind of problems are you experiencing?

---

### Post by adrianx on 2009-11-06
> **CheshireMac said:**
> Hey folks. I'm trying to get my 2gb usb stick back to a single partition instead of what was a failed attempt at creating a boot-stick from two years ago. I can't seem to do it in Gparted, and I'm wondering if I'm just not doing something properly. Any thoughts would be appreciated.
First, ensure that your usb stick is unmounted. You can do that from within GParted. 
The next step would be to delete all the partitions (right-click > Delete). After that, there should be only "unallocated space" on it. Right-click the unallocated space, and click on "New". The rest should be pretty straightforward. 

P.S. If you want Windows to be able to read the usb stick, I suggest formatting it to fat32 or ntfs.

---

### Post by CheshireMac on 2009-11-06
Great. I deleted the partitions and am ready to format. I'm going with ext3 for now, but what's the best format for data storage?

---

### Post by adrianx on 2009-11-06
> **CheshireMac said:**
> Great. I deleted the partitions and am ready to format. I'm going with ext3 for now, but what's the best format for data storage?
Ext3 is fine, but if you ever want to plug it into a Windows machine, you will need special Windows drivers for reading ext3. 

Most usb sticks are formatted with FAT when you buy them.

If you are sure that you are only going to use your USB stick with Linux, then go for ext3/4. Your file permissions will be preserved.

If you want to be able to read your files from both Windows and Linux, I would suggest FAT32 or NTFS. Your will lose your file permissions, but sometimes it doesn't matter.

**Edit:** I don't have anything formatted with NTFS at the moment, but in FAT32 all my permissions change to read, write, execute for the owner, nothing for group or other (rwx------). I think it is the same when you use NTFS.

For things like Photos/Videos, Music.... that's fine.

---

