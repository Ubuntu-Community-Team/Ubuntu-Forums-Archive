---
title: "fdisk partition issues with 9.10"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by Cr0n_J0b on 2009-10-31
I'm having some trouble with 9.10 and my partitions.

I have 5 devices:

sda
sdd
sde
sdf
sdg

I deleted all of the partions on the drives and wrote out to disk after deleting them.

I then went back in and created a new primary partition on each.

sda1
sdd1
sde1
sdf1
sdg1

I'm trying to use them for a riad volume...anyway

mdadm complains that it can't open /dev/sda1...and sure enough...it's not listed there under devices.

what am I doing wrong?:(

---

### Post by Cr0n_J0b on 2009-10-31
WOW, I'm really confused by what's going on here.

I'm looking at the disk manager in Karmic's desktop and I can see all the disks...and they are showing up in really strange ways.

sda for example shows up and has unallocated space...though it doesn't show that it's got a partition (Fdisk shows it has a partition).  I setup a 500GB raid partition, but it's not showing in disk manager.  there is an option to setup a filesystem, but no option to setup a partition.

then on another device it shows the device as owned by dev/mapper/nvidia_gchiecgi  ....  what the hell!?!?!

I'm thinking that there is something going on with nvidia and device mapper...which I've never seen before in linux.

can anyone help?

---

