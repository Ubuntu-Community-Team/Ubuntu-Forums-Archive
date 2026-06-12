---
title: "Flickery display with Intel 82852/82855 Integrated Graphics"
date: 2007-11-10
forum: Hardware &amp; Laptops
---

### Post by Ufff on 2007-11-10
I recently installed Ubuntu 7.10 on my LifeBook E4010, which has Intel 82852/82855 integrated graphics chipset. Ubuntu autodetects graphics driver as "intel experimental modesetting driver". This results in my native 1400x1050 resolution being detected properly but for some reason the display is flickery, as if the refresh rate were too low. I tried setting refresh rate to 60Hz with no results. The flicker is especially bad with semi-transparent windows :-/ Any idea if this driver is likely to be updated in near future? Or if there's another driver available? The standard intel 82852/82855 driver doesn't support this resolution to the best of my knowledge.

---

### Post by Ufff on 2007-11-10
Well, it seems reverting to the old intel graphics driver and running 915resolution solves the flicker problem. Transparent windows look slightly weird (light stripes in background), but i can live with that. Hopefully the intel driver gets updated further to properly support modesetting.

---

