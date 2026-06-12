---
title: "Hardware driver issue with Nvidia card?"
date: 2008-11-03
forum: General Help
---

### Post by evilwombat on 2008-11-03
So I've been dual booting Ubuntu 8.04 and Windows Vista home Premium since Hardy Heron came out. I also hopped on the bleeding edge bandwagon and got Ibex the day it came out. I had minimal problems installing (compared to this) and am now at a point where I am in need of some help.

I have a GeForce 8600 GT 256MB graphics card and it had no problems running with Hardy.
After I got Ibex up and running, I found that I can't enable compiz desktop effects, I can't enable ubuntu desktop effects and most importantly, I can't play World of Warcraft :cry:

I worked on this problem all Sunday afternoon to no avail ](*,). I installed envy, but when I try to use it it asks me for my password and thats the last i see of it. I cannot activate my 173 and 177 drivers from the hardware driver gui. When I try to load Nvidia X server settings it says...
> You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 
Anything anyone can do to get this working, I'm willing to do what it takes.
Layman's terms would be appreciated, I'm still learning.

---

### Post by sharkster2007 on 2008-11-03
My card's an NVIDIA 6600GT but this may help you:

Web source for .deb packages is [http://packages.ubuntu.com/intrepid/...-kernel-source](http://packages.ubuntu.com/intrepid/...-kernel-source)

Quote:
I have installed [COLOR="SeaGreen"]dkms_2.0.20.4-0ubuntu_all.deb[/COLOR] & [COLOR="SeaGreen"]nvidia-173-kernel-source_173.14.12-1-0ubuntu4_i386.deb[/COLOR] & [COLOR="SeaGreen"]nvidia-glx-173_173.14.12-1-0ubuntu4_i386[/COLOR] as these are the only parts required by 8.10 the other dependancies are already installed as standard. (double click the .deb files on desktop to install them)

Then go to:

SYSTEM>ADMINISTRATION>HARDWARE DRIVERS select NVIDIA ACCELERATED GRAPHICS DRIVER (VERSION 173) click enable, an arrow should appear asking you to restart your system

After restarting your system the driver will enable, select your desktop effects from appearances and your done enjoy

PS: I am a brand new user to ubuntu but this worked for me, hope it helps you.

---

### Post by stinger30au on 2008-11-04
nvidia have only got beta drivers out for 8.10 an stable release will be out very soon

---

