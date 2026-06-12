---
title: "Installing new video card"
date: 2014-07-04
forum: Hardware
---

### Post by cedric9 on 2014-07-04
[COLOR=#000000]I'm  running Ubuntu 14.04 LTS on an old Pentium 4, and I believe that my 128MB AGP card is starting to fail after many years of service.  (Occasionally displays random horizontal dash lines).  I'm thinking about swapping it with another card that I have, but the spare card I have has 256MB, so I'm guess that Ubuntu will want a new driver?

I know what to expect when replacing a video card in Windows, but what will happen when I reboot Ubuntu with a different card?  Will it display a message stating new hardware found?  Will Ubuntu find a suitable driver on its own?  Is there any chance I might corrupt my installation of Ubuntu, and it will become unbootable?

Any advice appreciated.

[/COLOR]

---

### Post by mastablasta on 2014-07-04
if you use opensource drivers you just replace the card. hardware is checked and necessary driver loaded on boot - the Linux way.

since you have such old card chances are you are using opensource drivers. if not (if oyu are using proprietary drivers), then you need to uninstall the drivers, add the new card in and reboot.

---

### Post by Bucky Ball on 2014-07-04
> **mastablasta said:**
> if you use opensource drivers you just replace the card. hardware is checked and necessary driver loaded on boot - the Linux way.

since you have such old card chances are you are using opensource drivers. if not (if oyu are using proprietary drivers), then you need to uninstall the drivers, add the new card in and reboot.

^^^
This.

I'd chuck it in and see what gives ... :-k The rigmarole is not equivalent to doing this in Windows.

---

### Post by jp734 on 2014-07-04
If the cards are the same model and the spare you have just have more ram, I don't think it will install a new driver, would it? Is this the case?

---

### Post by cedric9 on 2014-07-04
The card with 128MB is an ATI Radeon 9800, and I think that the other one is Geforce, but I haven't taken a close look at it. I'll give it a try after the holiday and see how it goes.

---

### Post by mörgæs on 2014-07-05
You can swap the cards freely, but a better approach is to begin with a fresh install of Lubuntu 14.04 using the best of the cards.

---

### Post by cedric9 on 2014-07-09
I know this is slightly off topic, but I wanted to include it anyway, as who knows,  maybe it will help someone else in the future.  After I took out my old card,  I noticed that one of the plastic clips holding the fan was broken, and that the fan was not making good contact with the GPU.  I took the fan completely off the card, cleaned everything up, put in some new grease, and found a nylon screw and nut to replace broken clip on fan.  I've now been running it for approximately four hours, and the problem with the random horizontal dash lines seems to have gone away.

I'm just wondering if the lose fan was somehow causing problems with the GPU (maybe by rubbing on it?) or if the GPU was actually overheating? At any rate, for the moment it appears to be working fine.

---

### Post by Bucky Ball on 2014-07-09
My guess is overheating. If the fix is physically solid and secure hopefully your problem is fixed. Maybe wait 24 hours before marking this thread as solved. Good luck. ;)

---

### Post by cedric9 on 2014-07-12
Well, I've been using it for three days now without any problems.  I guess the GPU was overheating, and all it really needed was some new grease, and a new plastic screw to hold it in place.   I hope that this benefits somebody else in the future.

---

### Post by Skiddaw on 2015-02-05
I'd agree with the above.  The inside cooling fins of one Video card were 80% clogged yet the fan itself looked very clean.

---

