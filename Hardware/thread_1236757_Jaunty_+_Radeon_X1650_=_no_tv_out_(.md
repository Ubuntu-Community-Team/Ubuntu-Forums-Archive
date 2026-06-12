---
title: "Jaunty + Radeon X1650 = no tv out :("
date: 2009-08-10
forum: Hardware
---

### Post by theregoesmyeye on 2009-08-10
Movie night!:popcorn:

I've got Ubuntu Jaunty, my network shares of movies, popcorn, and soda. But I just realized that the tv out does not work, and the atitvout in it's >200kb of glory cannot detect my tvout. Anyone else having this problem with this card? By the way, fglrx crashes X for some reason, so i'm currently using xorg-drivers-ati.


On the lighter side though, in my living area I have two 12" subs, two 6" mids, and two 1.5" tweeters ready to pump out the volume. But until  I get the tvout working, i'll just be setting in the dark staring at an off tele with all sorts of sound effects going off  :P

---

### Post by theregoesmyeye on 2009-08-22
Just giving my thread a nice bump..:lolflag:

---

### Post by BlakeWolf on 2009-08-22
I had the exact same problem using the same chipset. Apparently the proprietary driver isn't supported by the version of xorg that packs with Jaunty. And unfortunately I haven't been able to get tv-out using the "ati" driver, despite following the howto in the help-documentation.

My solution was to downgrade to Hardy and use the proprietary driver, which worked fine for a couple of weeks tv-out and all. Now, however, everything has broken down big time. Could be my fault though. I do believe that the solution is a sound one in general :)

---

### Post by theregoesmyeye on 2009-08-23
> **BlakeWolf said:**
> I had the exact same problem using the same chipset. Apparently the proprietary driver isn't supported by the version of xorg that packs with Jaunty. And unfortunately I haven't been able to get tv-out using the "ati" driver, despite following the howto in the help-documentation.

My solution was to downgrade to Hardy and use the proprietary driver, which worked fine for a couple of weeks tv-out and all. Now, however, everything has broken down big time. Could be my fault though. I do believe that the solution is a sound one in general :)

If only I had read that sooner. Believe it or not I checked this forum AFTER I uninstalled jaunty and went to hardy. Now all I need to do is figure out why the picture keeps scrolling like the Vsync is out of whack on an old tele.

---

