---
title: "USB removable drives not mounting with nautilus"
date: 2010-04-16
forum: Hardware
---

### Post by s0l1dsnak3123 on 2010-04-16
Hey guys,

I have a curious problem: removable drives do not show up in nautilus for you to mount, despite it showing up fine under lsusb:

[[IMG]http://i.imgur.com/0K9pol.jpg[/IMG]](http://imgur.com/0K9po.png)

Nautilus -> edit -> preferences -> Media -> Browse Media When Inserted is checked

gconf-editor -> apps/nautilus/preferences/media_automount is set to true

An additional find: If I reboot with the device plugged in, it works as expected.

---

### Post by RedSingularity on 2010-04-16
With it plugged in, post the output of 

sudo fdisk -l

It should show up there.

---

### Post by s0l1dsnak3123 on 2010-04-17
Hi there, I've done that, but I don't get any output.

---

### Post by frenchy82 on 2010-04-17
Hi,

do you think that this is the same issue that this one
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/564459]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/564459")

An update seems to have changed some things severals days ago

Y really hope they find a solution

---

### Post by s0l1dsnak3123 on 2010-04-17
This bug *seems* to have been addressed after an update. I will report any further findings I have when/if I find them :P

---

