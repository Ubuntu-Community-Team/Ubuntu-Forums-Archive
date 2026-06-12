---
title: "Driver Radeon 6850"
date: 2011-03-22
forum: Hardware
---

### Post by Abdujaparov on 2011-03-22
Hi,
I'm trying to install the driver of my radeon 6850. I downloaded the package from the AMD website and I installed it.
The installation seems terminated correctly I reboot and after that the login screen is with very very little characters and I cennot read anything. I click on ok in the first window and then appear a new window with many option, I leave the first option and click ok again (the name of the option is unreadable). At the end of this I login on ubuntu correctly and I try to open the ATI Catalyst Control Center and I receive an error messages that tell me that the driver is not installed or the driver is not installed correctly.
In the Hardware Driver window (in System->Administration) I read that the driver is installed and is used correctly.
When I launch fglrxinfo command I receive a segmentation fault error.
I launched aticonfig --initial and it's created a new xorg.conf file. I inserted ati as device driver (instead of fglrx) but this act has no effect.
I tried to uninstall the ATI driver using fglrx-uninstall.sh script but I receive this error:

> 
angelo@angelo-desktop:/usr/share/ati$ sudo sh ./fglrx-uninstall.sh

[Warning] Uninstall : inst_path_default or inst_path_override
 does not exist in /etc/ati.  This suggests that the ATI driver
 is not installed, the ATI driver is only partially installed,
 or the current ATI driver installed is an older version than the
 one this script was designed for.  Both files listed above are
 required for determining where installed files are located.
 To force uninstallation of the driver by guessing where the
 uninstallation files are located, set the FORCE_ATI_UNINSTALL
 environment variable and re-run ./fglrx-uninstall.sh (this is not recommended).


So I'm blocked here and I have no idea about how to solve the problem, could someone help me?
Thanks, bye bye.

---

### Post by khelben1979 on 2011-03-22
Are you sure you got the correct driver? You don't mention if you're on a 32bit or 64bit system. Also, are the monitor cable connected by [HDMI]("http://en.wikipedia.org/wiki/HDMI") or how does that look like?

If you go for the latest unstable version of Ubuntu 11.04 "Natty" you can use the RADEON driver which is the open source driver where the Linux kernel supports your graphics card, or you stick with your present version of Ubuntu and keep trying with the non-free driver as you currently do.

---

### Post by Abdujaparov on 2011-03-23
Hi,
I use a 64-bit system and the monitor is connected by HDMI cable. I'd like to use the 10.04 release, I have many applications installed and configured.
How can I uninstalla the driver and re-execute the installation procedure?
Thanks a lot, bye bye.

---

### Post by realzippy on 2011-03-23
read [this]("https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch")...

---

### Post by Abdujaparov on 2011-03-23
I cannot execute this:

sudo /usr/share/ati/fglrx-uninstall.sh

I receive an error and I cannot uninstall the driver. :(

---

### Post by Yellow Pasque on 2011-03-23
> To force uninstallation of the driver by guessing where the
uninstallation files are located, set the FORCE_ATI_UNINSTALL
environment variable and re-run ./fglrx-uninstall.sh 
...
```
export FORCE_ATI_UNINSTALL="yes"
cd /usr/share/ati
sudo ./fglrx-uninstall.sh
```

DO NOT just run the install file. Build packages like this: [http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Installing_the_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Installing_the_drivers_manually)

---

### Post by khelben1979 on 2011-03-23
Have you tried to connect the card by the [DVI]("http://en.wikipedia.org/wiki/Digital_visual_interface") port instead to see if it makes any difference in case the HDMI cable is broken in some way?

Also, what brand are you using? Like Sapphire, ASUS etc etc..

In general it's important to not go through installation procedures in fast pace to get it done, it's better to take your time and always follow all instructions very carefully! Go slow.

---

### Post by Abdujaparov on 2011-03-23
I have only the HDMI cable but it works in another computer with nvidia graphic card.

However the brand is XFX.
Thansk again.
Bye bye.

---

### Post by Abdujaparov on 2011-03-23
Thanks now the driver works!
Thanks a lot!

---

### Post by khelben1979 on 2011-03-23
Would you like to share how you got it working? :)

---

### Post by Abdujaparov on 2011-03-24
Hi did what Temüjin said.
Thanks again, bye bye.

---

