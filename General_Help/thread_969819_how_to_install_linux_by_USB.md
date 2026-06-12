---
title: "how to install linux by USB"
date: 2008-11-03
forum: General Help
---

### Post by snakeman21 on 2008-11-03
All right, here's my situation:  I have a computer with no CD drive at all.  Currently, it has Windows XP (ugh!) and I would like to replace windows with Ubuntu.  I have installed Linux operating systems before, but I've always used a CD.  Can I install Ubuntu from a usb stick?  I tried Googling this, and the answer seems to be yes, but I couldn't seem to make it work.  Any advice would be appreciated!

---

### Post by LateNiteTV on 2008-11-03
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by C.S.Cameron on 2008-11-03
From windows you can download the Ubuntu iso and Unetbootin.
Unetbootin will install the iso to a bootable flashdrive.
You can use this flash drive to install Ubuntu just like the CD.
Before booting, select the flash drive as first HDD in BIOS.

---

### Post by snakeman21 on 2008-11-03
I've been to that page, I must have read it twenty times by now.  I can't get any of the methods described to work.  First of all, I've used the utility in linux to create a bootable usb before, so I know it works.  Problem is... I don't have a computer set up with ubuntu.  Plus, I can't get Unetbootin or syslinux to work.

---

### Post by C.S.Cameron on 2008-11-03
I can't think  of anything better than Unetbootin for your situation.
What problems are you having with it.

---

### Post by snakeman21 on 2008-11-03
well, I open the program, choose "ubuntu", specify USB and drive letter "F" and hit ok.  But when I click ok, the window disapears, and nothing else happens.  Then, when I restart and try to boot from the usb stick, it still isn't bootable.

---

### Post by C.S.Cameron on 2008-11-03
Your selecting Distribution then Ubuntu?
I think this downloads Ubuntu off the Net.
What works for me is to select Diskimage, then point to where I have downloaded the iso.

---

### Post by snakeman21 on 2008-11-03
Okay, well, I made some progress, or so it seemed.  When I rebooted, a menu came up that *looked* like a normal dual boot menu.  But it only had one option, which was "Default".  At the bottom, it said, "press [tab] to edit options.  The tab key did nothing.  
There must be something I'm doing wrong here.  I'm trying to install Xubuntu 8.04, or "Hardy Heron".  Can you walk me through EVERY step?  Just so I know I'm not missing anything?  I appreciate your help

---

### Post by snakeman21 on 2008-11-03
oh yeah, I forgot to mention... choosing "default" literally does nothing.

---

### Post by C.S.Cameron on 2008-11-04
In Windows, I downloaded Unetbootin and ubuntu-8.04.1-desktop-i386.iso.
Started Unetbootin and selected Diskimage.
Hit the button to the right, found and selected the iso.
At the bottom I kept Type=USB Drive, then selected the correct drive letter, then hit OK.
A new box came up showing progress. I waited while it completed the 4 steps, (about 5 minutes).
When complete, hit Exit and Safely Remove USB Mass Storage Device.
Rebooted and selected Default.
Computer then booted into Ubuntu.

---

### Post by snakeman21 on 2008-11-04
Thank you, I'll give that a try.  Hopefully, next time I post, I won't be using wondows!

---

### Post by snakeman21 on 2008-11-04
One more question:  You can put unetbootin right on the desktop in windows, but where do you save the ubuntu-8.04.1-desktop-i386.iso. file?  Does it have to be on the usb stick? or should it be somewhere on the hard drive?

---

### Post by C.S.Cameron on 2008-11-05
I just download the iso to my Windows desktop so it is easy to find.

---

