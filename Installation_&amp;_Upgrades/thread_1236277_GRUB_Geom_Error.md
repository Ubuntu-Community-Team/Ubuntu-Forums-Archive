---
title: "GRUB Geom Error"
date: 2009-08-10
forum: Installation &amp; Upgrades
---

### Post by example6 on 2009-08-10
I currently have Windows Vista installed on two SATA hard drives via the SATA cable and one 250gB hard drive connected to Slave on the Primary IDE cable. The 250-gig hard drive was already formatted with a FAT32 File System, I used the LiveCD Installer's partition program to resize it to 220 gB, and used the remaining 30 gB for the Ubuntu partitions.

The installation completed successfully, but upon restarting my computer I get the Stage1 Error: "GRUB Geom Error"

I googled around for the solution to this problem and only found a few cryptic answers and pointed fingers to documents that don't really help.

All of my drives are recognized by BIOS. I have no idea where to go from here.

---

### Post by gabry79Italy on 2009-08-10
which OS doesn't start ? Windows? Ubuntu? both?

---

### Post by example6 on 2009-08-10
No OS Loads.
It shows "GRUB Geom Error" right after the BIOS prompt.

---

### Post by dandnsmith on 2009-08-10
Referring to [site referring to that error](http://en.opensuse.org/SDB:The_Boot_Process_Hangs_with_the_Message_GRUB_Geom_Error), together with the description of occurrence, I would think cause 4 is the most likely.
You'd have to look at the parameters to decide (use fdisk from a liveCD to give the cylinder numbers of the partitions).
How to avoid it? I'd say you should have shrunk so that the Ubuntu space came first, but that has its own pitfalls.

---

### Post by dfdario on 2009-10-31
I am experiencing the same fault on a fresh installation of UBUNTU Karmic.
Ubuntu 9.04 was previously installend on the same partition ad Grub was booting perfectly.
My configuration is:
OSL2000 boot loader
WinFLP on first primary partition (20GB)
Ubuntu 9.10 on second primary partition (20GB ext4)
Data on third  secondary partition (25GB)
Swap on fourth secondary partition (2GB)

Of course the BIOS is the last available and the disk is recognized by the BIOS (all settings in AUTO)

Almost the same configuration I have on an other laptop PC I use at work and the behaviour is the same.

Suggestions?

---

