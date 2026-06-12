---
title: "Kingston USB memory"
date: 2006-01-27
forum: Hardware &amp; Laptops
---

### Post by sonny on 2006-01-27
Hi... I recently bought a Kingston usb memory stick (DTIU3/1GB), It has 2 partitions in it, the first is the actual memory, where you can store files and stuff, the other one is a 4.1 MB partition, where a kind of app is store, if I conect it to a windows machine, it displays a menu showing a bunch of "goodies" like secure password, installation of apps, and other things I don't see the point in having them. Both Linux and Windows see this partition as a CD, and mount it as such, therefore is READ ONLY, I ran dmesg and got this:
[4396493.972000] ISO 9660 Extensions: Microsoft Joliet Level 3
[4396493.972000] ISOFS: changing to secondary root

I guess that is why it's mounted as a CD, and therefore the read only thing, my question is, How the hell can I get rid of it?? To farmat that partition with an other filesystem. Yes, I've tried gparted, and it doesn't see it, because it thinks it's a CD, therefore it doesn't care about it. Because most of friends, family and in my work use windows, I don't want to see the menu each time I plug it in, because I just don't like it, and it takes a while when the app scans the usb, and tells me it is recommended that I should install the software, to add apps, and some other stuff I won't use.

Any ideas??

---

