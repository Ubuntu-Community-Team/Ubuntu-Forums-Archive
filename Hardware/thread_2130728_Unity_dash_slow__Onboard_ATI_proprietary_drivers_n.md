---
title: "Unity dash slow / Onboard ATI proprietary drivers not available"
date: 2013-03-30
forum: Hardware
---

### Post by tstivers1990 on 2013-03-30
I'm using an onboard ATI Radeon HD 4290. It's not anything extremely powerful however it should be fully capable of running Unity-3D. The dash however is extremely slow. Just browsing applications my framerate drops significantly. I assume this is because I'm not using the proper drivers for my onboard graphics, however in software sources under the additional drivers tab, there are no drivers listed. I do have the relevant checkbox ticked to allow 3rd party drivers.

I'm running Ubuntu 12.10 x86_64 with the latest updates installed.

---

### Post by ManamiVixen on 2013-03-30
Yeah, ATI ditched all their cards older than the HD 4XXX in their proprietary drivers module. So only Ubuntu 11.10 or older can run it now. 12.04 onwards you are stuck on the open-source driver.

---

### Post by tstivers1990 on 2013-03-30
Ok, well I still don't see why Unity is this bad just opening the dash. I never had issues like this in any part of Cinnamon on Arch Linux.

---

### Post by ManamiVixen on 2013-03-30
Well Unity is a resource hog and requires a lot of OpenGL acceleration and such. So it really needs modern hardware or hardware with the proprietary drivers installed. Cinnamon dosen't need good acceleration and I don't know what you used on Arch, but I'm sure that desktop wasn't high on acceleration either.

---

### Post by tstivers1990 on 2013-03-30
I don't see where all this required acceleration is coming from. Windows 7 runs fine with aero. Every other window manager/desktop environment I've tried worked perfectly fine. Including Gnome 3 with all it's happy crap. Unity doesn't do much more than any of those, therefore there's no reason it shouldn't run perfectly fine on the same hardware that ran everything else acceptably. I attempted to use ALT+F2 then "about:config" to configure unity and disable whatever it is that's causing it to run slow, however when clicking the icon for about:config nothing happens.

---

### Post by tstivers1990 on 2013-03-30
I figured it out. I had to install compiz config settings manager, and open the unity plugin settings, and set blur to none.

---

