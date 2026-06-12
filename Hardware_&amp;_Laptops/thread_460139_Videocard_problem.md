---
title: "Videocard problem"
date: 2007-05-31
forum: Hardware &amp; Laptops
---

### Post by liberalist on 2007-05-31
1)Version Of Ubuntu 
6.06.1 LTS Dapper Drake 

2)Type Of Hardware
Videocard (probably Nvidia, as [I read in an article about my hardware and potential issues]("http://parrenin.frederic.free.fr/DellLatitudeD800/linux-DellLatitudeD800.html")) 

It does not have all resolutions (now my screen is 1024.784 pixels. 

3)Hardware Maker
Dell

4)Hardware Model
Latitude D800

Question: Which driver do you recommend me to install? And how do I install them (through Synaptic Package Manager)? 
- The open source "nv" driver without 3D hardware acceleration
- Proprietary "nvidia" driver (can only run in highest resolution)
- Proprietary "nvidia" legacy driver (has problems with sleep and hibernate modes, or are these resolved)?

---

### Post by illiadum on 2007-05-31
I've got an nVidia 6600LE and I've used it successfully with Gentoo, Slackware, and Ubuntu.  You will probably need to make sure that the kernel does not include "nv" frambuffer support.  If it is already excluded from the kernel precompiled for Ubuntu (I honestly have no idea), then all you will need to do is install the drivers directly downloaded from nVidia's website.

So, you probably have: Nvidia GeForce FX Go5600
Processor on the D800 is Pentium M, so you don't have EM64T, you'll need 32-bit driver.

1. Download the driver. 
[http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/NVIDIA-Linux-x86-1.0-9755-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/NVIDIA-Linux-x86-1.0-9755-pkg1.run)

2. Reboot into Recovery Mode, so you're X-Server Isn't up.

3. cd to the location you downloaded the driver, and add execute permissions.
cd /somedir/whereits-saved
chmod +x NVIDIA-Linux-x86-1.0-9755-pkg1.run

4. Run the Installer
./NVIDIA-Linux-x86-1.0-9755-pkg1.run

It will ask if you want to reconfig xconf for nVidia, I usually do this the first time I install.  Keep in mind every time you recompile your kernel, you will need to reinstall the driver.  This works for me, hope it works for you too.   ;)

---

### Post by illiadum on 2007-05-31
Update...

I happen to be doing this right now on my girlfriend's machine for her first Linux install (Hurray!) and two things I've also needed to do.

First, the nVidia installer will panic because you're in runlevel 1, this should be fine, just go for it.

Second, it fails if you don't have the libc package installed.  Frankly, I'm surprised this doesn't install by default, but oh well.  To install the package:
apt-get install build-essential

THEN, run the installer.

---

