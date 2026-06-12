---
title: "hard disk failure"
date: 2007-03-18
forum: Hardware &amp; Laptops
---

### Post by anv on 2007-03-18
I remember that there's a method to "put aside" those sectors which have damaged from the hard disk, is this true? is there link how to do it, which programs I need. and how much I should trust disk after this process?

---

### Post by gilgongo on 2007-03-20
You can run fsck to mark bad blocks and repair errors. Type "man fsck" at a command prompt to find out more. Bear in mind that you will need to unmount the device first before running the disk check though. This may mean you will have to boot off a rescue CD. Also, if you have more than a couple bad blocks on the disk, it will most likely totally fail before too long.

---

