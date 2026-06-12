---
title: "RAID 5 help - just mount"
date: 2006-06-13
forum: Hardware &amp; Laptops
---

### Post by koda on 2006-06-13
hi everybody!
i've managed to get my linux running but i have this problem
I have a RAID 5 array with Intel Matrix Storage as controller (so, that's a software controller)
under control center and disks and file systems, linux actually sees 4 arrays (sdb,sdc,sdd,sde) and on the last one it offers a 696 GB /dev/sdb1 partition
i thought that i just could mount it like anything else (they're just ntsc partitions) but it fails since there are bad blocks!
Later on i discovered that they were not bad blocks but a funny way of Intel to sign the disks! I also found out that i can mount these arrays with dmraid (i have version 1.0.0rc10) but it gives me this output
```
ERROR: device-mapper target type "raid45" not in kernel

```
(device mapper is version 4.4)

can you help me out with this or suggest other solutions???
thanks a lot!!
Koda

---

### Post by onlyoneskwalla on 2006-08-24
You need to patch a kernel with dm-raid45, in order to get the raid45 target support that you need.  Softwares in alpha stage right now thats why it's not in the kernel. Link here for the patch [http://people.redhat.com/~heinzm/sw/dm/dm-raid45/]("http://people.redhat.com/~heinzm/sw/dm/dm-raid45/") 

Excellent generic forum post for how to compile 2.6.17 kernel [http://www.ubuntuforums.org/showthread.php?t=217657&highlight=kernel+compiling+patch]("http://www.ubuntuforums.org/showthread.php?t=217657&highlight=kernel+compiling+patch")
Just be sure to enable the raid45 target in the kernel config. Currently Compiling a 2.6.17-11 kernel for this purpose, if ya have any questions or places you get tripped up feel free to post.

btw i know you prolly wont read this post since you posted back in june and its august now but who knows :)

---

### Post by koda on 2007-11-04
and instead i read it! a little late, but i did :)
thanks a lot for your reply!

bye
Koda

---

