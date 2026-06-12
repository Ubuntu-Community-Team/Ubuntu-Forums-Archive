---
title: "USB hard drive issues!"
date: 2007-04-27
forum: Hardware &amp; Laptops
---

### Post by string158 on 2007-04-27
Hi,
I have an 200gb external USB hard drive which is partitioned into two 100gb partitions - sda5 and sda6.  When I connect it Ubuntu loads it as disk and disk-1.  However the it loads them in a different order each time i connect the device.  This wouldnt be too much of an issue,  except my music collection is on one of the partitions so Exaile has to rescan its music library almost every use it.  

Is there anyway I can make sure the partitions load up in the same order each time the device is connected?
Cheers.

---

### Post by gyrev on 2007-04-27
Hi, I'm also searching information on USB drives. not for my music, but for backup scripts (local computer and remote laptop)

Here's what I've found out:
if you look at Place/Computer*, you see all mounted and unmounted disks. you can right click on your unmounted drive (let's say the one with your music), look at Properties, and last page Partition (or volume) you can specify a mount point. if you double-click on that drive, it'll be mounted at the right place.

now, what I'm looking for, is modifying the mount options. but looks like I haven't found the right syntax... if anyone has an idea...


(* this is a simple translation of the menus, hope it's right...)


Hope it'll help...

---

### Post by string158 on 2007-04-27
cheers,  that seems to have sorted it!!
Sorry im relatively new to linux, so can't really help with the mount options

---

