---
title: "How big is my hard disk?"
date: 2012-06-24
forum: Hardware
---

### Post by Blackbelt2011 on 2012-06-24
I have ATA Disk** WD1600BEVS-2** which the supplier names a size of 160 GB.
When I look at the sectors, **gparted, DBAN and hdat2** show me **312.581.808** Sectors per 512.

When I calculate this with 1024 units, I get 149,1 GB disk space available (unformatted).
This is what gparted told me.

But hdat2.exe show me 160,0 GB of unformatted disk space with the same number of sectors.
Before I wiped the disk with DBAN, I looked at the existing partitions: There were 3 partitions with 78,54GB, with 81,4 GB and with 0,1 GB what makes a total of 160,04GB.
 
hdparm showed me that there was no DCO and no HPA on the disk.
So I don't know if I have the correct disk space by now.

Shouldn't there be 160 GB as before deleting the space?
Thanks,
Blackbelt2011

P.P.: DBAN showed me he wiped 312.581.807 sectors, which means only the last sector was not wiped. I didn't take that for serious....
I took DBAN because I had viruses and trojans that were hard to delete.

---

### Post by coffeecat on 2012-06-24
1 [Gigabyte]("http://en.wikipedia.org/wiki/Gigabyte") (GB) = 1,000,000,000 bytes.

1 [Gibibyte]("http://en.wikipedia.org/wiki/Gibibyte") (GiB) = 1024x1024x1024 = 1,073,741,824 bytes

160 GB (gigabytes) = 149.01 GiB (gibibytes)

If you look closely at the sizes of drives and partitions in Gparted, you'll see that it is reporting in GiB, not GB. Not all applications are so careful, and you will sometimes see gibibyte figures reported as "GB". Added to which some people insist on using the term gigabyte for 1,073,741,824 bytes - mostly for historical/traditional reasons.

All-in-all it can be quite confusing!

---

### Post by Blackbelt2011 on 2012-06-24
Before the formatting, I checked the total size of the disk in the Windows Explorer, and he showed me 160 MB. As far as 1 know in Windows calculating 1MB = 1024 KB.

---

### Post by N0oki3 on 2012-06-24
> **Blackbelt2011 said:**
> As far as 1 know in Windows calculating 1MB = 1024 KB.

It doesn't matter which OS you have, everybody and every machine has the same calculating of the space.

Except 1 byte = 8 bit.

[quote=Blackbelt2011]and he showed me 160 MB. [/quote]

Impossible. I would belive u, if you are running PC from 80's - 90's. 

When you have installed windows, did you create 1 partition or more ? Or you haven't choose the whole disk ? Becouse if you haven't, than you have a lot of unused aka wasted space on your PC

---

### Post by coffeecat on 2012-06-24
> **Blackbelt2011 said:**
> Before the formatting, I checked the total size of the disk in the Windows Explorer, and he showed me 160 MB. As far as 1 know in Windows calculating 1MB = 1024 KB.

I think you mean 160 GB, not 160 MB. If Windows is showing the size of that drive as 160GB, then it is using base 10 measurements, i.e. 1 GB = 1,000,000,000 bytes. This is because....

> **Blackbelt2011 said:**
> I have ATA Disk** WD1600BEVS-2** which the supplier names a size of 160 GB.

Manufacturers use base 10 gigabytes for measuring their drives, not gibibytes. A Western Digital 160GB drive will have approximately 1000x1000x1000x160 bytes. If you want to know exactly how many bytes are on that drive, run this terminal command in Ubuntu:

```
sudo fdisk -lu
```

And look at the first line of the output. **EDIT:**. First line of the output for the drive, that is. The first internal drive will be sda, but it's not clear from your posts whether this 160GB is an internal one or an external USB one.

---

