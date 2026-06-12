---
title: "Will more or less processor CACHE effect boot load time."
date: 2009-01-05
forum: Hardware
---

### Post by concerto on 2009-01-05
Hey Guys!  I'm in the market for a new laptop.  I was wondering if I would choose to select 6 MB of processor cache if I would notice any difference with boot up times or application start up times as opposed to like 2 MB of processor cache.

It would be awesome to have a laptop with a very fast boot up and startup rate but would be stupid to blow money on something that I would never use.

Any other suggestions on boot up speed besides a SSD instead of a HD????????

---

### Post by concerto on 2009-01-07
Does anyone know if processor cache has any performance effect having to do with startup or boot speeds?!?!?!?!?

Is cache just for gaming?

---

### Post by igknighted on 2009-01-07
Shouldn't really do all that much.  Cache is just like RAM, except the processor can get to it much faster.  Since booting involves going to the HD a lot, that is usually the bottleneck.  You don't need a SSD, but a SATA-300 drive at 7200rpm will likely boot faster than a typical 5400rpm laptop drive (NB, the 7200rpm drive will also drain battery faster, so it's a little give and take)

All this said, Ubuntu can fairly easily be made to boot in 5-10 seconds (on decent but not great hardware) if you really want to get you hands dirty customizing the boot process (turning off things you don't need, and re-arranging the order of things turned on).

---

### Post by sdennie on 2009-01-07
igknighteds explanation about why a larger L2 cache won't improve boot speed is good.  Caches hide latency and the L2 cache hides latency from memory to processor.  The boot process is largely latency between disk and memory.

I've actually found that for laptops, the best way to improve the boot speed is to not reboot.  Instead, make sure to buy a machine that is known to support suspend/resume.  Not only will it "reboot" (resume) much faster but, all your apps are already open and your disk cache will already be primed and so the machine will be much more responsive than it would be after a reboot.

---

### Post by concerto on 2009-01-08
Thats awesome guys.  Thanks for your help.  I have a problem with hibernating and sleep features with my desktop computer.  DO you guys have any suggestions for a well supported laptop in these categories.?

---

