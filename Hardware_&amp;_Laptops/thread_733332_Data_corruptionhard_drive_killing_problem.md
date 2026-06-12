---
title: "Data corruption/hard drive killing problem"
date: 2008-03-23
forum: Hardware &amp; Laptops
---

### Post by nitromanrc on 2008-03-23
hey guys, here's my computer...
Motherboard: Biostar Geforce 6100 m9
CPU: AMD Athlon x2 3800+
2GB ram
Seagate Barracuda 7200.10 250GB SATA

alright everything worked beautifully until i got the new hard drive (christmas)...it worked for a couple of months...then i booted up and got a bunch of gross errors like this (this isn't the exact thing...i saw this in another forum and its very similar```
> > [  841.645699] ata1.00: exception Emask 0x10 SAct 0x2 SErr 0x400100 action 
> > 0x2 frozen
> > [  841.645708] ata1.00: (irq_stat 0x08000000, interface fatal error)
> > [  841.645719] ata1.00: cmd 61/00:08:17:31:f1/04:00:03:00:00/40 tag 1 cdb 
> > 0x0 data 524288 out
> > [  841.645721]          res 40/00:18:5f:fa:b9/00:00:01:00:00/40 Emask 0x10 
> > (ATA bus error)
> > [  841.947855] ata1: soft resetting port
> > [  842.447515] ata1: softreset failed (1st FIS failed)
> > [  842.447526] ata1: softreset failed, retrying in 5 secs
> > [  847.445028] ata1: hard resetting port
```

so i tried just low level formatting (w/ the seagate utility) and updating my BIOS. Then i reinstalled...and it worked, up until i upgraded from a 486 to a 686 kernel (im running x86...not 64 bit) then it did the same thing...and ruined the hard drive..so i RMAed the hdd...just thinking that was the problem...but now just today, running a 486 kernel, w/ the new drive...it did it again. im not sure what the problem is, but its very annoying. I think im going to RMA the mobo now...hopefully its still under warranty...if not ill get an ASUS probably... are there any other ideas before i RMA? or are there any known probs with this mobo and debian/ubuntu (it happened with both) or this hdd?


o yeah...where it says (ATA bus error in this code, it says that now...but earlier it said (Media error)

---

### Post by tgalati4 on 2008-03-23
It could be a cable problem or power connector problem.  Try changing both.

---

