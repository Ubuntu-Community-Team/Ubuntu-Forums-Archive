---
title: "Software raid failed after dist-upgrade"
date: 2009-07-13
forum: Hardware
---

### Post by altavatar on 2009-07-13
Hello, one of my linuxraid raid arrays failed after a recent dist-upgrade which upgraded the kernel to to 2.6.28-13 from -11.

$ cat /proc/mdstat

```

# cat /proc/mdstat
md_d4 : inactive sde1[1](S)
      1465135936 blocks

md3 : active raid5 sdb4[2] sda4[0] sdc4[1]
      1365331968 blocks level 5, 64k chunk, algorithm 2 [3/3] [UUU]
...

```It only shows 1 innactive raid device: inactive sde1[1](S) (slave). This should actually be active, and it should be picking up sdd1 too. 

When I reboot to the -11 kernel, only 1of2 raid partitions gets picked up, but at least i can make it active and re-add the other drive. 

Note that this is linux software raid (ref: [http://tldp.org/HOWTO/Software-RAID-HOWTO.html](http://tldp.org/HOWTO/Software-RAID-HOWTO.html) ) I'm not using hardware raid or the onboard controller's raid support.

Any ideas?

---

