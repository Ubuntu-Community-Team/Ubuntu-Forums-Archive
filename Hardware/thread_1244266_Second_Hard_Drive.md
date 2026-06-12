---
title: "Second Hard Drive"
date: 2009-08-19
forum: Hardware
---

### Post by Asterix1977 on 2009-08-19
Hi Guys.
I too am very new to Linux (1 day!) I too have been trying to add a second hard drive. I have tried the lines above but i think it may bee something to do with my HDD and the type of formatting??
This is the disk i am trying to mount automatically on boot:

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2019db00

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19457   156288321   42  SFS

I am guessing there is a specific line i need to add to the fstab?

Please help!

---

### Post by trundlenut on 2009-08-19
have you partioned the new drive / added a file system or does it already have data on it?

---

