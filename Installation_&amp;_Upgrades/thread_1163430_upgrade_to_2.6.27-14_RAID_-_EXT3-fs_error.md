---
title: "upgrade to 2.6.27-14: RAID - EXT3-fs error"
date: 2009-05-18
forum: Installation &amp; Upgrades
---

### Post by bvanaerde on 2009-05-18
Last week kernel **2.6.27-14** presented itself with the updates, and I installed it.
Now my RAID5 setup (that I'm using as data storage - no OS is installed here) doesn't work anymore.

After trying to mount it, and after this command:
```
dmesg | tail
```
I get this error message:
> [   26.080576] sky2 eth0: enabling interface
[   26.080943] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   27.795064] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both
[   27.795301] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   28.198513] NET: Registered protocol family 17
[   38.145004] eth0: no IPv6 routers present
[ 4402.855943] __ratelimit: 112 callbacks suppressed
[ 4402.855948] canberra-gtk-pl[7218]: segfault at 201d647c0 ip 00007fe8e6f1680c sp 00000000427c9b70 error 6 in libc-2.8.90.so[7fe8e6e9a000+169000]
[B][21356.019154] EXT3-fs error (device sdc1): ext3_check_descriptors: Block bitmap for group 912 not in group (block 164102144)!
[21356.019551] EXT3-fs: group descriptors corrupted![/B]


I get some graphical popups too... see attachments.

Funnily enough, the RAID5 setup still works on the previous kernel **2.6.27-11**.
In this kernel, I did a
```
fsck /dev/sdc1
```
which said that the file system is healthy.

On the new kernel, the same command tells me that there are problems with the journal and asks me if I want it deleted.
> Superblock has a bad ext3 journal ( inode 8 )
Clear?

I stopped the process right there, as I'm not sure this will do my data any good... I don't want to lose the file structure.

Since fsck doesn't give me any errors using the previous kernel, I suppose there's nothing wrong with my disks... no physical failure or something like that... I can access the drives without any problem in the previous kernel.

Is there someplace else I should report this as a bug, or am I just forgetting something? Maybe the RAID controller driver (RocketRaid 1740)?

---

### Post by hedefalk on 2009-09-08
I'm all of a sudden having the exact same problem on my RocketRaid 1740 configured for RAID 5. Haven't done any upgrade and it was working for a while.


> 
$ sudo mount /dev/sdb1 /mnt/raid/
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

$ dmesg | tail
[   24.560728] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   24.560961] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
[   24.560963] nf_conntrack.acct=1 kernel paramater, acct=1 nf_conntrack module option or
[   24.560965] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   29.006481] warning: `jsvc' uses 32-bit capabilities (legacy support in use)
[   34.611280] virbr0: no IPv6 routers present
[  171.461277] EXT3-fs error (device sdb1): ext3_check_descriptors: Block bitmap for group 912 not in group (block 164102144)!
[  171.461925] EXT3-fs: group descriptors corrupted!
[  318.761713] EXT3-fs error (device sdb1): ext3_check_descriptors: Block bitmap for group 912 not in group (block 164102144)!
[  318.762355] EXT3-fs: group descriptors corrupted!


$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00075d0d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60770   488134993+  8e  Linux LVM
/dev/sda2           60771       60801      249007+   5  Extended
/dev/sda5           60771       60801      248976   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe197c4a1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      182374  1464919123+  83  Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdd doesn't contain a valid partition table

Disk /dev/sde: 500.1 GB, 500107862016 bytes
251 heads, 63 sectors/track, 61770 cylinders
Units = cylinders of 15813 * 512 = 8096256 bytes
Disk identifier: 0xe197c4a1

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1      185281  1464919635+  83  Linux
/dev/sde3               1           1         512    0  Empty
Partition 3 does not end on cylinder boundary.

$ uname -r
2.6.28-15-server


sda is my boot drive and sdb-sde are the RAID 5-disks. Is my memory messed up if I think that I didn't see the disks separately on fdisk -l before, but only one sdb at 1.5 TB?

Did you find out what was the problem? I don't want to loose any data on my raid.

---

### Post by bvanaerde on 2009-09-09
> **hedefalk said:**
> sda is my boot drive and sdb-sde are the RAID 5-disks. Is my memory messed up if I think that I didn't see the disks separately on fdisk -l before, but only one sdb at 1.5 TB?

I think that's "normal". Had the same problem when the RAID drivers weren't installed. Your system then sees the disks separately.

> **hedefalk said:**
> Did you find out what was the problem? I don't want to loose any data on my raid.

I gave up, as my data is more important than trying to figure out what went wrong. As I can see in [the other thread]("http://ubuntuforums.org/showthread.php?p=7918528#post7918528"), it just seems to be a driver problem. Glad to hear it's working again.

---

