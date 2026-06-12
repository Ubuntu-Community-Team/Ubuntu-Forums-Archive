---
title: "what are amd/ati drivers like these days?"
date: 2015-02-18
forum: Hardware
---

### Post by jaarvidsen on 2015-02-18
im wondering what the amd/ati proprietary graphics drivers are like these days. im asking because i was planning to get the nvidia gtx 970 but because of the 3.5/4gb issue im exploring the option of getting a similar amd instead. 

my last experience with amd/ati was in like 2006 and the drivers were terrible on linux so ive stuck with nvidia since and never had a problem. so are the amd drivers on level with the nvidia ones nowadays, or do they still suck?

thanks

---

### Post by QIII on 2015-02-18
Hello!

AMD bought ATI in 2008 and the ATI branding has largely been dropped.

I never had issues with the ATI drivers even back when it was ATI.  I think part of the problem was always that there is a step people weren't doing -- initializing the adapters.

Currently, the AMD drivers are really good (there are still a few specific models that seem to be problematic, just like NVIDIA).  Unfortunately, the acceleration options are not as rich in Linux as they are with the NVIDIA drivers.  But if you ever want an obscenity laced explosion from Linus, look up at read his comments about NVIDIA...

Anyway, I recently tried out an AMD R9 290X and you can read about what I found [here]("http://theleftcoastgeek.net/").  With the proprietary AMD driver it works very well.  With the open source driver, not so much.  I think it will take the open source developers a little bit to get that under control, but I have great confidence they will.

The link in my signature has been updated as a result.  Installing from the Additional Drivers menu is easy, as is installation from the command line.

I think many will say that NVIDIA is still the way to go, but I've had smooth sailing with ATI/AMD.

---

### Post by Mark Phelps on 2015-02-19
I used Nvidia initially with Linux but when I went to a new PC with built-in video chipset, it was ATI -- and I've used ATI/AMD ever since.

Most of the problematic posts I see on the forum are from folks who are using "legacy" products (what AMD calls their old HD 2x/3x/4x-series cards) and are trying to force fglrx drivers to work -- which they won't because AMD dropped support for those last Summer.

For the most part, the default Radeon drivers do well.  Used to be, that to get full resolution and/or multiple monitors, you had to use the ATI drivers, but the Radeon drivers are good enough now that the AMD drivers aren't needed unless you plan on doing intensive 3D gaming.

---

