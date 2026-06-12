---
title: "Bios not using all available RAM"
date: 2010-03-19
forum: Hardware
---

### Post by Waderider on 2010-03-19
Hello-

I have just removed 2 x 1GB DDR2 DIMMS from my desktop and replaced then with 2 x 2GB DDR2 DIMMS.

On boot the Bios reports only 3GB is usuable - this is before the OS boots. There are two OS's, 64 bit Ubuntu and 32 bit XP. Both report 3GB of available RAM.

The mainboard manufacturer says the board can support 4GB of RAM. Am I only seeing 3GB because of the memory card?

Thanks

---

### Post by jrssystemsnet on 2010-03-19
No, there's a setting in BIOS that you'll need to tweak to get it to report all 4GB - the language changes from one BIOS to the other, so I can't really be specific, but look for things like "memory hole" and try changing settings.

Keep a notebook of what settings you change, and if you change one and it didn't help - change it BACK immediately before trying to change a different one.

Sorry I can't be more specific. :)

---

### Post by Waderider on 2010-03-19
Thanks jrssystemsnet, unfortunately I've had no luck finding any setting in BIOS to resolve my problem. However your comments did remind of on old BIOS setting I used to see, AGP aperture size. But I digress..........

Found a comment in the mainboard support site that using the max 4GB of RAM might mean all isn't reported; so I'm going to make do with 3GB.

---

### Post by coffeecat on 2010-03-19
Are those 2GB DIMMS new or have you used them before? I wonder if one might be faulty. It might be worth putting in only one at a time and seeing whether the BIOS reports the full 2GB for both.

---

### Post by jrssystemsnet on 2010-03-19
> **Waderider said:**
> Thanks jrssystemsnet, unfortunately I've had no luck finding any setting in BIOS to resolve my problem. However your comments did remind of on old BIOS setting I used to see, AGP aperture size. But I digress..........

Found a comment in the mainboard support site that using the max 4GB of RAM might mean all isn't reported; so I'm going to make do with 3GB.Well, that sucks.  It's almost certainly the fault of the motherboard; older motherboards (before amd64 cpus became popular) generally did exactly what you describe with 4GB of RAM, and if they were GOOD motherboards, you could change the "memory hole" setting to get them to report a little over 3.6GB instead.

Maybe it's time for a nice shiny new mobo and 64-bit CPU. ;)

---

