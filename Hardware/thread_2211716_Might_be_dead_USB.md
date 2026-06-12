---
title: "Might be dead USB"
date: 2014-03-17
forum: Hardware
---

### Post by ac98521 on 2014-03-17
I am trying to reformat my flash drive using disk utility or just erase all contents. but error messages pop out. My drive is supposed to be 4gb but the disk utility shows it only has 0.5 kb (please check attachment)

And another weird thing is that the terminal cannot see this. Whenever I type dev/sdb (name in disk utility) in terminal, the error comes out as input/output error.

It can't be detected too with sudo fdisk -l

Help?

---

### Post by ajgreeny on 2014-03-17
Try it with gparted and make a new partition table from the Device menu.

The device could, of course, be dead.

---

### Post by ac98521 on 2014-03-19
If it is dead. Is there a chance to make it work again?

---

### Post by sudodus on 2014-03-19
To me dead means destroyed beyond rescue. Let us hope it can be revived with ***gparted***. As long as you can see it as a drive, there is hope.

---

