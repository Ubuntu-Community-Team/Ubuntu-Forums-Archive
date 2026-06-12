---
title: "USB HDD as USB stick?"
date: 2008-05-20
forum: Hardware
---

### Post by panayk on 2008-05-20
Hi!

This is mainly to satisfy my curiosity, since I don't intend to try it out, but is it possible to use an external USB disk in place of a USB flash drive?

In particular, I have purchased a music system that can play mp3's off a connected USB stick. I have a WD external USB drive (MyBook) formatted into a single NTFS partition. Naturally, the music player can't read it, but: 

If I were to create a FAT partition on the disk, would that work? Since they both use the Mass Storage device interface... Has anyone tried something like this? Also how do such players select the partition to read from? Do they use the first partition on the device?

Thanks

---

### Post by SoloSalsa on 2008-05-20
Most likely, yes (but there is a negligible chance that it might not work).  I think you should make it FAT32, though.

---

