---
title: "Seagate 250gb - formatting - enable Ultra ATA/100 - reconfig GRUB"
date: 2006-04-30
forum: Hardware &amp; Laptops
---

### Post by bpont on 2006-04-30
Just bought a Seagate Barracuda 250gb hard drive (hasn't yet arrived).

I currently have a dual boot set up: Windoze 98 on /dev/hda and Ubuntu on /dev/hdc.  Grub boots from /dev/hda, but the menu.1st resides on /dev/hdc.

I have several questions:

What's the best linux program to format the 250gb hard drive...fdisk? cfdisk? parted?

How do I enable UDMA 100mhz transfer rate?  I've  bought the correct cable to facilitate this, but I don't know if UDMA will be utilized automatically by the kernel or if I have to configure something.

Once I pull out the old 6 gig hard drive /dev/hdc and install the new one, I'm not sure if I'll be able to boot into windoze since menu.1st will be on the removed hard drive.  As a precaution, should I create **fdisk /mbr** on the windoze partition, so at least I'll have access to one system if I run into problems?

---

