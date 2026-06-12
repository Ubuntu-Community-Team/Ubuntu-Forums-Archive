---
title: "ATI Accelerated Graphics Driver causing black screen"
date: 2008-04-26
forum: Hardware
---

### Post by virus92ita on 2008-04-26
I just got Hardy, booted the first time, logged on. It said that some proprietary drivers were needed (ATI Accelerated Graphics Driver). I installed those drivers and a blinking icon told me to reboot my pc. 
Now I can't use ubuntu anymore, I always get a black screen before the log on screen. 

Now I'm on Ubuntu Live CD

Can someone help me, please?

P.S.: I'm a newbe at linux, so be clear and don't take for granted anything, please.

---

### Post by bpl07 on 2008-04-26
Try booting in recovery mode, this reconfigures Xserver and usually works for me.  You might have to enable the ati driver again.

---

### Post by virus92ita on 2008-04-26
I reinstalled ubuntu twice, first time I tried reinstalling video drivers and I got again the black screen, and now I haven't installed video drivers yet.
My video card an ATI Radeon Sapphrie x1550 512MB and I'm googling for drivers.

---

### Post by matisyahu on 2008-04-26
I have x1950pro and I have exactly the same problem... Any ideas how to fix it?

---

### Post by XxX_VLAD_XxX on 2008-11-15
> **virus92ita said:**
> I reinstalled ubuntu twice, first time I tried reinstalling video drivers and I got again the black screen, and now I haven't installed video drivers yet.
My video card an ATI Radeon Sapphrie x1550 512MB and I'm googling for drivers.

I have the exact same Card, with the exact same problem... I have try this page, didn't quite work for me but you should give it a try

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

Now I downloaded the ati proprietary drivers and I'm following these instructions:

Guide to install Ati proprietary drivers

1. Download the drivers from [www.ati.com](www.ati.com)  Should be a file like this ati-driver-installer-8-10-x86.x86_64.run

2. You need to install some programs  to create the packages of this file.

	2.1.  	Open a terminal  write "uname -r"
	2.2.	then write: 	"sudo aptitude update"
				"sudo apt-get install module-assistant build-essential"
				"sudo aptitude install fakeroot dh-make debconf libstdc++5 linux-headers-"uname -r""
				**you must replace "uname -r" with the output from the terminal
3.	Now from your terminal redirect it to the download path and execute these commands

		bash ati-driver-installer-8.35.5-x86.x86_64.run --buildpkg Ubuntu/hardy

	this depends of your file, now you have created the packages and need to installed them

4. Installed this

sudo dpkg -i xorg-driver-fglrx_8.35.5-1_i386.deb

sudo dpkg -i xorg-driver-fglrx-dev_8.35.5-1_i386.deb

sudo dpkg -i fglrx-kernel-source_8.35.5-1_i386.deb

sudo dpkg -i fglrx-amdcccle_8.35.5-1_i386.deb

5. You may need to eliminate old files from   /usr/src/:


sudo rm /usr/src/fglrx-kernel*.deb

6. Now execute these commands to compile the kernel

sudo module-assistant prepare

sudo module-assistant update

sudo module-assistant build fglrx

sudo module-assistant install fglrx

sudo depmod -a

7. Now update the xorg.conf to do that execute

sudo aticonfig --initial

sudo aticonfig --overlay-type=Xv

8. Reboot. And the Ati Catalyst Conctrol Center should appear.

---

