---
title: "GRUB Loading Error 21  with Windows Vista"
date: 2009-03-06
forum: Installation &amp; Upgrades
---

### Post by joebinky on 2009-03-06
I am completely new to Linux. This was my first time at an installation. 

Hello...I installed Ubuntu 8.10 onto an external 60GB WD hard drive, thinking I can take it w/ me to any computer and load Linux on it to learn.

I decided to use my Dell laptop w/ Windows Vista on it to test. I was doing a "manual" partition on the external drive and everything was fine. After unplugging the USB external drive to start Windows Vista normally, I get this message:

GRUB Loading stage1.5.

GRUB loading, please wait...
Error 21

Any help will be greatly appreciated.

---

### Post by lindsay7 on 2009-03-06
look here  [http://www.linuxforums.org/forum/installation/94066-solved-need-fix-mbr.html](http://www.linuxforums.org/forum/installation/94066-solved-need-fix-mbr.html)

---

### Post by lindsay7 on 2009-03-06
The info I gave you should fix your computer so that it will load vista again. It probably will not load Ubuntu after the fix. I think everything would have been fine is your external drive always stayed connected the way you had it set up. I think the problem comes up when you disconnect it and try to boot because the grub loader in ubuntu does not see the ubuntu dirve and system. I think you need to set up the external drive with ubuntu like you would a usb thumb drive. When you do it will not be a dual boot system like you first had configured.  When you set the external drive with Ubuntu like a usb drive it will boot from any computer but that computer needs to have the bios set to boot from the usb port (assuming that is the way you connect the external drive). You will need to research how to do this.  There is good info on this for setting up a thumb drive at Pen Drive Linux.

---

