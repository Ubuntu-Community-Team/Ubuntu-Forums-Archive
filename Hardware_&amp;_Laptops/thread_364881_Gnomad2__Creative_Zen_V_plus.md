---
title: "Gnomad2 / Creative Zen V plus"
date: 2007-02-18
forum: Hardware &amp; Laptops
---

### Post by bjb.butler on 2007-02-18
ive been trying to get my zen v plus connected to my pc. it doesnt even show up on my usb drives. i read the ts, but it still doesnt work. 

i have the libmtp,amarok.libnjb, but i dont know what to do when u say: configure amarok with option ---with libmtp

---

### Post by kodoku on 2007-04-25
In the terminal:

> sudo fdisk -l

You should see the player for sure as some disk called /dev/sd(a-z)#, something like sda1, sdb2, etc

then

> 
sudo mkdir /media/usbdisk

pmount /dev/*diskname* /media/usbdisk

You should see the icon on your desktop afterwards.  Then its drag and drop from there.

---

### Post by kodoku on 2007-04-25
> **bjb.butler said:**
> i have the libmtp,amarok.libnjb, but i dont know what to do when u say: configure amarok with option ---with libmtp

This means when you compile amarok manually (meaning, not with apt-get from the repositories), one step that you take is the command

> ./configure

Basically, adding an option to the configuration process is as simple as

> ./configure ---with libmtp

Are you using Feisty?  I think the amarok in the repos has mtp support by default.  Correct me if I'm wrong.

---

