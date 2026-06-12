---
title: "Dual Monitors, ATI Radeon Xpress 200M?"
date: 2012-01-12
forum: Hardware
---

### Post by clevertomato on 2012-01-12
I have an old Gateway notebook. Jaunty runs perfectly on it but it is no longer supported and that presents a variety of issues for me as time goes by. I want to run Lucid on it but the BCM4318 wifi card will not stay connected, though it is officially said to work. I've spent hours on this with no success. I finally decided to try Oneiric Ocelet, even though it's such an old PC. The wifi works again, but now I want to use the s-video output to use my TV as a second display. It will not recognize any second display in the display properties. It seems no version past Jaunty is going to work on this notebook.

video: ATI Radeon XPRESS 200M 5955 (PCIE)

The proprietary ATI drivers haven't worked for this card for a long time, so I can't even try those.

The bummer is Windows XP works flawlessly on it as always, dual monitors and all. Plug in TV and voila! It works. A big reason I switched to Linux years ago was because it allowed prolonged use of older hardware. This doesn't seem to be coming true for me in this case.

(unrelated: Unity makes Linux practically unusable to me, which is another major downside for moving forward with Ubuntu, but that's another issue.)

---

### Post by mastablasta on 2012-01-12
there might be hope (though from what i read this card has poor linux support-at least in 10.04):
[http://www.x.org/wiki/radeon](http://www.x.org/wiki/radeon)
>  
**Dual-head Support**
See the [XRandR 1.2 documentation]("http://wiki.x.org/wiki/Projects/XRandR") for how to set up multiple monitors. 

 
newer version of Opensource drivers works seems to support your card better...
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
 
to speed up the things why not use Xubuntu 11.10?
 
ok anyway WinXP works fine, but the OS (especially it's kernel) is from 2001, while 11.10 is from 2011. Old Ubuntu, as you already know, also works fine. ;-)
 
Good luck solving the issue.

---

### Post by Mark Phelps on 2012-01-12
> **shawnboy said:**
> A big reason I switched to Linux years ago was because it allowed prolonged use of older hardware. 

Not to nitpick ... but it still does.

The case you mention, of "legacy" ATI equipment was the specific fault of ATI, not the Linux community.  The Linux community still provides video drivers for that card, but AMD does not. And, unlike with AMD, the drivers keep getting updated and improved, year after year.

I had an X1650 card when ATI did that, and was using the restricted drivers just fine.  When AMD dropped support, I quit buying ATI cards.

---

