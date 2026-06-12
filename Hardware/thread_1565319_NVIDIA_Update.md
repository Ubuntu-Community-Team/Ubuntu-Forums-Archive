---
title: "NVIDIA Update??"
date: 2010-08-31
forum: Hardware
---

### Post by Thomas_Bates on 2010-08-31
Alright, I'm trying to update NVIDIA, I've got a GeForce card (7100). I downloaded the driver (.run) from here:

[http://www.nvidia.co.uk/object/linux-display-ia32-256.53-driver-uk.html](http://www.nvidia.co.uk/object/linux-display-ia32-256.53-driver-uk.html)

It downloaded a .run file, after stopping xserver and running the file, which went smoothly, and then restarting xserver (actually I start/stopped gdm), it re-logged me in and I noticed there was no change to my screen resolution. I went into NVIDIA and noticed I was still stuck with the same resolution. Help with drivers?

---

### Post by Thomas_Bates on 2010-08-31
So I restarted the computer, and now it is a disaster. I noticed that the installation informed me that there was no configuration file or something, but I ignored it. Well, on restart I'm presented with this:


Ubuntu is running in low-graphics mode

The following error was encountered. You may need to update your configuration file to solve this.

(EE) Aug 31 18:29:49 NVIDIA(0): Failed to initialize the NVIDIA kernel module. Please see the systen's kernel log for additional error messages and consult the NVIDIA README for details.
***Aborting***

Screen(s) found, but none have a usable configuration.

This is an extremely common issue for me, and I have a file just for it. But after using the fix, it is still giving me the same error. So I used NVIDIA's own backups, also to no avail.

Below is the xorg.conf:



Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Maxdata"
	Modelname	"1905 S1"
	HorizSync       31.0 - 83.0
	VertRefresh     56.0 - 75.0
	Option         "DPMS"
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
	SubSection "Display"
		Depth	24
		Virtual	1024	768
		Modes	"1024x768"	"800x600"
	EndSubSection
EndSection

Section "Module"
	Load           "glx"
	#    Load           "dbe"
	#    Load           "extmod"
	#    Load           "type1"
	#    Load           "freetype"
EndSection

Section "InputDevice"
	Identifier     "Configured Keyboard"
	Driver         "kbd"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"GeForce 7100"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
	#	Busid		"PCI:0:1:0"
EndSection


I ran this file and xorg.conf.bak (which is the backup file I use), through Kompare, they're identical.  Any help with this is GREATLY appreciated.

---

### Post by Thomas_Bates on 2010-09-01
Bump, I really need help with this.

---

### Post by zecapistolas on 2010-09-01
Try [this]("http://www.nvnews.net/vbulletin/showpost.php?p=2118873&postcount=22")....

---

### Post by ellgor on 2010-09-01
Hi,

Found this guide which really works:


1) Download Newest Nvidia drivers from their website
2) Open module blacklist as admin:

sudo gedit /etc/modprobe.d/blacklist.conf
3) Add these lines and save: 

blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv
4) Uninstall any previously installed Nvidia drivers: 

sudo apt-get --purge remove nvidia-*
5) Reboot your computer
6) When an error message pops up saying that Ubuntu cannot load Nvidia drivers, choose Exit to terminal (Exit to console)
7) Login and cd to the directory where you saved your file
 Install drivers

sudo sh NVIDIA-Linux-x86_64-195.36.24-pkg2.run (or whichever package you have, be precise as errors will result in "no such file"
8) Follow the onscreen guide from Nvidia and when done
9) Start GDM

sudo service gdm start

Regards, Ellgor.

---

### Post by Thomas_Bates on 2010-09-01
Sir, you get 3 servings of EPIC WIN.

Thanks a lot, guide worked perfectly, there were a bunch of file creation errors, but it didn't actually effect anything.

---

