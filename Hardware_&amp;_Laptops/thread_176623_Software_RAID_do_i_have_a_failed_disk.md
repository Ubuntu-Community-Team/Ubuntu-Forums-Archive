---
title: "Software RAID: do i have a failed disk?"
date: 2006-05-15
forum: Hardware &amp; Laptops
---

### Post by stein on 2006-05-15
Hi,

just put a server together w/ 2 Maxtor Maxline III 250 gb drives in a software RAID1 array on Ubuntu 5.10.

"more /proc/mdstat" gives me the following:
========================================

Personalities : [raid1]
md3 : active raid1 sda4[2](F) sdb4[1]
      222548352 blocks [2/1] [_U]

md2 : active raid1 sda3[2](F) sdb3[1]
      19534976 blocks [2/1] [_U]

md1 : active raid1 sda2[0] sdb2[1]
      2931776 blocks [2/2] [UU]

md0 : active raid1 sda1[2](F) sdb1[1]
      96256 blocks [2/1] [_U]

unused devices: <none>

========================================

Anyone know how to read the above?
Taking one line as an example (md0):
      md0 : active raid1 sda1[2](F) sdb1[1]
            96256 blocks [2/1] [_U]

1. What does the number in brackets - [2] - right
after "sda1" mean?

2. What does the "(F)" mean right after "sda1[2]?

3. What does the [2/1] mean after "96256 blocks"?

4. What does the [_U] mean?
Does this mean that sda has failed?




Referring to my mdstat output specifically,
does it mean sda has failed?

If so, why is md1 (sda2) still ok (as it is a partition
on "sda" as well)?

Any HOWTO links on how to maintain an ubuntu software
raid?

any help would be much appreciated,

Thanks in advance,

Stein

---

### Post by banadushi on 2006-05-15
[QUOTE=stein]
1. What does the number in brackets - [2] - right
after "sda1" mean?
[/QUOTE]
That it is in the 2nd position in the mirror.
[QUOTE=stein]
2. What does the "(F)" mean right after "sda1[2]?
[/QUOTE]
That the parition has failed.
[QUOTE=stein]
3. What does the [2/1] mean after "96256 blocks"?
[/QUOTE]
That there are 2 drives in the array, and only one is active.
[QUOTE=stein]
4. What does the [_U] mean?
[/QUOTE]
That one of the 2 devices are not online.
[QUOTE=stein]
Does this mean that sda has failed?
[/QUOTE]
Yep.
[QUOTE=stein]
Referring to my mdstat output specifically,
does it mean sda has failed?
[/QUOTE]
Yep.
[QUOTE=stein]
If so, why is md1 (sda2) still ok (as it is a partition
on "sda" as well)?
[/QUOTE]
Software RAID works on the block level, an array element will fail if any of the data written to it is inconsistant.  So if one block in a partition goes bad, and data is attempted to write to it, the partition will be taken out of the array group.

It is just by chance that any of the blocks that compose sda2 have not failed yet.
[QUOTE=stein]
Any HOWTO links on how to maintain an ubuntu software
raid?
[/QUOTE]
[http://tldp.org/HOWTO/Software-RAID-HOWTO.html](http://tldp.org/HOWTO/Software-RAID-HOWTO.html) is a pretty good resource, its not ubuntu specific, but software RAID pretty much preforms the same no matter what distro your using.  Also the man pages for mdadm are a good starting point.

---

