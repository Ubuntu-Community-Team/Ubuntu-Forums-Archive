---
title: "/home on a separate drive......."
date: 2009-04-12
forum: Installation &amp; Upgrades
---

### Post by Immolatus on 2009-04-12
I don't just want to put /home on it's own partition. I want to put it on an entirely separate drive.:popcorn:
Any thoughts??

---

### Post by aaronp on 2009-04-12
Yep, it's basically the same procedure as putting it on another partition whether it's the same drive or different one.

- Set up the desired new partition on the other drive using parted/gparted etc. If you want to use the whole drive - just make one partition.
- Mount it somewhere so you can transfer files to it.
- Use rsync to copy your home to the new partition.
- Unmount the new partition
- Clean out the home driectory so it is just empty
- Mount the new partition to /home

Should do the trick. There is a link to a good guide somewhere but I'm struggling to find it - will post back when I do.

hth
Aaron

---

### Post by aaronp on 2009-04-12
Try this guide.

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

You won't need to worry about the livecd stuff if your filesystem is not on the same drive as the one that you want to put a home partition on.

---

