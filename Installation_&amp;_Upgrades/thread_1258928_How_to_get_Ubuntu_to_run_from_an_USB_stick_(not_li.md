---
title: "How to get Ubuntu to run from an USB stick (not live)"
date: 2009-09-05
forum: Installation &amp; Upgrades
---

### Post by oblidor on 2009-09-05
I have read and search the net a lot, but what I find is related to making live USB sticks for install on some hard disk. 

What I want is a way to make a USB stick (16Gb) contain bootloader (grub or syslinux) and Xubuntu OS on an ext2 partition and a /home partition (ext2). What I want is a OS on a stick so to speak. So no matter which PC I use I can boot Xubuntu with the stick and work on my files on the stick.

I have seen a lot of solutions to live USBs using FAT fs and casper. I do not want neither. I want ext2 fs for OS and /home partition. My problem is to figure out a way to actually get grub on the stick so that I can boot a xubuntu system. 

Any help much appreciated

---

### Post by stlsaint on 2009-09-05
putting ubuntu on a usb is ver do-able...as i am not at my system right now i cant send you the links to see how its done step by step but just do a lil research on google and you will get alot of help.

---

### Post by oblidor on 2009-09-06
> **stlsaint said:**
> putting ubuntu on a usb is ver do-able...as i am not at my system right now i cant send you the links to see how its done step by step but just do a lil research on google and you will get alot of help.

Would much appreciate any info when you get back to your computer. I'll continue searching, but I'm mostly getting how to put live systems on usbs and that is not what I'm after.

I found a  gentoo recipe, but not sure that is ht e right way to do it: [http://www.blah-blah.ch/Mra/GentooOnUsbstick](http://www.blah-blah.ch/Mra/GentooOnUsbstick)

---

### Post by AmerNewbieInDE on 2009-09-06
there is a program for windows.. usbuntu.. you need linux iso, run usbuntu select the iso, and usbstick and checkmark make persistant (or something like that) when you run llinux off the stick, boot to persistant and it keeps all your settings and info.

---

### Post by oblidor on 2009-09-06
> **AmerNewbieInDE said:**
> there is a program for windows.. usbuntu.. you need linux iso, run usbuntu select the iso, and usbstick and checkmark make persistant (or something like that) when you run llinux off the stick, boot to persistant and it keeps all your settings and info.

As I have Ubuntu and not Windows, I guess there is a way to do this from Ubuntu as well. However I would guess this solution uses casper and fat?

I want to have login, add programs, users etc...

Thanks for the tip though

---

### Post by AmerNewbieInDE on 2009-09-06
well, not sure if this way works for a stick or not, but check my post here.

[http://ubuntuforums.org/showthread.php?t=1259010](http://ubuntuforums.org/showthread.php?t=1259010)

---

### Post by Fafler on 2009-09-06
I just did this:
[http://http://ubuntuforums.org/showthread.php?t=1258014]("http://http//ubuntuforums.org/showthread.php?t=1258014")

It should work for you too.

---

