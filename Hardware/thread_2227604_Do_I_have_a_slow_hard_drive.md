---
title: "Do I have a slow hard drive?"
date: 2014-06-03
forum: Hardware
---

### Post by sofasurfer on 2014-06-03
I bought a new hard drive to install 14.04 on. I was not  paying attention and accidently bought a laptop hard drive, a Western Digital WD3200. I decided to go ahead and install my OS on it anyway. Now I have a system that seems to be slow sometimes. My question is, is a laptop hard drive slower than a PC hard drive? Is there a reason why my system seems slow?

---

### Post by grahammechanical on 2014-06-03
If you check the product on the manufacturers web site you can get information on spin rate and data transfer rate and if the drive has cache memory. Hard drives do differ in their specification but I am not sure if we users would notice the difference. And then there is something else to consider. Power usage. Laptop hard drives might be designed to spin down to save battery power. They then have to spin up to full speed when the drive is accessed. This is not so critical for desktop hard drives but none the less modern hard drives will have features like this because they need to meet industry standards on energy saving.

Run the Disks utility and click the 'more actions' cog icon and check out Smart Data & Self tests and Drive settings.

But I would also think about the power of the CPU, the amount RAM and especially, the graphic adapter and the capabilies of its GPU and the amount of memory it has. These things are more likely to effect performance in a way that the user can notice than the speed of a hard disk.

Regards.

---

### Post by tgalati4 on 2014-06-03
Open a terminal and post the output of:

```
sudo hdparm -tT /dev/sda
```

Slow is a relative term.  I have some Western Digital Raptor desktop drives (full size) that put out 68 MB/sec.  They are supposed to be fast with small capacity (75 GB).

> 
tgalati4@zalmint ~ $ sudo hdparm -tT /dev/sda
[sudo] password for tgalati4: 

/dev/sda:
 Timing cached reads:   8050 MB in  2.00 seconds = 4031.15 MB/sec
 Timing buffered disk reads: 206 MB in  3.02 seconds =  68.24 MB/sec
tgalati4@zalmint ~ $ sudo smartctl -a /dev/sda
smartctl 5.43 2012-06-30 r3573 [x86_64-linux-3.5.0-45-generic] (local build)
Copyright (C) 2002-12 by Bruce Allen, [http://smartmontools.sourceforge.net](http://smartmontools.sourceforge.net)

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Raptor
Device Model:     WDC WD740GD-00FLC0
Serial Number:    WD-WMAKE2382900


There are fast laptop drives that will outspin a slow desktop drive, but normally full-size, desktop drives are faster because they have bigger motors, run at full power, and don't have all of the power-saving features that tend to make the drive slower.

That being said, the latest generation Raptor drives are actually 2.5" in size (laptop platter size) with a desktop-size enclosure.  I presume that they are a lot faster, but I don't have any to test.

If you really want fast, then go with SSD.  They are 200-500 MB/sec.

---

