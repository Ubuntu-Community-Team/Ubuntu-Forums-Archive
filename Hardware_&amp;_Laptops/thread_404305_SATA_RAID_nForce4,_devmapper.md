---
title: "SATA RAID nForce4, /dev/mapper"
date: 2007-04-08
forum: Hardware &amp; Laptops
---

### Post by jarah on 2007-04-08
Hello,
I made an upgrade from 6.06 LTS to 6.10 Edgy

On 6.06 my RAID 0 (stripe) worked perfectly. There was sata disk names like : nv_beiaxv... in dir /dev/mapper, fstab mounted them to /mnt/xxx. Everything was superb.

AFTER the upgrade to 6.10 all disk names in /dev/mapper dissapeared.
dmraid -an i dmraid -ay makes no effect

During bootup I have messages like :
'BUFFER I/O ERROR ON DEVICE sda2, logical block xxxxxxxxxxx' - or something like that (multiple times)

AFTER that I get :
'device-mapper: dm_stripe: Target length not divisable by chunk size' ....
so I don't think this is caused by wrong version of dmraid (mapper)

all this takes place on 2.6.17-11 kernel

There was no RAID problem before the upgrade

Please, give me any clues how to make it work again

---

### Post by jarah on 2007-04-08
I solved that problem.
After hours of searching I found that that was a bug in kernel. 

[https://bugs.launchpad.net/ubuntu/+source/dmraid/+bug/54246](https://bugs.launchpad.net/ubuntu/+source/dmraid/+bug/54246)

the solution is to install the latest dmraid packages in version at least 1.0.0.13rc, latest libselinux1_1.32 (unstable), and libsepol1_1.14(unstable) (which were not in ubuntu repositories)

sorry for this topic, but maybe it will help someone :D

---

### Post by brandon_r87 on 2007-04-10
Hello,

I was having the same problem and this post helped, but [this comment]("https://bugs.launchpad.net/ubuntu/+source/dmraid/+bug/54246/comments/51") on the bug page finally solved my problem.

Full URL:
[https://bugs.launchpad.net/ubuntu/+source/dmraid/+bug/54246/comments/51]("https://bugs.launchpad.net/ubuntu/+source/dmraid/+bug/54246/comments/51")

Hope this helps anyone else having problems.

---

