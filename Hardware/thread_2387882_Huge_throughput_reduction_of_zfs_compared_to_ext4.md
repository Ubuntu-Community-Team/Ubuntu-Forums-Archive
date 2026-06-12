---
title: "Huge throughput reduction of zfs compared to ext4"
date: 2018-03-25
forum: Hardware
---

### Post by lammert-nijhof on 2018-03-25
I started using zfs and I'm using disks of different physical sector sizes in one pool. I have a pool with two disks with 4096 physical sector size and one disk with a 512 physical sector size. The pool reports ashift=0, which is not very helpful. The 4096 disk seem to work fine, if I try them in gnome disk utility, they report the same throughput as in the time they were ext4 disks. The 512 disk reports only half the throughput as previously achieved with ext4. Running larger file transfers and checking with "zpool iostat" confirms the measurement of the gnome disk utility. The 512 disk slows down the whole pool. 
Note that I used those same disks in a RAID-0 configuration without any performance degradation. 

My questions are:
[LIST=1]
[*]Why is there such a large difference between zfs and ext4 throughput on that 512 disk?
[*]Will re-creating the pool with ashift=12 change anything or is the default ashift=0 in practice the same thing?
[/LIST]

Currently I partioned the 512 disk and I use only half its size for zfs to compensate for the lower throughput.

---

