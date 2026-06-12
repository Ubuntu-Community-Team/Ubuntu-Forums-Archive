---
title: "[SOLVED] Dual boot with vista/ubuntu 8.10"
date: 2009-01-12
forum: Installation &amp; Upgrades
---

### Post by inwood on 2009-01-12
Trying to install ubuntu 8.10 with windows vista, Using guided partioner it
partitions 9% Vista,81% Ubuntu. I want to divide the 160 GB hdd 50/50
I presume I have to use manual partioner but need to know how to allocate the 80gb for use with Ubuntu. Hope this makes sense I am new to this. any help would be welcome

inwood

---

### Post by Partyboi2 on 2009-01-12
Create a ext3 partition and set the mount point to / (this is for system files) then make a /swap partition about x2 the amount of onboard ram but you probably will not need more then 3 gig. You can also create a /home partition that can be useful if you ever need to reinstall as all the info in your /home partition will remain untouched. So as an example you could do something like:
10 gig / (ext3)
1 gig /swap (if you had 512mb ram onboard)
69 gig /home (ext3)
or
79 gig / (ext3)
1 gig /swap

You may also want to use the resize tool that comes with vista to shrink it down before creating the partitions.

---

### Post by inwood on 2009-01-12
Thanks for that. I will give it a go when I get home later.

---

