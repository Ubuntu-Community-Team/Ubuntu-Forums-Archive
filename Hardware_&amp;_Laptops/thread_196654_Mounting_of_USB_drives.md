---
title: "Mounting of USB drives"
date: 2006-06-14
forum: Hardware &amp; Laptops
---

### Post by WebDrake on 2006-06-14
Under Ubuntu I found that volumes on USB drives were mounted according to the volume label: e.g. a partition labelled "DOCUMENTS" would be mounted as /media/DOCUMENTS/

I've found that under Kubuntu things are different, that the USB drives mount as simply /media/sda1 , /media/sda2 , /media/sdb1 etc.  How do I change settings so that they are mounted by label where possible?

Thanks :)

---

### Post by kb3hkg on 2006-06-15
/etc/fstab

edit the mount points it uses

---

### Post by WebDrake on 2006-06-16
[QUOTE=kb3hkg]/etc/fstab

edit the mount points it uses[/QUOTE]
Sorry, I probably didn't make clear the problem.  I'm not talking about /etc/fstab settings, obviously I could change those.

I'm talking about USB drives that are not in the /etc/fstab file, that are automatically mounted when plugged in.

---

