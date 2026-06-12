---
title: "Dual-boot Vista and Ubuntu."
date: 2009-09-03
forum: Installation &amp; Upgrades
---

### Post by jtan710 on 2009-09-03
Is it possible to dual boot vista and Ubuntu?Can someone guide me on doing this if it is possible.
Thanks in advance to anybody who helps.:D

---

### Post by sahabcse on 2009-09-03
yes it is possible. Try to Install ubuntu after installing windows vista, allocate one empty partition or free space (for eg E: ) then boot from ubuntu CD and the partition time choose manual partition and point out that empty partition for / also create swap partition too.

---

### Post by Mark Phelps on 2009-09-04
When you install Vista, leave room for an Ubuntu partition.  If you don't do that, then once Vista is installed, open the Disk Management utility and shrink Vista to make room.  Then, when you start the Ubuntu installer, choose manual partitioning and create the partitions you need in the unallocated space.

---

### Post by presence1960 on 2009-09-04
> **Mark Phelps said:**
> When you install Vista, leave room for an Ubuntu partition.  If you don't do that, then once Vista is installed, open the Disk Management utility and shrink Vista to make room.  Then, when you start the Ubuntu installer, choose manual partitioning and create the partitions you need in the unallocated space.

+1

Very important to use Vista's disk management utility to shrink Vista's partition to make space for Ubuntu. There is a known bug when resizing Vista with gparted or any other outside partitioning utility. Sometimes it works but other times it renders Vista unbootable. [Here]("http://bugzilla.gnome.org/show_bug.cgi?id=379482") is the bug report which still has not been solved.

---

### Post by jtan710 on 2009-09-04
kk.Thanks to evry one who replied.

---

### Post by jtan710 on 2009-09-04
kk.Thanks to everyone who helped.

---

