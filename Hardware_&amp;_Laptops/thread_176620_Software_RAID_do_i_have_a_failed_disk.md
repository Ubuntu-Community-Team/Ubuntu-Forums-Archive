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

