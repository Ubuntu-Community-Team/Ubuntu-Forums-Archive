---
title: "nVidia Driver Install and x-org Configuration for Toshiba LCD TV"
date: 2009-06-04
forum: Installation &amp; Upgrades
---

### Post by pdgessler on 2009-06-04
Hi all,

I'm working on setting up my Ubuntu system (Ubuntu 9.04 Desktop) and I'm having major troubles getting the resolution set properly. I'm sure that the monitor isn't reporting the EDID correctly, because I have problems even setting up multiple displays in Window. 

However, I think there may be a driver issue as well, because if I use the default install driver, the LCD will run at 800x600. As soon as I switch out to either of the nVidia drivers recommended by the System> Administration> Hardware Drivers dialog, the OS will only recognize an odd resolution like 480x320, and the nVidia software is locked on to this resolution as well.

Here is the relevant info, if anything else is needed please let me know:

nVidia GeForce FX 5200
lspci: 01:00.0 VGA Compatible Controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)

2.6.28-11-generic kernel, Ubuntu 9.04 Desktop w/ GNOME

Toshiba 19LV505 LCD TV w/ DVD player
--connected to FX 5200 via VGA
--manual says it can do 1360x768 @ 60 Hz in PC mode

for reference:

paul@MEDIA:~$ sudo ddcprobe
vbe: VESA 3.0 detected.
oem: NVIDIA
vendor: NVIDIA Corporation
product: NV34 Board - p162-1nz Chip Rev
memory: 131072kb
mode: 640x400x256
mode: 640x480x256
mode: 800x600x16
mode: 800x600x256
mode: 1024x768x16
mode: 1024x768x256
mode: 1280x1024x16
mode: 1280x1024x256
mode: 80x60 (text)
mode: 132x25 (text)
mode: 132x43 (text)
mode: 132x50 (text)
mode: 132x60 (text)
mode: 320x200x64k
mode: 320x200x16m
mode: 640x480x64k
mode: 640x480x16m
mode: 800x600x64k
mode: 800x600x16m
mode: 1024x768x64k
mode: 1024x768x16m
mode: 1280x1024x64k
mode: 1280x1024x16m
edid: 
edidfail
paul@MEDIA:~$ 

I've tried using both drivers through Synaptic as well as manually installing the driver from nVidia. Both yield the same results.

Any help would be greatly appreciated!!

---

### Post by pdgessler on 2009-06-04
OK . . . quick update, maybe this will help.

I basically wrote my own xorg.conf file from bits and pieces of previous machine's codes and stuff I found on the net.

Now I can get to the login screen at widescreen native resolution, but as soon as I log in, the screen scrambles and goes blank.

Is there any reason why the modeline I created (see below) works for the login manager but not for the session itself?

ModeLine "1360x768" 85.500 1360 1424 1536 1792 768 771 777 795 +Hsync +Vsync

---

