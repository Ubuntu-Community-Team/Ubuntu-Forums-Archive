---
title: "No DMA on my dvdrw drive"
date: 2005-03-14
forum: Hardware &amp; Laptops
---

### Post by kagou on 2005-03-14
I'v a Medion 40653 [description](http://forum.hardware.fr/hardwarefr/MiniPCPortablesPDA/sujet-1459-1.htm) 

I had to put "hdc=noprobe hdc=cdrom" to kernel's parameters.
If not, hal crash and all the sytem (gnome) too.

I'v put via82cxxx first on /etc/modules.

But I can't change DMA with "hdparm -d 1 /dev/hdc". It's not permitted (of course i do this under root)

All is ok, but reading a DVD or extracting an audio cd are very bad.

Any ideas ?

---

### Post by kagou on 2005-03-31
I'v found the problem. It's the RICOH dvd drive  :???: 
I'v threw it away, and put a NEC6500 (dvd writer, double layer).

All is working with DMA.
I'v switch the DD 4200tr by a 7200tr and all is rocking.

I'v tested the hoary daily 30/03/2005 and .... amazing !!! I'm the most happy man in the world  8)

---

