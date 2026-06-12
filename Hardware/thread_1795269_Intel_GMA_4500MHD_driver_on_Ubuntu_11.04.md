---
title: "Intel GMA 4500MHD driver on Ubuntu 11.04"
date: 2011-07-02
forum: Hardware
---

### Post by yoavbo on 2011-07-02
Hello,

I've got Acer Aspire 1410 and Ubuntu 11.04 The graphics adaptor is Intel GMA 4500MHD and the graphics seem to be running smoother on Windows. Where can I find a new updated driver that would fix this?

Thanks in advance,
Yoav

---

### Post by Evernoob7 on 2011-09-25
Anybody have an answer for this guy? I'm trying to squeeze some performance out of this GMA 4500MHD with a Pentium Core 2 Solo 1.4Ghz. I can get Nexuiz to the lowest possible settings to be barely playable at 25-30fps. Was hoping I might be able to get into the 40'-50's. Possible?

BTW - I have an Aspire 1410 as well, with the 32-bit Natty.

---

### Post by foresthill on 2011-09-26
The bleeding edge drivers are generally buggy, and with little or no performance increase. If you're running games and want the same framerates you're getting in Windows, just turn off all of the desktop effects and you should see that happen.

FWIW, I'm running an Intel 4500 MHD on my laptop.

---

### Post by littlebigman on 2011-11-29
I have a laptop that uses the GMA 4500MHD, and I can't even get Ubuntu 11.04 to display any video in text mode. I can work with it through SSH, but I'd like to be able to log on locally.

Is there an easy way to add basic video? I don't need X, or only in basic mode (1024x768).

Thank you.

---

### Post by foresthill on 2011-11-29
There are some fixes in this thread:

[http://ubuntuforums.org/showthread.php?t=1741556&page=4](http://ubuntuforums.org/showthread.php?t=1741556&page=4)

Also, you can use an external monitor.

Or you can log into failsafe mode and choose "basic graphics" (this will give you basic blurry, stretched 1024 x 768 resolution) though I'm not positive you can do this in 11.04, but I know you can do it in 11.10.

HTH.

---

### Post by littlebigman on 2011-12-01
Thanks for the tip. I'm not sure I have a "backlight problem", since my screen is just totally dark with just the cursor blinking at 0,0.

Running "apt-get update; apt-get upgrade" and rebooting didn't help.

I'll just stick to Ubuntu 10.x and see if they solve this in a later release.

Thank you.

---

### Post by mastablasta on 2011-12-01
> **littlebigman said:**
>  
I'll just stick to Ubuntu 10.x and see if they solve this in a later release.
 

 
that doesn't make sense. Since newer opensource drivers and resolved bugs will be found in 11.10 (as part of new kernel used in that edition) and Intel uses opensoruce drivers.
 
additionally the very new and even experimental drivers can be installed via PPA if necessary. make sure you read their release notes though.
 
additonally you could try a different desktop environment (XFCE, LXDE?!) with less 3D acceleration.

---

### Post by foresthill on 2011-12-01
The only way I can see this making sense is if he has a failed installation. Does the live CD work for you?

Have you tried reinstalling using some of the boot parameters such as "ACPI=off"?

---

### Post by SIOUX410 on 2012-02-17
Anyone  can help on installing drivers?? 

I mean directions for very very beginners. 

There is a bunch of different packages and files at intel webpage but is very messy and impossible to know what to install and how... 

thanks

---

### Post by CivilizationII on 2012-02-17
The latest driver is here:

[http://downloadcenter.intel.com/SearchResult.aspx?lang=eng&keyword=%22GMA+4500%22](http://downloadcenter.intel.com/SearchResult.aspx?lang=eng&keyword=%22GMA+4500%22)

(select Linux system)

But the drawback is you have to compile it yourself

---

### Post by Danielt876 on 2012-03-27
I have been using Linux for several years but only as a Live CD to do some basic hard drive work, etc. I just installed Ubuntu 12.04 on my laptop (Compaq Presario CQ60-417DX [Intel GMA 4500M]) and have already downloaded the drivers from Intel but have no idea how to compile them. I am a complete n00b when it comes to compiling anything in Linux. I would consider myself very advanced when it comes to my knowledge with Windows but Ubuntu is a whole new world. Any chance someone could write a basic guide for compiling the drivers for Ubuntu? Ubuntu installed with no issues and my laptop booted up in native resolution (1366 x 768) and everything works fine until I get to YouTube. Videos play fine in 360p and 480p but it won't even come close to playing HD smoothly. I know all I need is to install the drivers (will play Ultra HD [4320p on external 32"] in Windows 7) but I have no idea how to. Any help would be greatly appreciated.

---

### Post by Yellow Pasque on 2012-03-27
The drivers are already installed. The problem is Flash video using the Flash plugin is an unaccelerated mess on Linux. Try the Firefox Flashvideoreplacer plugin to view Flash content in a real video player.

---

### Post by Danielt876 on 2012-03-28
You were right, although Ubuntu has no idea what brand the graphics chipset even is it plays videos in full HD without a problem as long as its not through the Flash player. Thanks for the quick response and perfect answer.

---

