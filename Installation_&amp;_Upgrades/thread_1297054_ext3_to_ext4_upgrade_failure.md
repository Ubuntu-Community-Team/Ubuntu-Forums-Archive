---
title: "ext3 to ext4 upgrade failure"
date: 2009-10-21
forum: Installation &amp; Upgrades
---

### Post by xyepblra on 2009-10-21
Guys, I have screwed up my / and /home filesystem by following the instructions provided at [http://maketecheasier.com/how-to-upgrade-from-ext3-to-ext4-without-formatting-the-hard-disk/2009/04/21#more-4157](http://maketecheasier.com/how-to-upgrade-from-ext3-to-ext4-without-formatting-the-hard-disk/2009/04/21#more-4157).
What I can access now is just a command line preceding the Jaunty loading. I am being prompted the read-only file system in /root/ error.

---

### Post by stlsaint on 2009-10-21
it looks like you mounted your filesystem on /mnt..

please post the output of this:


```
df -h
```

---

### Post by xyepblra on 2009-10-22
On the 4th attempt those instructions I mentioned earlier have worked fine for me, but it's been just my / partition file system upgraded to ext4. My /home is located on a different partition, so now I need help changing it's file system carefully and smoothly. Ideas and fool-proof instructions will be highly appreciated.

---

