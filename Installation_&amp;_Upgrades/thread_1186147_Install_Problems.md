---
title: "Install Problems"
date: 2009-06-13
forum: Installation &amp; Upgrades
---

### Post by Joshua Mayer on 2009-06-13
I downloaded the Desktop ISO from the Ubuntu homepage, and burnt it to a CD at 4x speed. When I boot off the CD, I select Install Ubuntu and it just freezes on the main menu and doesn't go anywhere. I clicked Check Disk for Defects and then it pops up saying error reading boot CD. I have downloaded the ISO twice and both times it has the problem. 

What can be causing this??

---

### Post by _Purple_ on 2009-06-13
Have you checked the MD5SUM of the iso file after downloading? Here is the link: 
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by Joshua Mayer on 2009-06-13
They MD5 hashes are the same.

---

### Post by _Purple_ on 2009-06-13
You can try to install using a USB stick and see if it works.
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by Joshua Mayer on 2009-06-13
I just looked at the instructions and I don't understand them. It doesn't really say how to do it on Windows. Could someone please tell me how to do it on Windows?
 
I am currently using Windows XP

---

### Post by _Purple_ on 2009-06-13
First install [UNetbootin](http://unetbootin.sourceforge.net/) from [ this](http://sourceforge.net/project/downloading.php?groupname=unetbootin&filename=unetbootin-windows-344.exe&use_mirror=nchc) link. Then follow the steps under UNetbootin (GUI-based, runs from either Windows or Linux) in [this](https://help.ubuntu.com/community/Installation/FromUSBStick) page. Then you can boot from the USB stick and install.

---

### Post by Joshua Mayer on 2009-06-13
Ok, thanks. I have 1 4gb USB which has stuff on it I can't delete, it also has a u3 system on it. Can I leave that stuff on it and use the USB to install Ubuntu?

---

### Post by _Purple_ on 2009-06-13
I am not familiar with u3. In case it doesn't work, you might have to partition and format the USB stick.

---

### Post by Joshua Mayer on 2009-06-13
I booted off the USB after following the instruction. The Ubuntu loading screen appears and then all these errors come up. Some of the errors are:
```
SQUASHFS error: Unable to read fragment cache block [2767a54b]
```
```
SQUASHFS error: Unable to read page, block 2767a54b, size d7f2
```
```
SQUASHFS error: sb_bread failed reading block 0x9da1f
```
 
And a few others come up. Could this be caused by not formatting the USB before adding files to it? How can I fix?

---

### Post by _Purple_ on 2009-06-13
May be that is the reason. You can try to make a partition and format it in FAT32 and install there. See if it works.

---

### Post by Joshua Mayer on 2009-06-13
I formatted the USB and added the files back on, and booted it. All those errors I said before came up more times than before and "fail" written in red came up as well.

Please help me! I really want to use Ubuntu!:(

---

### Post by _Purple_ on 2009-06-13
I don't have any experience with U3. Please check this thread and hope you find it helpful
[http://ubuntuforums.org/showthread.php?t=739222](http://ubuntuforums.org/showthread.php?t=739222)

---

### Post by Joshua Mayer on 2009-06-13
I removed U3 and put all the files back on the USB, and I get the same errors.

---

