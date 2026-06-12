---
title: "USB Drives, FAT32, and Ext4"
date: 2013-10-24
forum: Hardware
---

### Post by Tom_ZeCat on 2013-10-24
I'm sure most people here know what a sucky file system FAT32 is.  However, it does have the advantage of working on a thumb drive in both Linux and Windows PCs.  That's the only reason I can think of to use this format.  However, I have heard there's a driver that allows a Windows PC to read Ext4.  I'm thinking of trying that out.  If it works well, I could ditch FAT32 on my thumb drives and go with the superior Ext4 instead.  Then they would work for my occasional, but necessary, Windows session.  

Is there any other reason why Ext4 might not be a good choice for a thumb drive?  If so, is Ext3 a better option?

Edit: Btw, by USB drives, I mean flash drives, not USB-based external hard drives.

---

### Post by sudodus on 2013-10-25
All ext file system work well on flash drives. But if you intend to use it a lot (as an installed system), certain memory cells will be written very often, which will wear the flash memory.

One tweak to do is to add the option ***noatime*** in /etc/fstab for the root file system. Another possible tweak is to shut off ***journaling***. It makes it harder to recover from logical errors of the file system (for example at hard reset), and it is in a way similar to using and ext2 file system (instead of ext3 or ext4).

You can browse the internet and find many interesting links. I suggest you start with this one

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by Tom_ZeCat on 2013-10-27
Thanks, that's good info.  I could conceivably use ext2 if it's simpler and does less wear to the flash drive.

---

### Post by sudodus on 2013-10-28
Yes, but there are also other improvements (than journaling) in ext3 and ext4.

---

