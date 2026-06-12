---
title: "Core 2 Duo Chipsets"
date: 2007-09-27
forum: Hardware &amp; Laptops
---

### Post by Gudanov on 2007-09-27
I'm looking to upgrade my computer to a Core 2 Duo processor. I'd like a chipset that isn't going to give me any trouble when installing Kubuntu Gutsy. I have an IDE DVD drive and two SATA drives. Is there a good chipset for avoiding problems? P965, P35, 945P, P31? My research has turned up lots of problems, but I figure there have to be lots of people using Ubuntu with a Core 2 Duo processor. Any advice for the smoothest experience?

---

### Post by michaelzap on 2007-09-27
I have a Core 2 Duo e6300 in an Intel D946GZ mobo, and I've never had any hardware trouble at all with Ubuntu.

---

### Post by Yoooder on 2007-09-27
I just build a new machine with an ASUS P5B Deluxe motherboard, can't cite the chipset but it seems to work quite wonderfully with stock Ubuntu Gutsy Tribe 5 so far.

---

### Post by canceLinux on 2007-09-27
i've 965 Chipset it works good :)

---

### Post by dabl on 2007-09-27
P975 works good.  Pay no attention to the silly PCI bus memory allocation error on boot -- it means nothing.  :lolflag:

---

### Post by odiseo77 on 2007-09-27
No problems here with my Core 2 Duo processor either, except for the "memory allocation" error message on boot mentioned by dabl, which certainly is absolutely harmless :) (Processor: E4400, motherboard: Intel D946GZls).

---

### Post by Gudanov on 2007-09-28
It sounds like the JMicron IDE controller problems on the P965 motherboards have been solved and that the P946G and P975 chipsets are good. That opens up a lot of options. Thanks for the responses.

Anybody have any experience with P35 with Gutsy? That one seems to have some issues, but I think one of them is the same JMicron issue that the P965  had. Well, not a problem with the chipset, but the IDE controller most of the motherboards added for IDE support. I'm hoping that the 2.6.22 kernel in Gutsy will take care of any other P35 problems and open up that chipset as well.

---

### Post by houstonbofh on 2007-09-29
> **Gudanov said:**
> It sounds like the JMicron IDE controller problems on the P965 motherboards have been solved and that the P946G and P975 chipsets are good. That opens up a lot of options. Thanks for the responses.

Anybody have any experience with P35 with Gutsy? That one seems to have some issues, but I think one of them is the same JMicron issue that the P965  had. Well, not a problem with the chipset, but the IDE controller most of the motherboards added for IDE support. I'm hoping that the 2.6.22 kernel in Gutsy will take care of any other P35 problems and open up that chipset as well.
I am very happy with my Gigabyte GA-p35-DS3L.  It has an odd LAN issue, (Well covered here) and the Sound has an eccentricity, but nothing that won't shake out soon.  I am running Gutsy, and quite fast!

---

