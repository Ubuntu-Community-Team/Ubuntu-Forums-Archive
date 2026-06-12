---
title: "Cant install Ubuntu 8.04"
date: 2008-07-30
forum: General Help
---

### Post by InQ_LV on 2008-07-30
Hello,
Last week I decided to change my OS to Linux. Problems starts when I push "Install Ubuntu". When Loading is complete there are plenty of things what happens. Sometimes it shows SQUASHFS errors, sometime black screens with cursor e.t.c. It happens when I choose "Try Ubuntu..." too.
My PC: 
32 AMD Sempron 3000+ 1.8GHz
Giga-Byte GA-K8NE
DDR 256MBx2
HDD: 1)80GB SATA Samsung HD080HJ 8MB 7200rmp
     2)400GB Sata 2 Western Digital 4000AAKS 16mb 7200rmp
GF-6600 256mb 

As I established that my Video card is guilty. I Find out that I need this [http://www.nvidia.com/object/linux_display_ia32_173.14.09.html](http://www.nvidia.com/object/linux_display_ia32_173.14.09.html)
driver to be installed, I just don't get it how I can install it . I am absolute newbie in Linux...

P.S Sorry for my bad English.

---

### Post by lisati on 2008-07-30
Something might have gone wrong with your disk - you might want to run the "Check disk for errors" option that comes up before the LiveCD starts.

---

### Post by InQ_LV on 2008-07-30
I have try it with couple of CD, I Also tried to install Ubuntu 7.04, Kubuntu and OpenSuse 11.0, but they just don't wont to be installed xD

---

### Post by danwood76 on 2008-07-30
Try the alternative isntall CD, it doesnt use a full GUI so you should be able to install from that.

Also check the MD5 of your downloads to verify theyre not corrupt, and also use the media check on the live CD boot menu to verify they burned correctly.

---

### Post by InQ_LV on 2008-07-30
When I tried to install Ubuntu  7.04 with alternate CD, all installation process was without errors but when I start to log in, there was some errors on desktop, where was told something about Nautilus(dont know what it is), anyway that wasn't all, I couldn't open any folder and couldn't start Mozilla. I tried to get in with recovery mode - all worked perfect. But when I restart PC I
couldn't get in recovery mode anymore.

---

### Post by Kevbert on 2008-07-30
Please run memtest from the CD menu.

---

### Post by kunixos on 2008-07-30
If you've been able to load up once, you should be able to update from the command line and things should go smoothly. I realize you'll need the nvidia drivers, so read on here and the wiki about how to install them via Command Line Interface (CLI).

As for updating, when grub kicks in, hit "Esc" and then edit the "kernel" line with a ```
single
```at the end. This allows you to log in to the CLI and then just ```
sudo apt-get update
sudo apt-get upgrade
```and you're on your way.

Hope this helps!

---

### Post by InQ_LV on 2008-07-31
I finished install ubuntu 7.04 from advanced CD. When I am finished install upgrades in recovery mode, "normal" mode now works just fine, but when I want to upgrade distribution, setup works until starts "installing upgrades". When installation is about over half, my screen turns pink with some blue and green stripes and I cant do nothing except push restart button. 
And could somebody tell me how to install  this file - NVIDIA-Linux-x86-173.14.12.pkg1.run

---

### Post by nbayiha on 2008-07-31
Follow this link to install nvidia graphic driver.
I worked without problem for me in 8.04 and i dont know if it will be the case in the 7.10 but give it a try .

[http://ubuntuforums.org/showthread.php?p=5495064#post5495064](http://ubuntuforums.org/showthread.php?p=5495064#post5495064)

---

