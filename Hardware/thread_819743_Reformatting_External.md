---
title: "Reformatting External"
date: 2008-06-05
forum: Hardware
---

### Post by ssharps711 on 2008-06-05
I need help reformatting my external GParted is stuck on Scanning all devices. Any idea how I might go about this in another way?

---

### Post by logos34 on 2008-06-05
There's the dd command.  Run in a terminal:
[B]
sudo dd if=/dev/zero of=/dev/sdb conv=notrunc[/B]

(replace 'sdb' with your actual external hard disk)

Just be careful--be absolutely certain that you get the right device 

sudo fdisk -l

---

