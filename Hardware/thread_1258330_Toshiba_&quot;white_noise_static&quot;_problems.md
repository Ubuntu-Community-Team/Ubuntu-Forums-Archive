---
title: "Toshiba &quot;white noise static&quot; problems"
date: 2009-09-04
forum: Hardware
---

### Post by Juan_Marco on 2009-09-04
I'm not sure where to post this, but considering the headaches it gave me, it needs to be posted somewhere. 

I have a Toshiba Satellite A355D, it came preinstalled with 64 bit Vista. I installed Ubuntu 9.0.4 with Wubi. 

It ran great, but I kept having trouble with the sound getting broken in ubuntu. From the time ubuntu booted up, there would be a white noise, static sound from the speakers. It appeared to be completely random, didn't seem to be any pattern to what was breaking it. 
When it did break, it usually messed up the sound in vista too, same white noise sound from time I booted it up. The only fix that seemed to work was to uninstall Ubuntu, reinstall the sound drivers in vista, then reinstall ubuntu. 

Well it happened again today, and I figured since it was happening in both os's maybe a bios option could fix it. 
I disabled "processor assisted virtualization" and "legacy usb support", rebooted and checked both os's, sound worked fine in both without having to uninstall or reinstall anything.

Hope this helps someone who has been beating their head against the wall like I have been. :D

Ubuntu berry berry gud. Like em heap big.

---

### Post by Juan_Marco on 2009-09-04
Sound problems came back again, went back into the BIOS, changed "Processor Assisted Virtualization" back, next boot sound was fine. Seems like it doesn't matter what it is set on, but for some reason changing it fixes the sound.

---

