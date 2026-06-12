---
title: "saving data from a former windows hdd"
date: 2007-11-03
forum: Hardware &amp; Laptops
---

### Post by hoopotus on 2007-11-03
A friend messed up his ubuntu installation and now has his hdd formatted ("quick format") with a brand new ubuntu system, having lost all his former fat partitions. Is there any tool that could recover some of his files when not a lot of data has been written to the disk yet?

We have already tried a program called testdisk. Its description matches perfectly to our demands but for some reason it doesn't find his hdd at all (for my hdd it works). He has a 180 GB hard disk with a SATA connection, it appears as /dev/sda1.

If you know and have good experiences of some, that kind of program that can be run without a boot disk, would be nice so that I can help him at the same time through an instant messenger connection. But of course any will do.

---

### Post by mrvertigo on 2007-11-03
if the disk has had data on it since then and been formatted.... you may be looking at a LOOOOOOOOOOOOONG shot not that it CANT be dont but its tough

---

### Post by hoopotus on 2007-11-04
Well you must be talking about a technique of observing the bits on the hard disk in order to find out whether they have been towards 0 or 1 before being rewritten.

But I mean it's like "quick-formatted", information about partitions deleted but the whole capacity not being physically reset to zero. I'm sorry, my fault.

Any ideas?

---

### Post by hoopotus on 2007-11-06
Anyone?

---

### Post by az on 2007-11-06
> **mrvertigo said:**
> if the disk has had data on it since then and been formatted.... you may be looking at a LOOOOOOOOOOOOONG shot not that it CANT be dont but its tough

Not at all.  It's trivial, in fact.

Find another drive to put the rescued files onto.

Use data carving software such as foremost or photorec

[http://help.ubuntu.com/community/DataRecovery](http://help.ubuntu.com/community/DataRecovery)

You can use the Ubuntu live cd or this:

[http://ubuntu-rescue-remix.org/](http://ubuntu-rescue-remix.org/)

Testdisk is great at finding lost partitions.  In this case, the partition that is lost is replaced by another, so that may explain your results.  Anyway, restoring the partition type will not change the filesystem on it.  The previous filesystem is probably not recoverable, but most of the data is still there.

---

### Post by hoopotus on 2007-11-06
Thanks. I'll try those links later.

But do you have any ideas why testdisk says it doesn't find the entire device at all? May it have something to do with the device id /dev/sda1 because mine appears as /dev/hda1 and IS detected by testdisk.

Testdisk's documentation didn't help.

---

