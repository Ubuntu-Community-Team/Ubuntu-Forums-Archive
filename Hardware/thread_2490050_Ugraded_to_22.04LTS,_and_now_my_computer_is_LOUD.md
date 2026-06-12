---
title: "Ugraded to 22.04LTS, and now my computer is LOUD??"
date: 2023-08-20
forum: Hardware
---

### Post by Seamless in Northampton on 2023-08-20
Just completed the 20.04 to 22.04 transition after solving the aufs issue. And now my machine is just plain loud. I think it's the fan noise, of all the weird things. Why on earth would that increase dramatically? 

I wouldn't care, except that I record music and voiceover within noise distance of my machine!

Any pointers appreciated. Gonna start with checking the BIOS, see if some settings are changed, though I can't imagine Ubuntu would affect that.

---

### Post by TheFu on 2023-08-21
Well, check the system temperatures for everything, unless you want to burn out storage and chips.  Be certain to check drive, SSD, GPU and CPU core temps, not just the normal South/North bridge temps that sensors provides.  Some motherboards don't have good support, so you may need to load drivers or even compile a kernel modules.

"loud" isn't really descriptive. Is it just moving more are or are the clicks or grinding noises?

Of course, you should clean all the dust out from every fan and inside the case too.  If the CPU seems too hot for the workload, you might need to pull the fan off, clean the contacts and apply fresh thermal paste to get a good contact and drastically improve heat transfer.

Sometimes, things that appear connected are just coincidence and not connected at all.

I have a case fan that sometimes hits a wire inside the case.  Sounds like a playing card on a bicycle wheel from when I was a child.  I should open the side panel and carefully relocated the wire, but if the sound isn't too much, a quick "whap" on the side can move the cable off until I'm inside the case for something important.  Last weekend, I finally got inside that case and specifically arranged the wires so they wouldn't touch that fan. All is mostly quiet, even though I added a 4 disk drive cage with another fan pulling air across the 4 HDDs.

```
$ sudo hddtemp /dev/sd[a-f]
/dev/sda: Hitachi HDP725050GLA360: 49°C
/dev/sdb: WDC WD8002FZWX-00BKUA0: 54°C
/dev/sdc: WDC WD20EFRX-68AX9N0: 34°C
/dev/sdd: TOSHIBA DT01ACA200: 35°C
/dev/sde: Hitachi HUA723020ALA641: 37°C
/dev/sdf: WDC WD20EFRX-68AX9N0: 34°C
```
The last 4 drives are in the new "cage".  the other two HDDs are installed in the front-bottom of the case ... where air should be sucked through, but there isn't any fan there.  Based on the temperature differences, I should get a fan sucking air across those drives soon.  54deg isn't THAT bad, but I'd rather have them all in the mid-40s for peak temperatures.
Heck, the SSD in that system is running at 44-47.9°C.

When I look for the CPU temperatures, I can't find them.  I know it worked previously, but that was with a different release and an older kernel.  In theory, better kernel support for my CPU sensors will happen when the 6.x kernels.  I'm still running 5.15, happily.  One more think to add to my list of things to do. CPUs have thermal throttles to protect themselves - have for the last 15+ yrs, so I'm not too worried.  OTOH, HDDs are known to fail if they run too hot for too long. Google found a correlation between drive lifespan and reported drive temperatures.  Seems that being over 50deg is bad for HDD lifetimes.

---

