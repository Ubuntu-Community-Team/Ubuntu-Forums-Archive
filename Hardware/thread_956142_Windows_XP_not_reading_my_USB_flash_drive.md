---
title: "Windows XP not reading my USB flash drive"
date: 2008-10-22
forum: Hardware
---

### Post by Rice8002 on 2008-10-22
Hello, I am running Windows XP Professional through Sun xVM VirtualBox, and when I insert my USB flash drive into my computer, Windows doesn't seem to want to find it.  It's not under 'Computer' or 'Computer Management'==> 'Device  Manager'.

I have tried deleteing all the things under 'Universal Serial Bus controllers', then rebooting and letting them reinstall, but with no luck.  

In Virtual Box i am running

Microsoft Windows XP
Professinal
Version 2002
Service Pack 3

Intel(R) Core(TM)2 Duo CPU
T5250 @1.50GHz
1.37 GHz, 192 MB of RAM

any helpful tips would be great, I just loaded Ubuntu onto my computer today and so far love it, so i dont want to leave it =P

---

### Post by Rice8002 on 2008-10-22
Sry had to cut the situation short because I was typing in class and class was dismissed.

but to go further into the situation, I have enabled USB controller and USB 2.0 (EHCI) controller.  Not sure what to put into the other box.

My computer does find my usb thumb drive while I'm in Ubuntu (my main OS)

not sure what else to do.

---

### Post by Rice8002 on 2008-10-23
if anyone else is having this problem, i found that email yourself the files you need to put on the flash drive (I use CSE editor for my XHTML class which is windows ONLY *sigh* haha) then just download and save the file to the flash drive is an easy way around the problem.  I'm sure there is a way to make VirtualBox read a flash drive, so I'll post it here if I happen to find it down the road

---

### Post by Rice8002 on 2008-12-08
Well looks like this thread didn't get used at all :-(, but I found that just running the the programs in WINE solved the issue.

---

### Post by maddog46113 on 2008-12-08
> **Rice8002 said:**
> Well looks like this thread didn't get used at all :-(, but I found that just running the the programs in WINE solved the issue.
 

Here is this, hope it helps solve your issue :)

[https://help.ubuntu.com/community/VirtualBox#USB](https://help.ubuntu.com/community/VirtualBox#USB)

---

### Post by russo.mic on 2008-12-08
Did you format the USB drive ext3?  if so, that could be the problem.  FAT32...just something to look at.

Russo

---

