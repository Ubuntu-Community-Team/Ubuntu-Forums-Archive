---
title: "Gutsy support for &quot;PINNACLE PCTV Dual DVB-T PCI&quot;?"
date: 2007-11-30
forum: Hardware &amp; Laptops
---

### Post by Ompul on 2007-11-30
Does Gutsy supports the PCI card for digital TV "PINNACLE PCTV Dual DVB-T PCI"?

I'm looking for a used one and it would be good to know if it is compatible before I bid for that card.

Thank you?

---

### Post by Kropotkin on 2007-12-07
The kernel module is included in the current distribution:

```
~$ modprobe -l |  grep saa7134-dvb
/lib/modules/2.6.22-14-generic/kernel/drivers/media/video/saa7134/saa7134-dvb.ko
```

More info here: [http://www.linuxtv.org/v4lwiki/index.php/Pinnacle_PCTV_310i]("http://www.linuxtv.org/v4lwiki/index.php/Pinnacle_PCTV_310i")

Let us know how you fare..

---

