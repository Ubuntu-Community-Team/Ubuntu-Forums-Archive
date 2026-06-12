---
title: "ssd will only mount as read-only"
date: 2009-04-05
forum: Hardware
---

### Post by murder2 on 2009-04-05
Hello,

I recently bought a OCZ Vertex 120GB SSD for my Dell XPS m1330, which I'm having problems with.

Installation is working fine, and everything looks good up until after a day or two, the disk is only able to mount as read-only.

This has now happened 2 times, I'm at a loss to what it can be...
The first time it happened suddenly while the computer was running, every write operation came back with the error that the file system was read only. I was then using 8.10 with ext2.
I could not fix this, so I re-installed from scratch, hoping it had something to do with me using ddresuce from my old hdd to the ssd. I then installed 9.04b with the new ext4 fs.
Then, after two days with the fresh install, I booting my pc, but it halts because it is not able to write to the disk, same error again, filesystem is read-only.

options in my /etc/fstab:
```
noatime,nodiratime,data=writeback,errors=remount-ro
```

Anybody have experienced the same or something similar? It seems to me that maybe my SSD is faulty, I am concidering installing another OS to test my theory...

Appreciate any tips or comments on how to find out why this is happening.

---

### Post by eurgain on 2009-04-29
Hi,

This is discussed (and solved) in

[http://ubuntuforums.org/showthread.php?t=1118681]("http://ubuntuforums.org/showthread.php?t=1118681")

Regards
A

---

