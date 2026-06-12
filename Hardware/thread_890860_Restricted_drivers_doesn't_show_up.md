---
title: "Restricted drivers doesn't show up"
date: 2008-08-15
forum: Hardware
---

### Post by sudo_chop on 2008-08-15
I am trying to get Ubuntu running on a new laptop that has a 9600M GS. The restricted drivers that should be there don't show up. Does anyone know what I can do? I am a total noob, if you need more info please ask, I want to fix this ASAP. Thanks

---

### Post by sudo_chop on 2008-08-15
My Atheros Wifi doesnt work either but the restricted drivers package says that both the nvidia drivers and the Atheros drivers are included. Help!

---

### Post by phidia on 2008-08-15
Hi sudo_chop, From what I've seen the 8 & 9 series nvidia cards have problems being recognized in 8.04. Some people use [envy]("http://albertomilone.com/nvidia_scripts1.html"), envyng (which I believe is in the repos) to install the driver and some download the driver direct from the [nvidia site]("http://www.nvidia.com/Download/index.aspx?lang=en-us"). There is more info at both of those links.

Atheros cards work through madwifi or ndiswrapper you may want to start a seperate thread on the wireless card to allow attention for each problem.

---

### Post by sudo_chop on 2008-08-16
Thanks phidia.

I am trying to install the drivers from the Nvidia website now, but the install errors out:

> 
-> No precompiled kernel interface was found to match your kernel; would you like the installer to attempt to download a kernel interface for your kernel from the NVIDIA ftp site ([ftp://download.nvidia.com)?](ftp://download.nvidia.com)?)
-> No precompiled kernel interface was found to match your kernel; this meansthat the installer will need to compile a new kernel interface.
ERROR: You do not appear to have libc header files installed on your system. Please install your distribution's libc development package.
ERROR: Installation has failed.  Please see the file '/var/log/nvidia-installer.log' for details.

I tried installing the package linux-libc-dev but it didnt fix it, thats probably the wrong package, bc im a noob. Anyone know what I need to make this installer work?

---

### Post by Ayuthia on 2008-08-16
> **sudo_chop said:**
> Thanks phidia.

I am trying to install the drivers from the Nvidia website now, but the install errors out:



I tried installing the package linux-libc-dev but it didnt fix it, thats probably the wrong package, bc im a noob. Anyone know what I need to make this installer work?

I think that you just need to have build-essential installed.  I don't recall installing anything else for it.

---

### Post by sudo_chop on 2008-08-16
It needed libc6-dev, the installer worked then. It installed and changed my xorg.conf to use the nvidia driver.

As soon as I started gdm again it said it was going into low graphics mode bc it couldn't detect my video card or my monitor :mad:

 I ran the nvidia-xconfig again and then went back and checked the xorg.conf and everything looked right (like the Nvidia package readme said it was supposed to look, I obviously wouldn't know what I was looking at otherwise). Also there is a "NVIDIA X Server Settings" app in my System Tools menu now, but when I try to run it, it says I am not using the nvidia driver, even though I am??? :mad:

Are there more X Server configurations I need to make or what? Very confused

---

### Post by phidia on 2008-08-16
Sorry you are having these problems obviously setting up the driver isn't suppose to be this difficult but hardy seems to have problems with some hardware configurations.
You could try the solution posted at the end of [this thread]("http://ubuntuforums.org/showthread.php?t=881314"). Let us know how that works or doesn't.

---

