---
title: "create 5th partitions in ubuntu"
date: 2007-06-25
forum: Hardware &amp; Laptops
---

### Post by heart_reaver on 2007-06-25
Hi, 

When I tried to create 5th partition by gparted I am getting message:

If you want more partitions you should first create an extended partition. Such a partition can contain other partitions. Because an extended partition is also a primary partition it might be necessary to remove a primary partition first.

What can I do ?

---

### Post by vanadium on 2007-06-25
gparted is actually pretty helpfull and I couldn't say it better or clearer. You indeed can have only 4 primary partitions on a HD. This is how it works and it is a limitation for all operating systems. The only thing you can do now if you really need more partitions is to delete one of your partitions, then in the freed space, create an extended partition. In that space, you can now create several extended partitions, and with that type of partitions, there is no limitation anymore in the number of them (except for the available space of course).

---

