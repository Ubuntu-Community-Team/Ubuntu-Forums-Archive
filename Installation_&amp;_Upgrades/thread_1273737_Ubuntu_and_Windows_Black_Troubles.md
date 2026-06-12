---
title: "Ubuntu and Windows Black Troubles"
date: 2009-09-23
forum: Installation &amp; Upgrades
---

### Post by Meteshjj on 2009-09-23
[RIGHT]Recently, an old computer came into my hands.  It had Windows XP Home Edition on it, but, it being Microsoft, the operating system crashed and destroyed the boot sectors, MBR, Recovery Partition, ect.  My brother, who was the one who owned it prior to me, had absolutely no idea what to do, so he just bought a new laptop.  I thought it would be no problem to fix this computer, what with it being only a software failure. 

The computer itself is a [Compaq Presario SR1520nx](http://h10025.www1.hp.com/ewfrf/wc/product?lc=en&dlc=en&cc=us&os=228&tool=softwareCategory&query=sr1520nx&product=471644), with the only addition over the years being a second 512 RAM stick.  Like I said, not exactly high-end.

To go about this, I decided to get a copy of Windows XP Black SP3, as well as a copy of the release disc of Ubuntu 9.04 (Jaunty). At first, I tried to use the Windows partitioner to create two partitions.  This was a mistake, as Windows labeled both partitions as full as far as Ubuntu was concerned.  One disc format and Windows installation later, Ubuntu could finally use the remaining part of the NTFS section of Windows to create a ext3 partition and a swap partition to install the operation system.

The first irritant that came up was that I had no access to my external harddrive when I used the eSATA port.  The port itself is just an eSATA bracket that plugs into the SATA ports on my motherboard.  It came with my [ Antec Harddrive Enclosure](http://www.antec.com/Believe_it/product.php?id=NzA0MjIx).  I've never actually used the bracket, eSATA port, or SATA port, so I don't know where to look for that problem. I know it's not the enclosure, because the USB-B port works just fine, and the case itself is fairly new.  I decided to ignore this and just use the USB port while I waited (hopefully) for eSATA/SATA support for my motherboard in Karmic Koala.  Continuing on, I moved to the problem of drivers for my wireless card.

Here's where my troubles begin.  Ubuntu still boots correctly. At the moment, however, I can't use Ubuntu for much because it does not natively support the drivers for my wireless card, an Belkin F5D8053 N (MIMO) USB device.  I thought that was a bit odd, but decided to look for a solution here on the forums. Not finding one that I could effectively use without any sort of internet connection to the computer itself, I decided to just install the drivers on Windows. 

Again, I hit a wall.  Windows won't boot.  After installing Ubuntu, I neglected to make sure Windows would still boot.  It doesn't.  I get an MSDOS-style screen that simply says, "Starting..."  This really isn't very helpful, as I really want to use both operating systems.

Now that you've read my tale of heroism, magic, and laser-gun fights, I'd like to ask for your help.  The three things (in order of importance) that I'd like help with are these:

1)Booting Windows Black and Ubuntu

2)Using the Belkin Wireless Card

3)Using the SATA/eSATA port with my external harddrive.

Thank you for your time.[/RIGHT]

---

