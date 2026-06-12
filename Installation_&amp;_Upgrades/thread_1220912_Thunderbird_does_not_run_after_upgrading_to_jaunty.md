---
title: "Thunderbird does not run after upgrading to jaunty"
date: 2009-07-23
forum: Installation &amp; Upgrades
---

### Post by Diderik From on 2009-07-23
The title just about says it. I'm on a year old oct-core Mac Pro with 16GB RAM. After upgrading from Intrepid 64bit  to Jaunty 64bit a week ago, Thunderbird won't run. When starting the program, it is visible on the panel for 10-20 seconds or so, but then disappears. When issueing 'ps -ef', there are active Thunderbird processes, and when I get new e-mails they actually show up in the lower right hand corner. I've uninstalled, removed every trace of Thundebird, and reinstalled -- but no luck. (Of course, the new email notofications disappeared after the abovementioned steps.)

I really need Thunderbird as it is the only e-mail client supported by my university.

(On my other machine, an oct-core Nehalem on a SuperMicro motherboard with 32GB RAM with the same software, Thunderbird runs fine after updating.)

Please, help!

---

### Post by Diderik From on 2009-07-24
Well, solvedish; Thunderbird works well now, but I don't know why...

I connedcted another monitor, and managed to screw up xorg.conf. After running dexconf in recovery mode, rebooting and then setting up my new monitor in ATI Catalyst Control Center (which I couldn't do earlier), Thunderbird loaded like it should. Coincidence?

---

