---
title: "NVIDIA Driver Problem"
date: 2006-04-13
forum: Hardware &amp; Laptops
---

### Post by SteveF on 2006-04-13
Hi,

I'm running kubuntu - Breezy.  I have the following card:
GeForce2 MX/MX 400

I followed the how-to for nvidia drivers (where I was a little confused over whether I needed the legacy drivers - I tried without) and did the following:

sudo apt-get install nvidia-glx nvidia-settings linux-restricted-modules-$(uname -r)
sudo nvidia-glx-config enable

modify /etc/X11/xorg.conf after backing up
	check the Section "Module"
	comment out:
		Load "dri" 
		Load "GLcore"
	verify/add:
		Load "glx"

	check Section "Device"
		make sure Driver is "nvidia"

then modify /usr/share/applications/NVIDIA-Settings.desktop
add:
	[Desktop Entry]
	Name=NVIDIA Settings
	Comment=NVIDIA Settings
	Exec=nvidia-settings
	Icon=
	Terminal=false
	Type=Application
	Categories=Application;System;

do CTRL-ALT-F1 to get to terminal
logged in and restart X with sudo /etc/init.d/kdm restart

Everything seemed to be fine.  I saw the nvidia logo and got the login screen.  I logged in and tested using glxgears and got a much faster frame rate than when I log in using Ubuntu (which does not have the drivers).

Today, I started my computer.  When Kubuntu started, everything looked correct, but at the point where the nvidia logo should have come up, I get a screen that is half black and white (looks like logo started to get loaded).  I can't do anything at this point other than reboot (CTRL-ALT_F1 does nothing).

I rebooted into recovery mode.  I copied my old xorg.conf over the new one and am able to log into my machine now.  But without use of the nvidia drivers.  I tried downloading the legacy drivers to see if that might help, but they do not seem to do anything either.

Any ideas?

Thanks, 
Steve

---

### Post by atomicbaum on 2006-04-13
I have had problems with my geforce 2 also. I had to get the  legacy drivers , and get a kernel update and then sudo nvidia-glx-config enable. What I would do is boot into safe mode, and comment out Load "glx" with a #. Then switch "nvidia" to "nv" (just for now) so you can boot into KDE. After that, start up synaptic and remove the normal drivers, get the legacy drivers, then enable them. I have had so many problems getting X to accept my nvidia card, If this does not work, post again and I will post my X.conf file (Im not at home right now).

I hope this helps.

---

### Post by SteveF on 2006-04-13
[QUOTE=atomicbaum]I have had problems with my geforce 2 also. I had to get the  legacy drivers , and get a kernel update and then sudo nvidia-glx-config enable. What I would do is boot into safe mode, and comment out Load "glx" with a #. Then switch "nvidia" to "nv" (just for now) so you can boot into KDE. After that, start up synaptic and remove the normal drivers, get the legacy drivers, then enable them. I have had so many problems getting X to accept my nvidia card, If this does not work, post again and I will post my X.conf file (Im not at home right now).

I hope this helps.[/QUOTE]


I unistalled the regular restricted files and installed the legacy and it seems to work.  Hopefully it will last more than one reboot this time.

Thanks for the help,

Steve

---

### Post by zubrug on 2006-04-13
Yup, that card is only supported with the legacy driver, sorry

---

