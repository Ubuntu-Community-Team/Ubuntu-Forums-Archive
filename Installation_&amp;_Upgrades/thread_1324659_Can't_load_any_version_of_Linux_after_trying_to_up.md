---
title: "Can't load any version of Linux after trying to update to Ubuntu 9.10"
date: 2009-11-12
forum: Installation &amp; Upgrades
---

### Post by mugwump40 on 2009-11-12
I need help!  I had a dual boot Windows XP and Ubuntu 9.04 working on my desktop.  I tried to do a clean install of 9.10.  It froze after I made my install options and gives a message: "Input Signal Out of Range.  Change settings to 1280 X 1024 - 60Hz"  My graphics card IS set at 1280 X 1024 - 60 Hz.  Operating system is HP Slimline s3521p, AMD Athlon X2 5200 proc., 4096 memory, 500 Gb HD, NVIDIA GeForce 6150SE Graphics card.  I have updated every driver I can find.  Meantime, NOTHING.....UBUNTU 9.04, 9.10, UBUNTU Studio, DEBIAN, FEDORA 11, etc. will load.  They all give the same message.  I also get a message during install boot up: "ACPI: Expecting a [Reference] Package Element, Found 0"  Other than these two messages, there is no indication of what is going on.  I'm at the point of thinking the new GRUB did something that I haven't been able to undo.  I have run "fixmbr", "Fdisk" and other methods of trying to re-write the MBR.  I have even used Killdisk.exe to write all 0's and 1's on the HD and re-loaded Windows XP.  The logon screen STILL comes up as though GRUB is controlling it, but the only choice is Windows XP.  It does not give me a "clean" Windows XP boot as I would expect.  So something must be staying on the HD in either the MBR or Journal that I can't get rid of.  Any suggestions??

---

