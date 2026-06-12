---
title: "Sony PCG-Z505JEK and Xubuntu 9.04"
date: 2009-07-11
forum: Hardware
---

### Post by pablolie on 2009-07-11
i have an old (y2k) Sony PCG-Z505JEK that i have decided to upgrade to run Xubuntu 9.04. the first attempt went very well. but i decided to give the hardware a required boost after nearly 10 years of service - i upgraded the system memory to 256k (whoa! :-)) and installed a Transcend SSD to replace the ageing 9GB IBM hard drive.

i know many would ask why bother - well, thse Sony systems have outstanding mechanicals, beayutoful metal bodies, a beautiful display - if you had one you'd try to keep it going, too. and why not take xubuntu up on its premise of being able to support humble hardware?

as we speak, i am reinstalling Xubuntu 9.04. 

i have decided to go with ext3 configured with noatime for the main SSD drive. 

the system also has a linksys wpc54g wireless card.

i will answer this message with experiences after this opening message.

---

### Post by prshah on 2009-07-11
> **pablolie said:**
> i upgraded the system memory to 256k

why not take xubuntu up on its premise of being able to support humble hardware?


I hope that's 256 MB...

Xubuntu will work well on that. You can also try #! (CrunchBang) linux if you want still better performance.

---

### Post by pablolie on 2009-07-11
it is 256mb indeed :-)

i am having the oddest issue - the install works, the system boots - but then the first update hangs.

---

### Post by pablolie on 2009-07-12
here's an update thread on this... 

[http://ubuntuforums.org/showthread.php?t=1210564](http://ubuntuforums.org/showthread.php?t=1210564)

i will experiment with updating the memory (PC100) to 512mb, even though (perhaps obsolete) sony documentation states only 192mb are supported max. perhaps that will allow for some more dramatic performance optimization.

as it is, it works quite well indeed. i just can't abide the nagging feeling this could be even snappier :-)

---

### Post by pablolie on 2009-07-18
so i was able to upgrade the memory to 308mb with addition of a 256mb pc100 module. certainly has helped performance, but it still was not enough system memory to be able to do without a swap partition (as would be better for the SSD). so for now, things stay the same.
the system was close to accepting a 512mb pc100 upgrade, but ultimately that would fail in post boot memory check for some reason. maybe that ability is a BIOS update away, but that seems impossible given Sony's atrocious support mentality. BIOS updates demand Windows *and* a floppy drive. Yes, a floppy drive. :-)

---

