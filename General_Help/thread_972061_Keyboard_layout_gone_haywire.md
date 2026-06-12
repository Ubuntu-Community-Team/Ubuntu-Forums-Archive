---
title: "Keyboard layout gone haywire?"
date: 2008-11-05
forum: General Help
---

### Post by Auraomega on 2008-11-05
I've run into a problem in the past hour or so where my keyboard has stopped working how it should do, instead of using the standard English layout, its gone weird.

I've gone through System > Prefences > Keyboard > Layouts to find that only USA was there, and after attempting to add a new layout, found the that English option is way out, most of the puctuation keys are incorrect, and none of the 4 available options give me the correct layout.

I've switched between standard USB keyboards, and using the generic option, as well as re-trying the laptop layout, but none gives even close to the correct layout.

After doing a search I found the command sudo dpkg-reconfigure xserver-org was a possible fix, but alas no luck. All other searches give hits on much older versions of Ubuntu which *only* set up English layouts.

I'm a tad confused because it was working earlier, and the only change I've done is to add GFX Grub...?

I'm on Ubuntu 8.04.

Thanks for any help.
-Aura

---

### Post by Auraomega on 2008-11-05
Sorry to bump but...

Bump.

-Aura

---

### Post by Auraomega on 2008-11-06
Has anyone got any advice? This is really bugging me and I can't find any information on how to fix...

-Aura

Edit:

Fixed it, for some odd reason the keyboard type changed to 105 keys, which was causing all the issues, after searching and finding a way to manually configure, I noticed the incorrect keyboard type.

---

