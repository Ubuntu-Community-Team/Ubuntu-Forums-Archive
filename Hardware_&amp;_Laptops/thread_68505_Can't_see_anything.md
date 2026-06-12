---
title: "Can't see anything"
date: 2005-09-23
forum: Hardware &amp; Laptops
---

### Post by ALumsden on 2005-09-23
I have an Acer Travelmate 8104 - Pentium M 2Ghz, Intel i915PM/GM chipset, 1Gb DDR RAM, 100Gb hard drive, Ati Radeon mobility X700 graphics card. Initially I had 2 partitions, one with windows XP with service pack 2 (25Gb FAT 32) and one partition with my data (68Gb NTFS).

I used the CD (downloaded ISO from website) to load Linux and all seemed to go well.

Now..Grub loader loads and offers me the choice between Linux and Windows.

The Ubuntu splash screen opens and it runs through the loading process. It shows 'failed' for sync clock and for control console font t_kernel font but continues. 

The screen then goes black?

Pressing Ctrl-Alt-F1 opens the terminal screen but after that I have no idea where to look or what to do??

I reinstalled the whole thing again yesterday and exactly the same problem.

What can I do??

Thanks in advance for any help!

---

### Post by mlomker on 2005-09-23
> Pressing Ctrl-Alt-F1 opens the terminal screen but after that I have no idea where to look or what to do??


It misdetected your video card.  At the terminal prompt type **dpkg-reconfigure xserver-xorg**.  The default suggestions should be what it is currently trying to use.  Try the 'ATI' driver or if that is what it is already using then try 'VESA'.

You can work on getting a [faster driver](http://www.ubuntuforums.org/showthread.php?p=348911)  working once you have your desktop back.   :)

---

### Post by ALumsden on 2005-09-23
Well I went in and typed **dpkg-reconfigure xserve-xorg ** and received the following...

Pacakge 'xserve-xorg' is not installed and no info is available
/usr/sbin/dpkg-reconfigurexserve.xorg is not installed

Is this why it is not working?  Why wasn´t it installed?

---

### Post by mlomker on 2005-09-23
> Is this why it is not working?  Why wasn´t it installed?

You mistyped the command.  It's **xserver**.

---

### Post by ALumsden on 2005-09-24
Opps..Well it worked when I typed the command line correctly and I have changed to VESA..everything works now!  Thank you so much!

---

