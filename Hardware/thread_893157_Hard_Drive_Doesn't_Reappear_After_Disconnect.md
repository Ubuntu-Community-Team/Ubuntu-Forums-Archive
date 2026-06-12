---
title: "Hard Drive Doesn't Reappear After Disconnect"
date: 2008-08-18
forum: Hardware
---

### Post by Armando Penblade on 2008-08-18
The wiring in my house is somewhat spotty, so sometimes, when turning off a box fan plugged into the outlet above my hard drive'ss wall outlet, the HD pops off for a split second--just long enough for an OS to lose track of it.

Windows is able to rediscover the hard drive immediately, and rescans it, returning functionality within seconds.  I say this only to show that we aren't looking at a hardware problem (Bad drive, USB controller, or cable).

Howerver, Ubuntu loses track of the drive until I do a hard reboot--even logging out and back in isn't enough to recapture it.  It shows up when I do the fdisk command I read about in another thread, in the spot "dev/sdb," however, when cruising through the various dev/drive folders, I am unable to load this drive (Which is even listed perfectly in the "by label" folder as its name).  It appears that on some deep level, the kernel IS detecting the drive, but Nautilus/the GUI don't see it or let me access it...and more importantly, Rhythmbox isn't able to read the music off of it.

Any (very explicit, newbie-centric) advice?

---

### Post by spacedoggy on 2008-08-18
usb drives employ write caching and do not generally like power interruptions on any operating system, if this happens when you are writing important data to it you are in danger of corrupting all the data on it.

I'm sure you could remount the drive without restarting linux by removing the USB for longer than a split second and reinserting it then mounting manually using the sudo mount command (man mount)

but the fact remains you really want to hate your data to have a CPU or hard drive running on such reliable power, you could invest in a cheap surge protector or if you if some power points are more reliable than others give less reliable ones to monitors, printers and devices that have a little more fault tolerance.

---

