---
title: "Partition missing"
date: 2010-03-17
forum: Hardware
---

### Post by lemmy999 on 2010-03-17
I have been having some issues with my EEEPC 900 and tried to  reinstall 9.10. The re-install didn't work (not sure why) Suspecting a SSD issue I checked out the disks with Gparted. My onboard SSD is not detected. 

I have done some research and know the following
[HTML]ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 4034 MB, 4034838528 bytes
255 heads, 63 sectors/track, 490 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sda doesn't contain a valid partition table

Disk /dev/sdb: 16.1 GB, 16139354112 bytes
255 heads, 63 sectors/track, 1962 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000aa898

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1824    14651248+  83  Linux
/dev/sdb2            1825        1962     1108485    5  Extended
/dev/sdb5            1825        1962     1108453+  82  Linux swap / Solaris
[/HTML]

and 
[HTML]ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sdb1: UUID="d9156e9f-ed1b-44e1-b307-2557e0211b98" TYPE="ext4" 
/dev/sdb5: UUID="f959d3ce-265c-425d-943a-8afdc7eb843d" TYPE="swap" 
/dev/sdc1: LABEL="" UUID="316C-6784" TYPE="vfat"[/HTML]

I think I  need to amend the partition table but don't know how. Any other suggestions? I have tried Testdisk as well but its documentation is less than clear in this situation and I don't want to totally bork this machine

---

