---
title: "External Drives Not Mounting or showing up"
date: 2010-03-31
forum: Hardware
---

### Post by StepBack on 2010-03-31
Karmic 9.10 on a Acer 5920G laptop.

External drives were fine not long ago, but recently they don't show up.

When I plug one in, nothing happens.

"lsusb" output shows that it's plugged in and recognised:
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 002 Device 025: ID 0bc2:3300 Seagate RSS LLC **
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 064e:a101 Suyin Corp. Acer CrystalEye Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Happens with both USB flash drive and my 500GB External HD. Both work fine on other computers and my xbox.

gconf-editor: *apps>Nautilus>preferences> media_automount *and *media_automount_open* are both checked.

I am able to manually mount the device via a lengthy process of using "demsg" output to find the "/dev/sd**" address, and then doing a 
sudo mount -t vfat /dev/sd** /media/WHEREEVER -o uid=1000,gid=100,utf8,dmask=027,fmask=137"

if it's FAT16 or FAT32.

Please someone save me from having to do this...

---

### Post by StepBack on 2010-03-31
I think the behaviour started after some incident with my flash drive. I did something that stopped it from working on my laptop. It may have been something like just removing without safely removing hardware, or something. I'm sorry I can't be more specific, but I don't recall how it happened.

---

### Post by StepBack on 2010-04-05
Bump

---

### Post by zerkig on 2010-04-07
Hi

Not a full answer as I am having a similar problem with my drives no longer auto mounting but to stop you messing around at the command line..

You should have in Karmic 

System -> Administration --> Disk Utility

if not, it is in Synaptic Package manager called gnome-disk-utility

Open this, find your device and click the mount button. It will now be in Nautilus. When finished click unmount.

As I said not a full answer but hope it helps.

---

### Post by StepBack on 2010-04-09
Thank you, very much.
This will make things considerably easier.

All suggestions I'd looked up made reference to "Removable drives and storage" or something in Preferences, but this was removed in Karmic and I couldn't find anything similar, until now. Thanks.

---

### Post by wilee-nilee on 2010-04-09
When the external devices don't show on the desktop have you looked in places-computer to see if they show there?

---

