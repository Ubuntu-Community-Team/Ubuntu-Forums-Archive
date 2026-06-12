---
title: "Ubuntu does not see external hard drive"
date: 2009-02-25
forum: Hardware
---

### Post by nyazdan2 on 2009-02-25
Hi,
Im running Ubuntu 8.10 on a dell precision t3400.
I have a external hard drive which I used to use on my old computer which was running windows xp.
When I first plugged it into my ubuntu machine it worked perfectly, the problem is that it seems like after a lengthy amount of time, ubuntu seems to lose the hardrive. Then when I unplug it and plug it back in, regardless of the port I use, ubuntu does not detect it. I have to restart my machine each time to get ubuntu to detect the drive again.
Thanks for any help!

---

### Post by taurus on 2009-02-25
With external harddrive, make sure you unmount it first even in windows (safely remove harddrive icon in the lower right corner) before you unplug it.  A lot of people just unplug it when they are finished using it which could cause all kind of trouble later.

Make sure it is plugged in.  Then, open a terminal and post the outputs of these commands.

Applications -> Accessories -> Terminal
```
dmesg | tail
sudo fdisk -l
df -h
```

---

