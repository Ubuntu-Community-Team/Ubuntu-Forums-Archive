---
title: "What SATA controller does my laptop have?"
date: 2011-11-27
forum: Hardware
---

### Post by KhaaL on 2011-11-27
I'm thinking going for a SSD soon for my laptop (Acer Aspire Timeline 1810tz) and am aiming at drives with SATA 600 standard. Before I go for it, I want to know if my computer is capable of utilizing the full power of it. According to the arch wiki (I don't have access to my laptop atm), the SATA controller is

```
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
```

(gained through lspci).

Does my laptop have a SATA 600 capable controller?

---

### Post by dabl on 2011-11-27
No.

To use a SATA 6 GB/s storage device a full speed, you need a SATA 6 GB/s controller, such as this:  [http://www.newegg.com/Product/Product.aspx?Item=N82E16815158207](http://www.newegg.com/Product/Product.aspx?Item=N82E16815158207)

or with a Marvell 9128 controller such as on this motherboard: [http://www.newegg.com/Product/Product.aspx?Item=N82E16813131641R](http://www.newegg.com/Product/Product.aspx?Item=N82E16813131641R)

Your Acer Timeline specs are on this page:  [http://www.notebookcheck.net/Review-Acer-Aspire-Timeline-1810TZ-Subnotebook.21322.0.html](http://www.notebookcheck.net/Review-Acer-Aspire-Timeline-1810TZ-Subnotebook.21322.0.html)  and there is no mention of SATA 6 GB/s.

So you can buy a 2.5" SATA SSD and get good SATA 2 performance, but not SATA 6 GB/s.

---

