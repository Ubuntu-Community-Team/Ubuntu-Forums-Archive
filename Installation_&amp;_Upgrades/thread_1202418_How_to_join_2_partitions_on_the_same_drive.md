---
title: "How to join 2 partitions on the same drive?"
date: 2009-07-02
forum: Installation &amp; Upgrades
---

### Post by laurik on 2009-07-02
I have just upgraded my hard drive and copied my existing Ubuntu setup on it.  Copy process created one partition on the new drive of same size as the old drive and then created an empty partition for the remainder space.

How can I join these two partitions to create just one large partition?

Thank you for any help!

---

### Post by Sef on 2009-07-02
1) Is your data backed up?

2) How big are the partitions?

3) Why not use the other one as a home partition, so your data is separate from the os?

---

### Post by laurik on 2009-07-02
> **Sef said:**
> 1) Is your data backed up?

2) How big are the partitions?

3) Why not use the other one as a home partition, so your data is separate from the os?

1. no data yet, but a very nice Ubuntu installed with all kinds of tweaks which I don't want to lose.

2. About 120GB each

3. I just like to have everything on one partition - easier to share and I don't have to worry about losing operating system space.  Also eventually I will increase the size of the hard drive - life is simpler with one partition.

Regards,
Laurik

---

### Post by Mark Phelps on 2009-07-03
You can't basically "join" partitions.  What you will need to do is remove the second partition and expand the first partition to fill the now unallocated space.

---

### Post by Jose Catre-Vandis on 2009-07-03
> **Mark Phelps said:**
> You can't basically "join" partitions.  What you will need to do is remove the second partition and expand the first partition to fill the now unallocated space.

So, copy over/backup all the data you need from the "old partition" (and to be on the safe side backup your new partition too), then start up gparted. If not installed:
```
sudo apt-get install gparted
```
then run
```
sudo gparted
```

You may need to unmount partitions in order to delete and resize, and best to reboot when you are done. It may take some time to do the resizing, and best to leave PC alone while gparted does its stuff

---

### Post by laurik on 2009-07-05
Thank you Mark and Jose - that did it!  Just after a week or two I just love this Linux (Ubuntu) world!

Laurik

---

