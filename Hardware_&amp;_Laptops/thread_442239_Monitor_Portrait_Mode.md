---
title: "Monitor Portrait Mode"
date: 2007-05-13
forum: Hardware &amp; Laptops
---

### Post by nsivin on 2007-05-13
I have a workstation (details below) on which I normally use my monitor in portrait mode. I am going to install Ubuntu Edgy 7.04 to dual-boot. Is there a utility available for it (or for Linux generally) that will allow a pivoting monitor to function in portrait mode? 

EndPCNoise Workstation
AMD Athlon dual-core 4200+ 64-bit CPU
Samsung quiet 160GB SATA2 hard drive
ASUS A8V-E SE motherboard with 64-bit support, 3 quiet fans
Samsung SyncMaster 960B Digital/Analog Monitor
2 GB DDR-400 memory
One DVD-RW drive, one CD-RW drive
Windows 2000 SP4, Word

---

### Post by heimo on 2007-05-13
On command line xrandr can be used to rotate display - if your video drivers supports it.

---

### Post by nsivin on 2007-05-17
I would be delighted to try the “xandr” command, but when I issue it Ubuntu replies that there is no such command. A search of the whole disk showed no file named xandr. I also tried searching the software repositories, and even SourceForge, and did not turn it up. Can anyone give me a little more direction?

If this command is built into certain Linux drivers for Samsung monitors, where do I look for them?

Thanks,

NS

---

### Post by heimo on 2007-05-18
> **nsivin said:**
> I would be delighted to try the “xandr” command, but when I issue it Ubuntu replies that there is no such command. 

Command is x**r**andr

---

### Post by DishBreak on 2007-07-03
try typing the following into a terminal

which xrandr

if it's there, you should be able to run it. type

xrandr --help

and you should be able to take it from there.

---

### Post by nsivin on 2007-07-04
I downloaded the driver (which supports portrait mode) and installed it, putting the xrandr command in startup, so now the monitor automatically starts in portrait mode. Many tnanks to everyone.

---

### Post by samarth on 2008-01-22
Hi, Can you tell me exactly how you did this? Thanks.

---

### Post by nsivin on 2008-01-24
Here is how I did it:

Portrait Mode, Configuring NVIDIA Drivers
To get, do 
	sudo apt-get install nividia-glx nvidia-kernel-common
	sudo nvidia-configuration
If that does not work, do 
	Sudo gedit /etc/X11/xorg.conf
And replace “nv” with “nividia”, and add to the same “Device” section
	Option		“RandRRotation” “on” (quotes needed)
To rotate, in System, Preferences, Screen Resolution dialog set Rotation to Left. Alternately, issue command  
xrandr –o left
To return to landscape mode, do 
Xrandr –o normal
Or put the command in startup (see below)
Startup Configuration
To send a command at startup, choose System, Preferences, System. Under Startup Programs, click New, enter command and a title for the action.

---

