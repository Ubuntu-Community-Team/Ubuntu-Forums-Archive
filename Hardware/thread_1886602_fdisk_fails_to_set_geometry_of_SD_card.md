---
title: "fdisk fails to set geometry of SD card"
date: 2011-11-25
forum: Hardware
---

### Post by andyjjones on 2011-11-25
Hi,

This my first post on the Ubuntu forums.

I am attempting to follow [this](http://code.google.com/p/beagleboard/wiki/LinuxBootDiskFormat) tutorial on how to use fdisk to set the geometry of an SD card, and then create two partitions and format them both.  This tutorial is for BeagleBoard.  I am running Ubuntu 11.10.

Setting the geometry is causing me massive headaches.  When I go into Expert Mode and set the number of heads, sectors and cylinders, everything seems to be just fine.  For example, if I set the geometry for: 

Heads: 255
Sectors: 63
Cylinders: 124

The partition table then prints: 
```
255 heads, 63 sectors/track, 124 cylinders, total 1995776 sectors
```Everything looks fine so far.  But when I write the changes, return to shell, re-enter fdisk and re-print the partition table, I get rubbish output.  32 heads, and I forget the rest.  

My boss has a script on his computer which does everything outlined in that tutorial.  He ran that script on my SD card, and when I used fdisk again to print the table, everything seems normal: 

```
255 heads, 63 sectors/track, 124 cylinders, total 1995776 sectors
```So it seems to me that this isn't an SD card hardware problem, but an fdisk problem, or a problem with how fdisk interacts with this hardware.  Any ideas?

---

### Post by BC59 on 2011-11-25
On the same page of beagleboard, if you look down to the comments you see this:

> Comment by challi...@gmail.com, Aug 5, 2009
As noted elsewhere, there is a typo under "Create the FAT32 partition for booting and transferring files from Windows". Type simply 51? and not the +50 as indicated. Also, for unknown reasons, after the first fdisk on a SanDisk? 2GB SD Card (about the most common card you can find) the total bytes shows up under fdisk as 1977614336 and not the full 2GB. When you do the calculation above, you end up with number of cylinders = 240, not 245. My resulting SD Card was not recognized by the X-Loader until I corrected this.

---

### Post by andyjjones on 2011-11-25
My problem is not that x-loader won't recognize my SD card.  The problem is much more basic; fdisk will not recognize its own work.

Besides; the [+50] does not matter, right?  I was under the impression that the FAT32 partition can be any size, just so long as it is big enough to contain (in my case) MLO, u-boot.bin and uImage.

---

### Post by BC59 on 2011-11-25
I would try to format first of all the SD in FAT32, but under Windows.

---

