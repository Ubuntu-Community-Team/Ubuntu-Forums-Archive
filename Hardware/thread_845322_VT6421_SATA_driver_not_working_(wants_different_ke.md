---
title: "VT6421 SATA driver not working (wants different kernel version)"
date: 2008-06-30
forum: Hardware
---

### Post by lifeisbetterwithketchup on 2008-06-30
*** This package only supports kernel version 2.6.20-15-generic.

That's the message I get when I try to install the VIA driver from here: [http://www.viaarena.com/default.aspx?PageID=420&OSID=45&CatID=3270&SubCatID=117](http://www.viaarena.com/default.aspx?PageID=420&OSID=45&CatID=3270&SubCatID=117)

Any suggestions as to how I can get this working on my system (which has a newer kernel)?  I'm on Gutsy.

---

### Post by lifeisbetterwithketchup on 2008-07-04
Bump!

Also, if nobody can help with this, does anyone know of a good SATA PCI card that is ubuntu-friendly?

---

### Post by Jubei71 on 2008-10-17
I'm going to bump this thread. I installed Ubuntu Hardy Heron on an old PC and like what I it very much. Problem is this motherboard (Asus A8N-E) has a fried SATA controller, and I want to add one spare SATA drive to this machine, hence my interest in PCI SATA controller cards.

At the moment, I can only find ones based on the VIA VT6421 chip, so would really appreciate if someone can tell me whether Ubuntu 8.04 supports it or not. Thanks!

---

### Post by valentt on 2009-11-29
I found the answer on how to make this VIA VT6421 card work on Ubuntu:

sudo modprobe sata_via

more details on my blog:
[http://kernelreloaded.blog385.com/index.php/archives/ubuntu-and-via-vt6421-pci-sata-howto/](http://kernelreloaded.blog385.com/index.php/archives/ubuntu-and-via-vt6421-pci-sata-howto/)

---

### Post by pigphish on 2010-06-30
I can see the controller but no drives. How did you get access to your drives?

---

