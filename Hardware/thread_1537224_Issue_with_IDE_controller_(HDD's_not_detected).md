---
title: "Issue with IDE controller (HDD's not detected?)"
date: 2010-07-23
forum: Hardware
---

### Post by vcanic on 2010-07-23
Hello,

I just recently switched from Debian to Ubuntu. The machine has several IDE harddisks that are connected to a Promise IDE controller.

It seems that the IDE controller is detected, but the harddisks connected to it aren't. Does anyone have any experience with this problem?

When I do an 'lspci' I do see the IDE controller:

*05:02.0 Mass storage controller: Promise Technology, Inc. 20269 (rev 02)*

Any help is much appreciated, thanks in advance.

---

### Post by clrg on 2010-07-23
```
sudo fdisk -l 
```

---

### Post by vcanic on 2010-07-23
Only shows the sd? disks and none of the hd? (IDE) disks.

---

### Post by clrg on 2010-07-23
That's pretty cool, never encountered a problem like this.. Hm.. The only think I can think of is to check for drivers.

---

