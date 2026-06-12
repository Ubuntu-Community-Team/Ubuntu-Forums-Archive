---
title: "infrared (irda) not working on T43"
date: 2007-08-07
forum: Hardware &amp; Laptops
---

### Post by Meister_Eder on 2007-08-07
Hi,
I am unable to get my infrared running. I would like to use it for synchronizing a Palm.
 dmesg says
```

[   16.196000] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 3.
[   16.196000] nsc-ircc, chip->init
[   16.196000] nsc-ircc, Found chip at base=0x02e
[   16.196000] nsc-ircc, driver loaded (Dag Brattli)
[   16.196000] nsc_ircc_open(), can't get iobase of 0x2f8
[   16.196000] nsc-ircc, Found chip at base=0x02e
[   16.196000] nsc-ircc, driver loaded (Dag Brattli)
[   16.196000] nsc_ircc_open(), can't get iobase of 0x2f8
[   21.628000] IBM TrackPoint firmware: 0x0e, buttons: 3/3

```

I followed several howtos but irdadump does not show anything if I connect my palm and try to synchronize. I would appreciate any suggestions.

---

