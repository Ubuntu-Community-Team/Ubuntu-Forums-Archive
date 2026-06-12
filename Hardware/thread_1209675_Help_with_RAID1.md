---
title: "Help with RAID1"
date: 2009-07-10
forum: Hardware
---

### Post by beetlejuice_masterson on 2009-07-10
I've followed this guide for installing RAID1 using the alternate CD (ubuntu 9.04).

[https://help.ubuntu.com/community/In...n/SoftwareRAID](https://help.ubuntu.com/community/In...n/SoftwareRAID)

Everything seems to be fine...My partitions are correct, and when I run GParted from the LiveCD my two devices (/dev/sda and /dev/sdb) come up and are recognized as "raid" in the "flags" section.

Now, what's weird is when I run these commands from liveCD:
mkdir /data
mount -t ext3 /dev/sda1 /data
grub-install --recheck --root-directory=/data /dev/sda

The last command outputs as the contents of /boot/grub/blahblah/device.map
fd0,0
hd0,0
hd1,0

Or something like that...Anyways, I got into the bios and noticed that
Primary master and primary slave are my DVD drives, while SATA port 0 and SATA port 1 are my 2 hard-drives. Since grub is throwing an error 2 all the time I wonder if it's trying to boot from the DVD drive?

Any help or ideas appreciated!

---

