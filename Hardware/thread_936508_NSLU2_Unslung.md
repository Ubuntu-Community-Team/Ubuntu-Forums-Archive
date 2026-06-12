---
title: "NSLU2 Unslung?"
date: 2008-10-02
forum: Hardware
---

### Post by RealG187 on 2008-10-02
Okay I have an NSLU2 and it had firmware V2.3R24.

At that time it couldn't read my FAT32 hard drive (the image on ebay of the box said it read fat32 and NTFS, but my box didn't), but it read my 1 GB Kingston Data Traveller that was fat32). The paper that came with it said the drives "Have to be specially formatted" for the NSLU2, and after they are they cannot be used in windows (I read around and it makes them EXT3, which means they cant be read in windows directly, but in Linux they can, I know all about Linux using EXT3)

I upgraded it to V2.3R63 and it reads both, I have not tried an NTFS hard drive yet*. (It it did then this would be good since I could access fat32 and NTFS USB hard drives from Windows 98 without a driver, because when one plugs a USB Hard Drive directly into the computer on 98, they need a driver for every hard drive. But this way I would only need the network drivers)

* NTFS works on port 1 only, however the firmware release notes state the oposite
> 1. FAT32/NTFS support on Port 2 and FAT32/EXT3 support on port 1

If I would install Unslung, would I be able to still read FAT32 and NTFS and not just EXT3?

If for any weird reason I dont like Unslung, can I go back to V2.3R63?

I also am confused about this Unslinging thing:

> "Unslinging" is the process of copying the firmware to an external disk, and
configuring that external disk for installation of packages.  In order to
perform this operation, you need to log in to the NSLU2 using telnet, and you
need a suitable external disk or flash device.

This procedure is made a bit more complicated because the behavior of the NSLU2
can change depending on the presence of an external disk.

So does this make it brick proof, do i have to use red boot?

---

### Post by giants_fan on 2008-10-03
I don't know about NTFS, but you can definitely read FAT32 with unslung.  It seems that NTFS is possible (I just did a quick google search), but I've never tried it myself.

I used unslung for a few weeks but found it a little unstable and well, a little weird.  I've hence moved to Debian and it works great.  I'd recommend the Debian firmware over unslung--especially if you're already a Ubuntu user. 

As for upgrading, I used upslug and and it worked great.  And yes, according to this page:

[http://www.nslu2-linux.org/wiki/HowTo/RevertToLinksysFirmware](http://www.nslu2-linux.org/wiki/HowTo/RevertToLinksysFirmware)

You can go back to the original firmware...but I don't see why you'd want to.  =)

---

### Post by RealG187 on 2008-10-06
The guide for USBHOSTS, [here]("http://forums.maxconsole.net/showthread.php?t=111889"), says to use Unslung. But if you download the attachment, it says to type a bunch of Linux commands, so maybe Debian would work??

In case you don't know, was just wondering, or need to know here's what USBHosts is.

The PSP is a gaming and media device, it loads content off of a Sony Memory Stick. When I plug my PSP into NSLU2, normally what it does is the NSLUE mounts the PSP as a USB Device. USBHost does the oposite, it mounts the NSLU2 as a USB Device. So I plug my PSP into one of it's USB ports and a USB Hard drive into the other and I can access the contents of my USB Hard drive on my PSP. THis means I can listen to music off my USB Hard Drive, Copy files between my PSP and the harddrive, and even play backed up PSP games off the USB Hard drive, this is handy as the average PSP ISO is 1GB. The averge Memory Stick is 4 GB (~4 games). There is a 16 GB for like $200, but for less than that I could buy a 160 GB USB hard drive (10 times the space, and cheaper because hard drives are usually always cheaper than flash media [like Memory Stick])

---

### Post by RealG187 on 2008-10-07
[http://www.nslu2-linux.org/wiki/HowTo/UseTwoBusPoweredDevices](http://www.nslu2-linux.org/wiki/HowTo/UseTwoBusPoweredDevices)

Is it possible to have two USB Powered Hard Drives on the NSLU2?

---

### Post by giants_fan on 2008-10-08
Hmmm...can't tell you first hand.  I'm running mine with a single USB powered 2.5" HDD (a Western Digital Passport 250).

There are a bunch of other people's setups here:

[http://www.nslu2-linux.org/wiki/Info/WhatPeopleAreReallyUsingTheirSlugsFor](http://www.nslu2-linux.org/wiki/Info/WhatPeopleAreReallyUsingTheirSlugsFor)

But it's hard to tell if anyone is running 2 USB powered HDDs.

---

### Post by RealG187 on 2008-10-14
Does anyone have connection errors with NTFS drives attached to their NSLU2?

[http://www.nslu2-linux.org/wiki/Main/ConnectionIssue](http://www.nslu2-linux.org/wiki/Main/ConnectionIssue)
[http://www.linksysinfo.org/forums/archive/index.php?t-38423.html](http://www.linksysinfo.org/forums/archive/index.php?t-38423.html)

---

