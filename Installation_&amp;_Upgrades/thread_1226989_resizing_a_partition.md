---
title: "resizing a partition"
date: 2009-07-30
forum: Installation &amp; Upgrades
---

### Post by n1h0k3r on 2009-07-30
sorry if this is in the wrong place

i have a computer with two partitions- one was 70 gig, and one is 40. i resized the 70 gig (with puppy linux on it) to 5 gig. that partition comes before the 40 gig one (ubuntu) in the gparted window. i want to increace the size of the ubuntu partition, but all the unallocated space comes before it. somehow, it doesn't want to resize in that direction. what do i do?

i tried resizing the extended, but the option is grey when i right click.

```
Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors
```

the swap partition is locked too, and so swapoff doesn't work (at least i think that's why)
thanks for the help.

---

### Post by Elfy on 2009-07-30
At a guess - resize the extended then resize the ubuntu one. No idea what you are using to do the job - but possibly also make sure swap is turned off.

If that makes no sense please post back with a bit more information - at least the result of

```
sudo fdisk -l
```

---

### Post by n1h0k3r on 2009-07-31
bump (sorry)

---

### Post by merlinus on 2009-07-31
Post results of

```
sudo fdisk -l
```

l is a lowercase L.

---

### Post by Elfy on 2009-07-31
> the swap partition is locked too, and so swapoff doesn't work (at least i think that's why)Once gparted is open - right click on the swap and you can tunr it off, alternatively from a terminal

```
sudo swapoff -a
```

---

