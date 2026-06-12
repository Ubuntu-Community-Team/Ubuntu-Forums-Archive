---
title: "Issues with built-in AC97 detection"
date: 2011-12-03
forum: Hardware
---

### Post by difiCa on 2011-12-03
Hello!

I recently encountered a problem with my built-in sound card on a  three-and-a-bit-year-old Acer 7520G which I recently installed Linux on.  The card itself is a Realtek AC97.

This computer did the same  earlier on with Windows, which I didn't even try to fix because I didn't  need this computer for anything but now I decided to try whether this  would work with Linux. It worked fine on a clean install of Ubuntu 11.10  for some weeks. Then, one or two boots before the sound problem  appeared, I noticed that in the first screen where BIOS settings are  accessible, it was taking a relatively long time (about 15-30 seconds)  to get over one point in loading while loading everything else in a few  seconds. Everything worked fine though.

Then, one time after  closing the lid normally and the laptop going into suspend (just before this I  played videos and the sound was fine), when I opened the computer the next day and  logged in from screen lock, the window frames or Unity bar would not  show, only the contents of the windows. Tried playing a video I  imported, no sound. Reboot, no sound still. 

I tried [these]("https://help.ubuntu.com/community/SoundTroubleshooting")  directions which point to a reason that my system isn't for some reason  recognising my sound card anymore, since it or its driver are not showing up anywhere. The Acer Phoenix BIOS has no user-accessible option of enabling or  disabling the sound card, so that can't be the reason.

Any ideas  on what to try next? If someone knows a good source or repository for  downloading drivers for the AC97, that could be helpful since the few  sources I found using Google did not work and I'm guessing it's missing drivers...

---

### Post by dandnsmith on 2011-12-04
If it really is a separate sound card (not technically built-in, as that is usually taken to be a chipset on the motherboard), then you wouldn't expect BIOS settings to enable/disable it - but you might be able to influence it's performance by putting it in a different motherboard slot.
I have a built-in facility on one of my PCs which has an AC97 chipset, and that requires no added linux drivers.

---

