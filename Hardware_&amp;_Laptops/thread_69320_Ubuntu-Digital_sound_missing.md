---
title: "Ubuntu-Digital sound missing"
date: 2005-09-26
forum: Hardware &amp; Laptops
---

### Post by Giardap on 2005-09-26
Hi,

Just dipped my toes in the Linux waters for the first time with the following...
I have just dual booted a machine with Windows XP Home and Ubuntu 5.04 (Gnome desktop?)on 2 separate disks.
Disk 1 160GB SATA- C,D,E NTFS partitions with WinXP on C; Disk 2 160GB  PATA F,G NTFS partitions and then swap 500MB and Ext3 for/, 9.5GB.
Other info- 2.8E Pentium IV Prescott, I GB dual DDR RAM, on a D865GBF Intel board with SoundMAX Integrated Digital Audio (AC'97 codec I think).
I manually select the operating system from the BIOS on startup due to horrendous problems with MBR's being corrupted and loss of WinXP when I put Ubuntu bootloader at start of C partition (where Windows MBR is I think)etc...but that's a story for another time/question!


However first a Ubuntu sound issue. I have managed to load all updates and other bit's 'n pieces. I have analog sound in my humble bog-standard stereo speakers. But no digital sound. My SPDIF out is a RCA jack ( not TOSLINK) into Creative Cambridge Soundworks THX digital speakers 2.1. These work fine in Windows XP. 
Any suggestions as to how I might get digital sound out please in Ubuntu?

I have Googled/Forumed this and a number of other problems without too much success. 

Thanks

---

### Post by mlomker on 2005-09-26
> Any suggestions as to how I might get digital sound out please in Ubuntu?


If it requires a software driver to work then the motherboard manufacturer would have to provide it.  Have you checked their website?

Generally only the higher-end sound cards have a hardware digital out (the AC3 is encoded using a chip).

---

### Post by Giardap on 2005-09-27
No special drivers or settings needed for XP - the digital speakers were plug n' Unmuted everything in alsamixer to no avail!
Can't see Ubuntu/debian drivers on D865GBF motherboard Intel page.
[http://www.intel.com/design/motherbd/bf/bf_drive.htm](http://www.intel.com/design/motherbd/bf/bf_drive.htm)

Any other ideas welcome!

---

### Post by DancingSun on 2005-09-27
I have a nForce4 Ultra based motherboard, and also integrated AC'97 CODEC sound (Realtek ALC850).  I also have a 3.5mm jack for a coaxial S/PDIF out connection that doubles as line-in (at least according to the manual).

The depressing part, I wasn't able to get the digital out connection to work at all.  Not even in Windows XP using the Realtek drivers.

Currently I'm using a Soundblaster Live! board that I bought from a fellow forumer.  Well, at least it works, and I even have hardware mixing which saves me from so much trouble with software mixing in Linux.

---

