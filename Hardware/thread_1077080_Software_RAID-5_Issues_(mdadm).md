---
title: "Software RAID-5 Issues (mdadm)"
date: 2009-02-22
forum: Hardware
---

### Post by shaft0 on 2009-02-22
I've got a 5 disk RAID-5 array setup with mdadm.

Here is my /proc/mdstat:

Personalities: [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0: inactive sdc1[1](S) sdf1[5](S) sde1[3](S) sdd1[2](S) sdb1[0](S)
   4883799040 blocks
unused devices: <none>

When I run "sudo mdadm -A /dev/md0 /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1 /dev/sdf1" it says:
"mdadm: /dev/md0 assembled from 3 drives and 1 spare - not enough to start the array."

I opened up gparted and all of my drives show up there, they all show up in the BIOS, and they all show up as being drives that are working, so why won't mdadm assemble the array?

Here's my specs:
Intel 2.8ghz core 2 duo
Gigabyte GA-EP45-UD3R motherboard
8gb Kingston DDR2
nVidia 7200 graphics (PCIe)
Ubuntu 8.04 x64

What else can I give you to help diagnose (and solve) my problem?

---

### Post by mikey5555 on 2009-03-17
shaft0,
Have you tried issuing **sudo modprobe md** b4 attempting to assemble/re-assemble your array?  This helps the Kernel know the **md** device.
You might try using this to assemble:
**sudo mdadm --assemble --verbose /dev/md0 /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1 /dev/sdf1** 
It is a good idea to rum gparted and check the device numbers of each drive, to verify the device numbers, and use those appropriate for yoiur hardware.

Hope this helps...  

Regards...

mikey5555

---

