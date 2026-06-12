---
title: "Installed 2 versions of Ubuntu"
date: 2009-03-24
forum: Installation &amp; Upgrades
---

### Post by chkneater on 2009-03-24
I have a hard drive that had 8.04 and 8.11 installed at the same time.  I decided to remove 8.04 and deleted the partition with gparted.  Now I am unable to format that partition to use with the main partition.  What should I do now?

---

### Post by lisati on 2009-03-24
I'm wondering where you got version 8.11 from

---

### Post by chkneater on 2009-03-24
hehe, whoops.  You know what I mean

---

### Post by LasherHN on 2009-03-24
I think if you deleted the partition already you only have to resize the one with 8.10.
Just be sure you are doing it with a live cd and that the partition is unmounted.

---

### Post by chkneater on 2009-03-24
Haven't tried that thanx.  I will try that and let you know.

---

### Post by chkneater on 2009-03-26
I've been trying that for an hour and haven't been able to resize the partition.  All partitions are unmounted but it just won't let me use the available free space?

---

### Post by chkneater on 2009-03-27
Still no luck... anyone know what I should do?

---

### Post by chkneater on 2009-03-27
All right, figured it out.  All disks were unmounted but the page files were still active.  I had to right click on the page file and select swapoff, resize the drive, then turn the swap back on and apply.

---

