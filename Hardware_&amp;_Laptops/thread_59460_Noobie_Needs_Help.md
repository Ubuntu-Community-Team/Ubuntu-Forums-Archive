---
title: "Noobie Needs Help"
date: 2005-08-24
forum: Hardware &amp; Laptops
---

### Post by LostinTime on 2005-08-24
I am completely new to linux.  I have tried approx 20 times to install this on my system but failed.  I have version 5.04 ubuntu.

I am having 3 problems-----

Part of the problem is no internet via a network type connection.  I have two different pci modems and tried both. (not at same time)  Both are full blown modems NOT winmodems!  Both have shown up in device manager.  I have installed 3 coms linux file to run set serial ....no sucess

Secondly,  I have ati all in wonder 9600 video card installed and can not get it to change resolutions.  it is stuck on 640x480 and that is only choice in menu.
Tried ati file and get broken pipe error on install.  (By the way ...this is a dual head card but currently only using one monitor.) 

Thirdly no matter what i try cannot get 686-smp kernel to install and i have downloaded the image.  Irq balance loads fine. Important because I have a dual xeon with HT cpus.

If I can get these things installed I will be happy with linux.  I have read and tried things found in forums....so please give me step by step instructions for a linux newbie.

Thanks for any help in advance.

---

### Post by strips on 2005-08-24
[QUOTE=LostinTime]Secondly,  I have ati all in wonder 9600 video card installed and can not get it to change resolutions.  it is stuck on 640x480 and that is only choice in menu.
Tried ati file and get broken pipe error on install.  (By the way ...this is a dual head card but currently only using one monitor.) 

Thirdly no matter what i try cannot get 686-smp kernel to install and i have downloaded the image.  Irq balance loads fine. Important because I have a dual xeon with HT cpus.
[/QUOTE]

To get better resolution to begin with you could try to use plain VESA to start with. Run **$ sudo dpkg-reconfigure xserver-xorg**. You need the vertical and horizontal refresh rate for your monitor. Else search this forum for xorg.conf files and ATI cards.

Have you tried both these kernel images?
linux-image-2.6.11-1-686-smp
linux-image-2.6.10-5-686-smp

I have no knowlage about HT CPUs in perticular. But does the kernel entry in */boot/grub/menu.lst* point to the right partition? Check differences with the working kernel and non working one.

Can't help with modem trouble since I never tried that.

________________________
Regards
Stian H. Larssen

---

### Post by ubuntme on 2005-08-24
If I understand you corrently you have a dial up internet connection from a PCI modem??  I havn't done that for years, but would any of these  help?

[http://ubuntuguide.org/#gnome-ppp](http://ubuntuguide.org/#gnome-ppp) 
[http://ubuntuguide.org/#identifymodemchipset](http://ubuntuguide.org/#identifymodemchipset)
[http://ubuntuguide.org/#configuredialupconnections](http://ubuntuguide.org/#configuredialupconnections)  

As for the vid card, have you installed the ATI drivers?  I have never done this as I would never buy a ATI card (poor linux support!).  Here is the howto:

[http://www.ubuntuforums.org/showthread.php?t=24557](http://www.ubuntuforums.org/showthread.php?t=24557) 

Hope that is some help 

Out of curiousity, can you post you xorg.conf?
cat /etc/X11/xorg.conf

good luck

---

