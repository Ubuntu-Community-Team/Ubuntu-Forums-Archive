---
title: "AMD radeon HD 6470 resolution"
date: 2011-05-09
forum: Hardware
---

### Post by dclement on 2011-05-09
Hello,

I have a hard time setting up proper resolution for an Acer laptop with AMD radeon hd6470 (integrated) graphics under Ubuntu Lucid.

At present, fglrx package is installed, but the proprietary driver manager fails to detect anything, so there is nothing to 'activate'.

As a result, the screen resolution is stuck to 1024x768 (should be 1366 in width).

I'd appreciate any solution, even without 3D, possibly (hopefully!) with open-source driver, to get at last the screen to its native resolution.

TIA,

Regards - Daniel

---

### Post by Zingam on 2011-05-09
no proper driver support i guess

---

### Post by dclement on 2011-05-09
Hmm... I know it must be possible, because I have read (in other forum archives) about successful users with 'a proper xorg.conf'.

It is also said ([here]("http://wiki.cchtml.com/index.php/Ubuntu#Unsupported_adapter")) that the driver (fglrx) is installed but not 'loaded' because it _supposedly_ doesn't support this graphic card (wrong!).

So, my problem could be solved if someone could just explain how to force a driver to load (in xorg.conf), or just point me to the relevant Wiki section, which I couldn't locate.

---

### Post by TokyoJeff on 2011-05-11
I have the same card and the same problem.  Have spent all day going through various wikis and how-tos, removing the open source drivers, re-installing the proprietary driver, then doing the whole thing again but using the 11.5 driver from the AMD download site.

Here is what I have been able to determine:
1)  According the AMD, the 6470m is not yet listed as supported.
2)  No matter what I do, the aticonfig command tells me there is no supported driver.
3) No matter what I do, the catalyst GUI will not start.

Somehow, I managed to get back to a unity desktop--- I suspect it is now using the intel Sandybridge video card.  I think we just have to wait for AMD to support this, but this may not be a bad thing, as poking around the forum it appears that the latest catalyst drivers are reportedly a bit buggy...

JH

---

### Post by dclement on 2011-05-11
Bad news indeed.

I'll trust you and stop fiddling with the ATI proprietary driver.

Have you tried either free driver (radeon or radeonhd), possibly giving up 3D support?

Perhaps also, some nonfree package could help (maybe linux-firmware-nonfree)? 

At last, I assume you are using Lucid too. I plan to try and start from a Natty USB startup disk... Just out of ideas.

DC

---

