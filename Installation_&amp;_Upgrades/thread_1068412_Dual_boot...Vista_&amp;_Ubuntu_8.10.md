---
title: "Dual boot...Vista &amp; Ubuntu 8.10"
date: 2009-02-12
forum: Installation &amp; Upgrades
---

### Post by Tomlin on 2009-02-12
I bought a laptop with...what else....vista on it. I used the M$ shrink tool to free up space for Ubuntu (even though it wouldn't allow me to shrink it as much as I'd have liked).

I booted an Ubuntu 8.10 live DVD and get ready to install following this site's tutorial:

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=3]("http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=3")

The tutorial says to choose - "Guided - use the largest continuous free space"

This gives me this:

[http://farm4.static.flickr.com/3402/3275019697_aaf745575a.jpg?v=0]("http://farm4.static.flickr.com/3402/3275019697_aaf745575a.jpg?v=0")

Does this look right?

I need to leave vista on one partition as my wife will use it, and of course, I received no DVD from Best Buy when I bought the laptop.

Thanks.

Tomlin

---

### Post by gabo.cr on 2009-02-12
I would do:
Guided Resize SCSI and then give the partition size for Linux by moving the bar.
:)

---

### Post by CapnGimp on 2009-02-12
What you are showing in your picture is 100% of hard drive is going Ubuntu, windows wiped out. NOT what you want. I ran into same problem, I just set up my linux partitions manually there.
 Be sure and check the format box.

---

### Post by Tomlin on 2009-02-12
> **gabo.cr said:**
> I would do:
Guided Resize SCSI and then give the partition size for Linux by moving the bar.
:)

That partition is vista (123GB) the "Free space" (101GB) is the area left over after the shrink for Ubuntu. I don't want to use any of the vista partition, as everything I've read says you're asking for trouble if you use anything but vista's shrink.

---

### Post by Tomlin on 2009-02-12
> **CapnGimp said:**
> What you are showing in your picture is 100% of hard drive is going Ubuntu, windows wiped out. **NOT what you want**. I ran into same problem, I just set up my linux partitions manually there.
 Be sure and check the format box.

Yeah, for some reason it's not letting me use the free space. Choosing "Manual" gave me the same options as "Guided - use the largest continuous free space".

Tomlin

---

### Post by gabo.cr on 2009-02-12
In that case you can use "manual" but you would have to be very careful there.
If you are not using the sda3 partition at all, the you can resize that one to the size you think is better. If not, you can create a new partition.
In the the manual option, you would have to create each partition needed by Ubuntu.
I would do it like this since you have a 250G drive:

/boot   ext3   100MB
/home   ext3   (as much as you want)
/       ext3   no less than 3G.
/swap   ext3   1G

---

### Post by Tomlin on 2009-02-13
sda3 is only 5.9GB. It's the vista recovery image.

I need to be able to get Ubuntu to "see" the free space.

---

### Post by tommcd on 2009-02-13
Use manual partitioning as as Gabo.cr said. IMO you really don't need a separate /boot partition. Just create 3 partitions:
root: 10GB (since you have a big drive. This is plenty; more than you will ever need).
swap: 1GB
home: the rest.

If this does not allow Ubuntu to see the free space, use the GParted or Parted Magic live CD to partition the free space, then install Ubuntu to the root partition you create:
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
[http://partedmagic.com/](http://partedmagic.com/)

---

