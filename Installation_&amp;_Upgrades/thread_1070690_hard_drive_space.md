---
title: "hard drive space"
date: 2009-02-15
forum: Installation &amp; Upgrades
---

### Post by hatmancan on 2009-02-15
i am new to ubunu and gnome.
i have 2 hard drives but only see one in my comp icon..
i am using mint6-linux

i still have windows on the comp. but i would like to get rid of if i need to.
now both hd's are 40 gig..i barely have anything downloaded except for the updates to mint..

i went to burn a dvd movie and it tells me i do not have enough space..
could someone give me some instructions on how to see what is using up my space?i am used to right clicking in windows and finding where space is gone..

maybe i do not have the partitions set right? is there a way of telling
ty
hat

---

### Post by oldos2er on 2009-02-15
Please post the output of
```
sudo fdisk -l
```
run in a terminal.

---

### Post by hatmancan on 2009-02-15
Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd7ddd7dd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4862    39053983+   7  HPFS/NTFS

Disk /dev/sdb: 40.0 GB, 40016019456 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x931f931f

   Device Boot      Start         End      Blocks   Id  System

---

### Post by oldos2er on 2009-02-15
Is that the entire output from the command? You appear to be missing some info for sdb.

---

### Post by hatmancan on 2009-02-15
thats all it reports to me from the command you gave me

i think there is a problem with my install somewhere?
can we investigate
hat

---

### Post by oldos2er on 2009-02-15
You have one Win* partition on sda, and sdb is showing nothing, which means it's unallocated space. Is that correct?

---

### Post by hatmancan on 2009-02-15
to be honest i have no idea what i have done..
can you suggest how to correct this?
can i re-partition without losing data?
if so how do i do this?
ty
hat

---

### Post by oldos2er on 2009-02-15
There's no data to back up, at least on sdb. You could install Mint to sdb while keeping Windows on sda, as a dual boot setup. There's info on dual-booting here: [http://psychocats.net/ubuntu/index](http://psychocats.net/ubuntu/index) and here: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

