---
title: "gparted sees drive but Breezy installer doesn't ???"
date: 2006-03-28
forum: Hardware &amp; Laptops
---

### Post by DaBruGo on 2006-03-28
Hi folks,

I have a portable (USB) Seagate Pocket hard drive (2.5GB) that I can play with all day long using the "gparted live cd".

But, I cannot get my home PC or work PC to even see it when trying to run the Breezy Install CD. (This is the same CD that I use successfully to load onto other USB drives and/or USB memory sticks using my setup guide down in my signature lines.)

Is there some utility or module that I need to load to get the Breezy install CD to see this drive? (Windows XP sees it just fine ... sigh)

I could really use some help on this one ...


DAVE

---

### Post by DaBruGo on 2006-03-28
UPDATE:
 
When I am in gparted, it shows the drive geometry as ...
 
Cylinders = 304
Heads = 255
Sectors = 63
 
But when I run the "hdparm -g /dev/sda" command in aterm on the "gparted live cd", I get this result ...
 
Cylinders = 1022
Heads = 77
Sectors = 62
 
 
Why would they show two different values? Is there something I can do to make sure the drive geometry is correctly set. I am wondering if this is why the Ubuntu Installer can't see this USB drive.
 
Can anybody help me out on this?
 
 
DAVE

---

