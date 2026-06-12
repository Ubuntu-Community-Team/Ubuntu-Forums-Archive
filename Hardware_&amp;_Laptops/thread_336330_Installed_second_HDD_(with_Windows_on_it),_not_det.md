---
title: "Installed second HDD (with Windows on it), not detected...?"
date: 2007-01-11
forum: Hardware &amp; Laptops
---

### Post by Good Ol' Ramos on 2007-01-11
Hey there folks!

I installed my second HDD on my system today, and BIOS detects it, but Ubuntu does not. Is there something I need to install? All I can tell you is that it's a 120GB Western Digital HDD that has Windows on it with all the stuff I have yet to transfer over to Ubuntu. I was hoping to set it up for dual-booting, and it will, but until then, I want to be able to access my mp3 files and whatnot and put them on this Ubuntu drive. Any suggestions, fellas and gals?:confused:

---

### Post by ajgreeny on 2007-01-11
Show us the output of sudo fdisk -l, which will show the partition setup and where your new windows is according to ubuntu.  It can then be added into the grub menu to see if it will boot.  I doubt that will be possible, but you should be able to mount it to retrieve your files and copy them to ubuntu.

I've attached a txt file that I made some time ago to remind me of the various mount commands, just in case you're not sure of them.

---

