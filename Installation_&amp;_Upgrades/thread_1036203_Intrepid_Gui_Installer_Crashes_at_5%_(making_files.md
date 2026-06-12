---
title: "Intrepid Gui Installer Crashes at 5% (making filesystem on /)"
date: 2009-01-10
forum: Installation &amp; Upgrades
---

### Post by svet-am on 2009-01-10
First off, here's my system:
2x nVidia 8800GTX (SLI)
1x Creative Audigy 2 ZS
4GB (4x1GB DDR2) SDRAM
nVidia nForce 680i SLI mainboard from eVGA with latest BIOS
Intel Q6700 Core2Quad
1x Western Digital 500GB SATA drive (primary)
1x Seagate 400GB SATA drive (secondary)
1x Sony PATA DVD-ROM
1x LG PATA DVD-RW

I can boot into the LiveCD version of Intrepid just fine.  During the installer, Intrepid sees both of my hard disks and lets me customize my partitions.  I set things up how I want and go through the GUI and then click "install"

At this point, the installer reports that it's setting up the partition on / for my primary hard disk.  It gets to about 5% done (still while formatting /) and then all disk activity quits and I can no longer move my mouse or type on my keypad (numlock is stuck on and cannot be toggled).  At this point, the only way to get the machine to do anything is to cycle the power.

Has anyone else run into this?  I want to try to boot the installer in text-only mode but I cannot figure what the proper boot flag is in order to boot text mode instead of GUI mode.

thanks in advance!

---

### Post by mikewhatever on 2009-01-11
How do you set up the partitions, in other words, what are the partitions you create and what sizes? Can you post the output of <sudo fdisk -l> without brackets from Applications->Accessories->Terminal.
It's also advisable to check the installation cd for errors.

---

### Post by svet-am on 2009-01-11
In my rig, I was setting up the partitions as follows:

SDA:
SDA1 - /boot - 130MB
SDA2 - / - remainder of disk (about 499GB)

SDB:
SDB1 - /mnt/secondary - about 495GB
SDB2 - swap - about 4GB


I just did a test where I cleaned all partitions on SDB and left it entirely unused.

Then, on SDA, I created /boot as 130MB, / as 12GB, and swap as 4GB

In this configuration, the installer ran just fine and had no trouble.

Any ideas on what I was doing wrong with my other configuration?

---

### Post by mikewhatever on 2009-01-12
:confused:

---

