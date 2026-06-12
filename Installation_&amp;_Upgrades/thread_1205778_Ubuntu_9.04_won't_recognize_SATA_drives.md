---
title: "Ubuntu 9.04 won't recognize SATA drives"
date: 2009-07-06
forum: Installation &amp; Upgrades
---

### Post by monogoat on 2009-07-06
Ok, I am trying to migrate my desktop to linux, but it is giving me a lot of grief. This is my first experience with Ubuntu (or any debian based distro), I run Mandriva on my laptop (and previously Fedora).

My hardware configuration:
Intel E8500
Evga 780i SLI Board
8GB RAM
OCZ Vertex 30gb SSD (for /)
Western Digital 640gb Black (for /home)
BFG 260 GTX GPU


My goal is to have linux run on my desktop and be able to play my games as it appears enough of them are working with wine that it is finally feasible for me. My friend urged me to try Ubuntu, and given the popularity I figured it would be easier to get my games working (more guides specifically for Ubuntu).

I first found out that Ubuntu would not start at all with my DVD rom connected to SATA, no problem with IDE. Then it was immediately apparant that it does not recognize anything that is connected to SATA.

lspci
```
00:00.0 Host bridge: nVidia Corporation C55 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a2)
00:00.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.7 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:03.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP55 SMBus (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1)
00:0b.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2)
00:0d.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a3)
00:0e.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a3)
00:0e.2 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a3)
00:0f.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2)
00:0f.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
00:11.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a3)
00:12.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a3)
00:13.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a3)
01:00.0 PCI bridge: nVidia Corporation Device 05b1 (rev a2)
02:00.0 PCI bridge: nVidia Corporation Device 05b1 (rev a2)
02:02.0 PCI bridge: nVidia Corporation Device 05b1 (rev a2)
03:00.0 VGA compatible controller: nVidia Corporation GT200 [GTX260-216] (rev a1)
05:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
```

fdisk -l gives me nothing, there are no sd* or hd* devices at all in /dev. The drives may as well be unplugged. I've been googling and this problem does not seem isolated to me, and appears that enabling ahci in the bios is a cure. My bios does not have this option. I've also tried the suggested acpi boot strings and pci=nomsi to no avail.


Interestingly, if I boot from my Mandriva 2008.1 disc in text mode (GUI freezes for some reason), I can see both the drives fine and even formatted them this way to see if it would help. 

Honestly, if I could get a 64bit Mandriva One disc I'd not even mess with ubuntu anymore, but I can't, and it will take days for me to download the 64bit Mandriva free dvd. I am downloading Ubuntu 8.04 now to see if the older kernel will work at all, but was hoping for suggestions because unfortuneatly I always want to do things that require the latest kernels for some reason (lucky me).


Thanks for any and all ideas

---

### Post by Motlei on 2009-07-06
I have the same problem, upon reaching the partitioning tool, the installer does not recognize anything other than my USB external HDD.  When operating from the Live CD, the File Browser does not display any hda.  The HDD in this case is also a Western Digital, 750GB Caviar Black, model WD7501AALS.

I did not have this problem in my HP laptop which also contained SATA drives.  Windows Vista and Windows 7 did not have this problem.  The BIOS recognizes the HDD as attached to SATA port 4, which is where it is plugged into.  There are three primary partitions on this drive, two of which are occupied by Vista and Win7.  The third partition is raw space waiting to be partitioned into a primary partition for Jaunty and an extended partition for swap, /tmp, and /home.

---

### Post by presence1960 on 2009-07-06
I have read similar posts  as this and the others seemed to be successful using the alternate text based installer: [http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

---

