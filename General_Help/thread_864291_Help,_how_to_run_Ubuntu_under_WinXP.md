---
title: "Help, how to run Ubuntu under WinXP?"
date: 2008-07-19
forum: General Help
---

### Post by ProDigit on 2008-07-19
Hi,

I wonder if there's a sollution to running Ubuntu under Windows XP.

It would be wonderfull if I could dualboot my HD to Ubuntu or XP,
but when I'm using Windows, and occasionally need to be in Ubuntu, I would like to run Ubuntu in a window.


The current programs I'm aware of is Virtual Box, and VMWare player.

I've been looking arround, and what I want is the opposite of what I could find on the forum. I read lots about making WinXP work in Ubuntu; but I want Ubuntu in XP;not as the live CD, but as an upgradable configurable installation.


I would also want to ask,if there was a way, to make my HD dual bootable (XP/Ubuntu),and use the Ubuntu boot partition inside a window in WinXP.
That way anytime I update or modify Ubuntu booted from the harddrive, I get the same results in the windowed version of Ubuntu (In WinXP),and visa versa.


Any advice,or installation procedures?

thank you!

---

### Post by mikewhatever on 2008-07-19
Well, there is not much to tell. Simply install vbox or vmware and then Ubuntu. vbox is a little easier to configure in my opinion.
I don't know anything about the other thing.

---

### Post by ProDigit on 2008-07-19
<deleted double post>

---

### Post by ProDigit on 2008-07-19
what worries me is wether or not the installation of Ubuntu under Virtual box will alter my boot sequence.
I hope it'll all stay in the virtual box window,and does nothing to the bootsector on my HD.

For VMWare I probably need to download a VMware image, but I haven't found any on the site.

---

### Post by Lord DarkPat on 2008-07-19
veedee-eyes.com
Wubi is good,  but Virtualbox is fine too, it's a ram hog though

---

### Post by ProDigit on 2008-07-19
It seems that after the installation of VirtualBox, one can set the internal RAM memory and diskspace.
When selecting 'Ubuntu' as operating system, Virtualbox automatically allocates a 8GB file to the OS(configurable, but I left it at 8GB, a large enough diskspace for most basic programs I want to install).

I downloaded the Ubuntu ISO, and mounted it as a virtual CD-rom drive in VirtualBox.
Booted from the CD rom drive, and went straight to the installation.
After the installation is done (virtualBox finds 8,??something something GigaBytes harddrive space, on a something in the likes of 'VBOX' drive, so it was clear to me VirtualBox wasn't going to overwrite the bootsectors of my HD.

So far so good, Ubuntu seemed to have installed smoothly, and run fine windowed.
I've also installed all the remaining updates from the internet

In VBOX, I allready had enabled most settings, and the sliders I set to the middle (1GB RAM, 64Mb Vram).

It was a little figuring out how the sound could be enabled; obviously 'null driver' creates no sound; but the 'soundblaster 16' function didn't seem to work on my pc.

Wifi worked out of the box.

But now I seem to be stuck at 800x600 pix. even at fullscreen.
Adding VRAM (to 128MB) doesn't seem to help.

It maybe a driver issue, allthough I doubt that because when I boot into Ubuntu,I get the full 1280x800 pix of my screen.

I'm running the "Mobile Intel 945GM Chipset Family" video chipset on my laptop. Any ideas? (It maybe a fault in Virtual Box; I'm running Virtual Box 1.6.2).

It's not a major issue, since I generally will need to enter Ubuntu only from time to time from my windows to do some checkups and so..

But still,I rather go fullscreen when needed, if possible!

---

### Post by bodhi.zazen on 2008-07-19
VMWare server is freely available and is also a fine choice.

Virtual machines use virtual videocards, not your host hardware.

To improve the resolution, you need to install the tools. DO NOT INSTALL THESE ON THE HOST

Vbox = guest additions 

[http://ubuntu-tutorials.com/2007/10/13/installing-guest-additions-for-ubuntu-guests-in-virtualbox/](http://ubuntu-tutorials.com/2007/10/13/installing-guest-additions-for-ubuntu-guests-in-virtualbox/)

VMWare = VMWare tools

[http://www.vmware.com/download/server/](http://www.vmware.com/download/server/)

[https://help.ubuntu.com/community/VMware/Tools](https://help.ubuntu.com/community/VMware/Tools)

---

