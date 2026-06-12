---
title: "Sata Controller Unitek Sil3512"
date: 2007-07-13
forum: Hardware &amp; Laptops
---

### Post by r00tn00b on 2007-07-13
After long period of not touching Ubunti for a while i wanted to try it again (i'm quite a noob when it comes to linux).
Have several problems fixed but because mobo is rather old i needed a cheap *** sata controller otherwise controller would cost more then whole box :)
Anyway i managed to get a controller true a friend named Unitek Sata Controller with Silicon Image 3512 on it, found drivers for it that should work for Unix/Linux global but was wondering before i get my mind stressed up again if this controller ever would work also when there are drivers for it.

---

### Post by Sukkula on 2007-07-13
I bought a Inline PCI sata card few days a ago, and its working perfectly. No drivers needed, just needed to add irqpoll in boot options so I could see hdd:s

```

miika@nurkkaboxi: lspci | grep Sil
0000:01:00.0 RAID bus controller: Silicon Image, Inc. SiI 3512 [SATALink/SATARaid] Serial ATA Controller (rev 01)

```

---

