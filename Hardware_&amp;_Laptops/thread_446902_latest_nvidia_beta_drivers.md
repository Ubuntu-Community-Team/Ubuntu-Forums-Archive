---
title: "latest nvidia beta drivers"
date: 2007-05-17
forum: Hardware &amp; Laptops
---

### Post by Jiroo on 2007-05-17
Hi,

I'm trying to install the latest nvidia beta drivers (100.14.03) and I can't make them work. I tried three things:

**[COLOR="DarkRed"]First:[/COLOR]**
I downloaded the file NVIDIA-Linux-x86-100.14.03-pkg1.run, that could be found [here]("http://www.nzone.com/object/nzone_downloads_rel70betadriver.html") and followed the howto for [Nvidia 9742 beta drivers in Edgy/Feisty]("http://ubuntuforums.org/showthread.php?t=296933").

Everything is ok until I reach this point:
```
sudo ./nvidia-installer -n -s --x-prefix=/usr/lib/xorg/ --kernel-source-path=/usr/src/linux-headers-`uname -r`
```

It simply does nothing. So, removing the -s tag, I remove the silent mode and the installation begins, but it complains about the gcc (I can't reproduce the message because I can't copy it without starting x). Removing the -n tag (no precompiled kernel) doesn't work either.

**[COLOR="DarkRed"]Second:[/COLOR]**
I run the install program as appears on nvidia's webpage:
```
sudo sh ./NVIDIA-Linux-x86-100.14.03-pkg1.run
```
The programs needs to build the kernel because it couldn't find a precompiled one nor the linux headers.
If finishes, I modify xorg.conf (I add Load "dri" and change in device "nvidia" for "nv").
Here X starts but with no acceleration enabled. When I check the drivers version I get this:
```
$ sudo nvidia-installer -i

Welcome to the NVIDIA Software Installer for Unix/Linux

The currently installed driver is: 'NVIDIA Accelerated Graphics Driver for
Linux-x86' (version: 100.14.03).
```
So it is installed... but not configured?

**[COLOR="DarkRed"]Third:[/COLOR]**
Start again. remove all nvidia packages and follow the [wiki guide]("https://help.ubuntu.com/community/NvidiaManual") to install nvidia drivers manually, which is basically the same as the first thing I tried. That article points out an alternative by linking the linux source kernel, but, I can't  find nothing similar on the repos, so I can't solve it that way. The command is:
```
sudo apt-get install linux-source-`uname -r`
``` So maybe this guide is not for Feisty

Now I'm working with the second proceeding, but with no acceleration.

I obviously don't know much about building kernels or anything that goes much further than a howto.
Any clue? Something, whatever. #-o

I really appreciate any help.

---

### Post by kc8hr on 2007-05-18
Hi Jiroo,

> **Jiroo said:**
> Hi,

Welcome to the NVIDIA Software Installer for Unix/Linux

The currently installed driver is: 'NVIDIA Accelerated Graphics Driver for
Linux-x86' (version: 100.14.03).[/CODE]
So it is installed... but not configured?
.

I have had similar problems. If the installer says it is there, then  it is there. Make sure you modify your /etc/xorg.conf and make sure it says:

Section "Device"
    Identifier     "nVidia Corporation NV6 [Vanta/Vanta LT]"
    Driver         "nvidia"
EndSection

and not

    Driver     "nv"

Good Luck!
Tim

---

### Post by psyke83 on 2007-05-18
You're much better off trying Alberto Milone's Envy script. See post #9 of this thread: [http://ubuntuforums.org/showthread.php?t=441630](http://ubuntuforums.org/showthread.php?t=441630)

---

### Post by IntuitiveNipple on 2007-05-18
I installed the 64-bit version of these drivers and it was quick and simple.

```
$ sudo /etc/init.d/gdm stop
$ sudo apt-get install build-essential
$ sudo sh ./NVIDIA-Linux-x86_64-100.14.03-pkg2.run
$ sudo /etc/init.d/gdm start

```
When prompted, I allowed the installer to search for existing modules to replace, and let it modify xorg.conf. It restarted immediately with acceleration and the Nvidia X Server Settings application was in the Applications > System Tools menu.

---

### Post by Jiroo on 2007-05-19
Maybe the problem is that my xorg.conf is modified, and that modification is somehow is incompatible with the drivers.

I run ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` to reset the xorg.conf... but it didn't work, and now my keyboard is set as US. 

Tim, when I use "nvidia", I can't start X, so I'm using at the moment "nv".

> **psyke83 said:**
> You're much better off trying Alberto Milone's Envy script. See post #9 of this thread: [http://ubuntuforums.org/showthread.php?t=441630](http://ubuntuforums.org/showthread.php?t=441630)

I've been looking all the threads about nvida and envy and such... but obviously, I didn't see that one... I'm going to try it and I'll tell you.

Thank you all your your help

---

### Post by Jiroo on 2007-05-19
This Alberto Milone's script is great! It fixed everything and now I'm running the beta drivers. I though I needed to mess around to install the beta drivers with envy, but I just needed three clicks. :guitar:

Thank you for the help.

---

### Post by _simon_ on 2007-05-19
Easiest way I have found to install Nvidia drivers is:

1)First make sure libc-dev is installed.
2)Reboot machine.
3)Hit ESC to display GRUB Menu
4)Choose the "Recovery Mode" option.
5) type "login" and login
6) type sudo sh /path/to/installer/NVIDIA-Linux-x86-100.14.03-pkg1.run
7) Follow on screen instructions, don't try and download anything from NVIDIA.
8) Reboot - all done.

I've been using this method for a very long time and it always works.

---

