---
title: "What kind of success are you having with the 9600gt?"
date: 2008-04-25
forum: Hardware
---

### Post by mikezila on 2008-04-25
I've got a 9600gt (made by XFX, if that matters) that I can't seem to get working correctly, and I'd like to see if other people are having similar problems, or if it's just me.  Everything else about my computer is pretty standard.  One video card, Core2Duo, 2GB ram, nothing special.  I'm using the 32-bit version.

I'm using the 8.04 that just came out yesterday, would have been here sooner but it wasn't until this release that it would even work in generic VESA mode.

I can get the driver installed correctly (or at least I assume correctly) using EvnyNG, but when the X server starts, I get an nVidia logo with white dots and lines all over the screen, and a hardlock follows shortly after.  I don't even make it to gdm.

I read somewhere that the 32-bit version of the driver is actually more hit-or-miss than the 64-bit version, but I've yet to try the 64-bit version, so I can't say myself.

I did use Google and the forum search, but all of the posts are for old versions of either Ubuntu, the driver, or both.  Plus they're old, and thread necromancy just confuses everyone.

What kind of success is everyone else having?

---

### Post by Novega on 2008-04-25
I've been struggling with the same problem. The Nvidia driver is the only thing missing for me to be 100% happy with my new Ubuntu setup.

I've searched the forums here and found that some people have had success with the beta driver (ver. 173.08) But I can't figure out how to install it since I'm really new to linux. I know you have to get your system to run level 3, but X server is running at that point...so I'm lost ](*,) 

I also tried the older driver that you describe, I had the exact same results. It showed the Nvidia logo but looked like it snowing, then a lock up.

If you do manage to figure it out, please share...and I'll do the same if I happen to stumble upon a fix :D

---

### Post by mikezila on 2008-04-25
I kind of have it working, I guess.  On a whim, I told EnvyNG to try installing the driver again, and now it works with some problems.

3D accel works, glx, comiz and all

gdm is using the wrong resolution, or something.  The screen zoomed up on the top left corner.

I can't select any widescreen resolutions.  The nvidia X config utility has a panel where it detects my monitor correctly, and lists it's native resolution, and all that jazz, but the panel where you actually change it refuses.  adding it to my xorg.conf manually causes bad things to happen, with half the screen garbage, and the other half split in half and shifted left, if I manage to get that far.

I also can't seem to abort mission and just return to vesa, as now anything but the "nvidia" driver causes safe graphics mode to wrestle control of my display options from me.

I'm about to take drastic messures, and if they don't bear fruit I'm going to reformat and try the 64-bit version.  Thank god for separate /home partitions.

---

### Post by mikezila on 2008-04-25
Fruit was not beared.  I got the nvidia logo again, with snow.  This is frustrating.  I'll try the x64 version, which I should have installed in the first place.

---

### Post by Chefbrenner on 2008-04-25
Hi all,

I've had the same issues with Ubuntu 8.04 (both AMD64 and i386 versions) and a Nvidia 9600 GT. I did not use "envyng" under AMD64, just installed "nvidia-glx-new" by hand. I've you have any success with "envyng" under AMD64 or find a fix for i386, please let me know.

Additionally, the default Ubuntu driver (nv) refuses to boot if I have more than one monitor plugged in. (See [http://ubuntuforums.org/showthread.php?t=766458](http://ubuntuforums.org/showthread.php?t=766458))

This means that I have to stick with 7.10 until a solution is found, because I need both monitors. (9600 GT works fine under Ubuntu 7.10 with 3d-acceleration and dual screen setup using the nvidia driver.)

Best regards,
Chefbrenner

---

### Post by Chefbrenner on 2008-04-25
Got everything working: You need to install the beta drivers from NVIDIA directly:
[LIST]
[*]Install kernel sources: sudo aptitude install linux-source-2.6.24
[*]Download [http://www.nvidia.com/object/linux_display_ia32_173.08.html](http://www.nvidia.com/object/linux_display_ia32_173.08.html) (i386) or [http://www.nvidia.com/object/linux_display_amd64_173.08.html](http://www.nvidia.com/object/linux_display_amd64_173.08.html) (AMD64)
[*]Shut down X-server (I did this very brutally with "kill [PID of gdm]" from another shell, what's the best way to do this?)
[*]Run downloaded NVIDIA installer
[*]Run "./startx"
[*]EDIT: You have to purge "nvidia-kernel-common" or the driver will refuse to work after reboot. This will remove several meta-packages, which is undesirable but I'm not aware of another way. If anyone has a better approach to prevent it from loading the wrong module/driver, please let me know.
[/LIST]

Good luck!

[B]EDIT: I've experienced massive stability issues with this drivers under Ubuntu 8.04 Hardy. I've also tried the previous version (171.06), which worked fine under Ubuntu 7.10 Gutsy, with the same results: freeze when switching virtual desktops, freeze when opening synaptics, freeze, freeze, freeze, ...
Therefore I cannot recommend installing this driver at the moment.[/B]

Best regards
Chefbrenner

---

### Post by Novega on 2008-04-25
Good job Chefbrenner :)

I guess I'll wait until a new driver comes out...soon I hope.

---

### Post by Extraneous on 2008-04-25
Yup, having the same problem. The most recent nvidia driver doesn't claim to support the 9600GT, and support it it does not. Got the same thing reported above, booted to a slightly fuzzy nVidia logo, had to uninstall it.

Shame, I'd like to actually experience the 3D desktop stuff.

---

### Post by Novega on 2008-04-28
So I was wondering, because the people who have nvidia 9600GT cards can't install the nvidia drivers...what kind of limitations does that put on us?

I'm pretty new to this but I'd guess we can't use the 3d desktop effects....what else?  Are the nvidia drivers required to play games? (Pretty sure they are, but just double checking) are there any exceptions?
Basically, I just want to know what I *will not* be able to do until the drivers get updated

Thanks in advance

---

### Post by slick_nick on 2008-04-28
I'm having a low level of success :(.

I just built a new computer today, with a 9600GT.  Whatever driver Hardy installed seems to work fine, not that I've tried any serious graphics/3D on it so far, besides trying to enable extra visual effects in Appearance, which did not work.  Tried installing the latest Nvidia drivers manually; total failure as others have experienced.  I have two monitors plugged in and it boots/runs fine, but the output is cloned...therefore useless.

Eagerly awaiting an updated driver....

---

### Post by Chefbrenner on 2008-04-29
> **slick_nick said:**
>  I have two monitors plugged in and it boots/runs fine, but the output is cloned...therefore useless.

That is very interesting! What driver is used for your card? NV? (Have a look at /var/log/Xorg.0.log if you don't know, or even better: post the file in here, if possible) Can you provide me with more information about your system? (Mainboard, Displays, ...) I'd like to find the reason why booting with two monitors is not working for me with the default driver (NV).

---

### Post by slick_nick on 2008-04-29
Mainboard is a Gigabyte GA-MA770-DS3, with an Athlon X2 4600+.  The video card itself is an Asus EN9600GT.
Primary display is a 19" Samsung Syncmaster 930B LCD, and the secondary is an ancient brand X (Gem?) 19" CRT.

---

### Post by Chefbrenner on 2008-04-29
Thank you!
It seems to depend on the way the 2nd monitor is connected: If I connect both via DVI, the system will hang during X startup. If I connect one via VGA, the gnome desktop appears but output can only be cloned. I'll file this as a bug.

---

### Post by isecore on 2008-04-29
Works fine for me. I had to download the beta-driver from Nvidia, but it works fine. Mostly fine. For some minor reason it gets wonky when using Twinview, but other than that it's great. I don't really use Twinview so whatever.

I experienced stability issues with the 173-version (tearing of graphics, random X lockups) but 171 works good for me.

---

### Post by ztarget on 2008-05-03
1. [http://us.download.nvidia.com/XFree86/Linux-x86/171.06/NVIDIA-Linux-x86-171.06-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/171.06/NVIDIA-Linux-x86-171.06-pkg1.run)
2. download find and give permissions
3. in console (terminal) : sudo apt-get install mc
4. alt+ctrl+F1
5. sudo /etc/init.d/gdm stop
6. sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev    press: y if done
7. sudo mc
8. find and run the nvidia driver
9. answer NO for the first question
10. Press ok to build headers
11. after nvidia driwer installation done, answer YES, to autoconfigure xconfig


Tested it on Ubuntu 8.04 with  Geforce9600GT 
Tested it on Kubuntu 8.04 with Geforce9600GT but the 173.08 driver, working but bugged, DONT RECOMMEND to install it.

---

