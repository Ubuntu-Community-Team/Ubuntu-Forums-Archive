---
title: "no sound in after upgrade from hardy to intrep (i have an onboard and a pci snd card)"
date: 2009-01-25
forum: Installation &amp; Upgrades
---

### Post by terrencemcg on 2009-01-25
back in the ol days of hardy the sound was excellent (actually was clearer and louder than windows) but after i've upgraded to intrep, it was all gone... i have an onboard realtek ac 97 sumthin sumthin but the right channel was damaged so i had to have a pci sound card which is a VIA 1617... it was listed differently in ubuntu (VIA 8xxx [the x's are numbers]) but it worked back in hardy... when i open the preferences>sound, there are many options to choose from (like OSS, ALSA, PULSE AUDIO etc...). i tested them one by one but no sound comes out...

---

### Post by 73ckn797 on 2009-01-25
> **terrencemcg said:**
> back in the ol days of hardy the sound was excellent (actually was clearer and louder than windows) but after i've upgraded to intrep, it was all gone... i have an onboard realtek ac 97 sumthin sumthin but the right channel was damaged so i had to have a pci sound card which is a VIA 1617... it was listed differently in ubuntu (VIA 8xxx [the x's are numbers]) but it worked back in hardy... when i open the preferences>sound, there are many options to choose from (like OSS, ALSA, PULSE AUDIO etc...). i tested them one by one but no sound comes out...

Have you disabled the on-board in BIOS?

I assume you raised the volume level settings.

---

### Post by terrencemcg on 2009-01-26
whew... that worked... thanks a lot!!! i did not thought of that prolly because hardy automatically detected which sound card has jacks in it... guess there's still a lot to come for intrep...

---

### Post by 73ckn797 on 2009-01-26
Glad to hear the problem is solved. Enjoy Ubuntu!!

---

