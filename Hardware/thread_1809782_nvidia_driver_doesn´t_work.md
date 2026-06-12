---
title: "nvidia driver doesn´t work"
date: 2011-07-22
forum: Hardware
---

### Post by pain.reign on 2011-07-22
i use ubuntu 11.04
and have asus k53sv laptop with nvidia geforce GT 540M

i do this:

[FONT=courier new]sudo apt-get --purge remove xserver-xorg-video-nouveau [/FONT]
	(from [this ubuntu forum]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia"))  	1) Make sure that the kernel headers for your kernel are installed
	[FONT=courier new]sudo apt-get install linux-headers-$(uname -r)[/FONT]
	2) Install the nvidia driver:
	[FONT=courier new] sudo apt-get install nvidia-current (or nvidia-173 or nvidia-96,[/FONT]
	depending on your card)
	3) Select the driver that you wish to use (you can install all of the
	nvidia drivers but use only at the time):
	[FONT=courier new]sudo update-alternatives --config gl_conf[/FONT]
	[FONT=courier new]sudo ldconfig[/FONT]
	[FONT=courier new]sudo update-initramfs -u[/FONT]
	4) Configure your xorg.conf
	[FONT=courier new]sudo nvidia-xconfig[/FONT]
	5) Restart your computer (restarting only the xserver might not work)


After restarting ubuntu doesn´t start. And i have to start recovery mode with failsafe grafics.


what to do? I am new to ubuntu.

---

### Post by _?_ on 2011-07-22
I've a x53sv, too and I had that problem, too. I resolved loots of problem following this topic:
first I put the kernel 2.6.39-3 following this [http://guiodic.wordpress.com/2011/07/02/cal-for-test-per-chi-ha-una-scheda-intel-o-ati-con-driver-open/](http://guiodic.wordpress.com/2011/07/02/cal-for-test-per-chi-ha-una-scheda-intel-o-ati-con-driver-open/) 
then I put bumblebee and made all this stuff: [http://ubuntuforums.org/showthread.php?t=1791081](http://ubuntuforums.org/showthread.php?t=1791081)
now it works great!

---

