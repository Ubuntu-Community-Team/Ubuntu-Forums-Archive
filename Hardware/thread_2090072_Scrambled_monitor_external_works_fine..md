---
title: "Scrambled monitor external works fine."
date: 2012-12-01
forum: Hardware
---

### Post by jonnyboysmithy on 2012-12-01
I replace my Dell D610 motherboard after the ATI x300 graphics in it died.
The new board has a problem: the internal monitor is always scrambled. From boot (bios screen) to fully booted. External monitor works fine all the time, every time.
I tested with both ubuntu and windows xp.
I'm pretty sure its a hardware fault. I checked all cables, connectors, heatsinks.. They all seem good.
 Anything else I can do/check? :???:

If I can't fix it I'll just keep using it with the external monitor..:popcorn::D

---

### Post by houseworkshy on 2012-12-01
It does sound like hardware but there is one more test to make sure.  Get an iso of Knoppix [http://www.knoppix.org/](http://www.knoppix.org/) and burn it to write once only dvd or cd ( it's frequently useful so it's well worth getting the big one. ).  Unlike most distro's Knoppix includes most of the main non-free drivers which is why it is such a good hardware tester, it also has many useful tools and superb hardware detection.  It's designed to be run live, I think they were actually the first to produce a live distro.  
If Knoppix won't run it is probably hardware, if it does obviously not.  The full bells and whistles require a fair bit of ram, it has the compiz desktop cube with gears inside it on a default bootup,  so if low on ram look at the large number of boot options.  Runs fine on my 1.8GB though.

---

