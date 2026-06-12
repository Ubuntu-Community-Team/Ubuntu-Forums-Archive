---
title: "RAID problem at boot, then mysteriously fixed"
date: 2009-05-05
forum: Hardware
---

### Post by patspam on 2009-05-05
Today I turned on my Ubuntu Jaunty and was told that there was a problem with one of my RAID devices. I have two RAID devices, one of them my filesystem and the other my swap (raid-1 over two hard drives). The degraded device was my main, filesystem /dev/md0.

I told the system not to start with a degraded device, and simply rebooted. Everything started perfectly the second time. Weird.

Everything seems fine with RAID now:

```
$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid1 sda1[1] sdb1[0]
      966887936 blocks [2/2] [UU]
      
md1 : active raid1 sdb5[0] sda5[1]
      9871808 blocks [2/2] [UU]
```

Should I be concerned? Should I take some sort of precautionary action?

Thanks,

Patrick

---

