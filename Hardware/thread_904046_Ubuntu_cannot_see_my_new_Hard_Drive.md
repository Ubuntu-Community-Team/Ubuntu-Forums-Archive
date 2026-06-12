---
title: "Ubuntu cannot see my new Hard Drive"
date: 2008-08-28
forum: Hardware
---

### Post by siriusfox on 2008-08-28
I recently bought a new Western Digital IDE hard drive for my Ubuntu server to replace a very noisy Maxor that was in it. The drive partitioning with Parted Magic worked fine, but when I went to restore my old system I found that the new drive could not be read. Even when I go into Gparted on the Ubuntu 8.04 live CD, nothing is shown.

I had this problem once before with a random hard drive that wouldn't work, but I assumed that the drive was bad. Now I'm starting to think that there might be a driver issue. If this is the case, how do I tell what driver is needed for the drive? How do I add said driver? Is another problem more likely?

-siriusfox

---

### Post by jpkotta on 2008-08-28
Post the results of this command:
```
dmesg | grep -i ata
```

---

