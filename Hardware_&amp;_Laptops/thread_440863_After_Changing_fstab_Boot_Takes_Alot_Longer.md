---
title: "After Changing fstab Boot Takes Alot Longer"
date: 2007-05-12
forum: Hardware &amp; Laptops
---

### Post by I922sParkCir on 2007-05-12
I am setting up a friends laptop and I don't want it to auto-mount the diagnosis and windows partition, so within the fstab I've changed those partitions to "noauto" from "defaults", but now the boot take about 1.5 minutes longer and in console 1 this is displayed

> kinit: no resume image, doing normal boot...  

This is going to be used for class, so a fast boot is a must.

Thank you, this community is great.
-Jai

Edit:
I know this has something to do with hibernation, which he will use alot.

---

### Post by Spartan.II.117 on 2007-05-12
Try removing the lines instead of using no auto

---

