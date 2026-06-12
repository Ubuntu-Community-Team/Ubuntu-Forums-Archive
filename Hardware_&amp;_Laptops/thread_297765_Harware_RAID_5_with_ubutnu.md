---
title: "Harware RAID 5 with ubutnu"
date: 2006-11-11
forum: Hardware &amp; Laptops
---

### Post by nullspace on 2006-11-11
I am looking for a new mobo for my server. I was wondering what chipsets if any support a hardware raid 5 on linux. I ahve tried a couple boardsa and realised that support for linux doesn't alwasy mean that. so any suggestions?

---

### Post by PilotJLR on 2006-11-11
I've never seen ANY board with integrated hardware RAID 5... what you typically get is software RAID 5, which is no better than the RAID 5 tools any Linux system has.

If you really want hardware RAID 5, you need a add an Adaptec or LSI PCI-X controller board. If you pay less than $400 or so for this board, then you are not getting "real" hardware RAID 5!!

In other words, if this is more $$ than you want to spend, then just use mdadm to make a linux software RAID 5 array.

---

### Post by SticknClutch on 2006-11-13
I use a 3ware 9590SE PCI-e board capable of having up to 8 drives and support for RAID-5.

Ubuntu came with the kernel level drivers needed for this board. And if you google it you can find their 3DM2 web based managment tool for debian which works on ubuntu.

---

