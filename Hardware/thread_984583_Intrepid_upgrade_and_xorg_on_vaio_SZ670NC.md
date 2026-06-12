---
title: "Intrepid upgrade and xorg on vaio SZ670N/C"
date: 2008-11-16
forum: Hardware
---

### Post by Gothnet on 2008-11-16
Hi all,

I've been a happy ubuntu user for a little over a year now, when I picked up my vaio last year I put gutsy on it and all was well. ALSA didn't pick up the headphone jack but a quick recompile from alsa source and all was well. The laptop has dual gfx cards, an nVidia 8400M GS and an Intel X3100/965. Only one is on at a time and I stuck in a startup script to detect which was active and configure x accordingly.

I also got it to detect if the laptop was in its dock and swap in the dual-screen xorg.conf I had.

I upgraded to Hardy and the headphone jack thing came back, no big deal, same solution.

Now I've upgraded to Intrepid and I'm having X problems. Firstly, X doesn't start at all when the laptop is in the dock in speed (nVidia) mode. When it's not in the dock all is well and I can even run dual screens. In the dock X reports "no screens found". I've tried uninstalling the nVidia binary driver, I've tried installing the one from nVidia, I've uninstalled and reinstalled most of xorg, I've downgraded to the 173 series. None of it helps.

In stamina (intel) mode I used to be able to get a decent resolution on both screens, 1280x800 on one and 1280x1024 on the other, but the screen resolution app only displays widescreen resolutions as available for my non-widescreen external LCD, and I can't get it to do much else. Even tweaking xorg.conf doesn't seem to have helped.

Anyone got any ideas why either may be happening? Can provide config files/logs etc.

---

