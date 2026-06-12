---
title: "Disk partitioning with GParted"
date: 2010-07-01
forum: Hardware
---

### Post by mpiaria on 2010-07-01
I am trying to resize my primary ext4 partition to include a large portion of unallocated disk space using a GParted Live CD.  This is proving to be very difficult as the two are not adjacent.  Here is how it breaks down:

unallocated                       1.00MiB
/dev/sda1        ext4           223.41 GiB
/dev/sda2        extended    9.48 GiB
    /dev/sda5    linux-swap  9.48 GiB
unallocated                       232.87 GiB

I want /dev/sda1 to consume all the unallocated space, but I am having a very difficult time doing so.  I can't seem to do anything except control the free space before and after it.  The extended/swap partition is in the way.  I can't move the free space to before the extended/swap partition either.  I'm pretty stumped.  Any suggestions?

---

### Post by Elfy on 2010-07-01
Boot with the livecd - gparted is in system -admin menu > Partition Editor

Right click on the swap partition - swapoff

Refresh and there should be no padlock symbols against any of the partitions. You should be able to move the extended to the right putting the unallocated next to sda1

---

### Post by byStanderone on 2010-07-01
...may i know what's in sda2 extended partition, installed 'OS' i mean?

---

### Post by mpiaria on 2010-07-01
Well it looks like it just took a little trial and error.  I finally moved things around just right.  Kinda like a jigsaw puzzle.

---

