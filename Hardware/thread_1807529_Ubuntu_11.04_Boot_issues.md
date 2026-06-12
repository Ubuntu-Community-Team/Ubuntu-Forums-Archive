---
title: "Ubuntu 11.04 Boot issues"
date: 2011-07-19
forum: Hardware
---

### Post by Decessus0 on 2011-07-19
I am having quite a number of issues with Ubuntu 11.04 using a Dell Inspiron M5010. The most minor issue is that GRUB will not show boot options unless another medium is present (disc in the optical drive, usb flash drive, etc). Ubuntu unity and ubuntu classic will not boot, all I get is the background image, no panels, no shortkeys and rightclicking does not show a menu. However, when I manually download and install Compiz under Ubuntu Classic (no effects), all animations work smoothly. I have never had these types of issues with ubuntu before, and am heavily disappointed in this release. :(

Is there anything I can do besides revert to 10.04 LTS?

---

### Post by dabl on 2011-07-19
If the USB stick has to be in the computer to boot Grub, then you have apparently installed Grub to the USB stick instead of on your hard drive.

You can install Grub to the hard drive and fix that issue.

---

### Post by Decessus0 on 2011-07-20
Grub is not installed on the usb drive, it doesn't matter what medium you put into the computer, it just *has* to have another medium inserted to show the grub menu..does not matter if it's a usb stick or a cd or otherwise

---

### Post by Bucky Ball on 2011-07-20
Is it set to boot from the hard drive in the BIOS?

---

### Post by Decessus0 on 2011-07-23
Yes, that is what is so odd. Ubuntu 10.04LTS works just fine, but nothing but Ubuntu classic will work when I do in fact insert a random medium to boot grub in 11.04. All I get is the background image, and nothing further if I try anything other than that and Safe Mode

---

### Post by Bucky Ball on 2011-07-23
So you're saying you need a usb stick or a cd in to get a grub? Are you talking about using media that *isn't* Ubuntu install media?

For instance, if you insert an audio cd, does it boot to grub? If you insert a random USB device (dongle, mouse, anything) does it boot to grub?

If not then sounds like you are perhaps getting a grub from the install media. 

You could install and run [BOOT REPAIR]("http://www.webupd8.org/2011/06/boot-repair-fix-ubuntu-boot-issues.html"). When you get to the options choose, 'Install Grub to MBR' and see if that makes any difference.

PS: 10.04 LTS pretty rock solid, current LTS release and longest support (April 2013) so not really a come down unless you're looking to use a specific package in 11.04. You will find that you can try other kernels and manually install newer versions of things if you want them in 10.04. Why not a stable 10.04 and a 'test' partition for tweaking and dabbling with 11.04 (or even 11.10). I currently have 10.04, 10.10, 11.04, Win7 on separate partitions. ;)

---

### Post by Decessus0 on 2011-07-23
Yes, it requires any medium, including install mediums, but excluding things such as human interface devices. I have never seen or heard of anything like this. Ubuntu itself will boot to the default version, but unless I have a storage device of any kind inserted I do not get the option to select another OS/Kernel when I have them installed as a dual boot. The only reason I even want to try 11.04 is due to the fact I have dying to play with unity, but I can not get it to load. I had Win7 and 11.04 installed side-by-side, but I went back to 10.04LTS and have not had any of these mentioned issues.

---

### Post by Bucky Ball on 2011-07-23
Strange indeed. And 10.04 is working no problem? Odd. Sure there's an explanation.

No reason you can't try Unity, though:

[http://www.ubuntugeek.com/how-to-install-unity-in-ubuntu-10-0410-10.html](http://www.ubuntugeek.com/how-to-install-unity-in-ubuntu-10-0410-10.html)

Just open package manager and search/install Unity. ;)

---

### Post by Bucky Ball on 2011-07-23
Just installed it myself in 10.10. Don't know why people hate it so much. Extremely sluggish and jerky on my machine, though. Probably need to tweak it a bit but think I'll be sticking with my trusty xfce for some time to come! ;)

---

