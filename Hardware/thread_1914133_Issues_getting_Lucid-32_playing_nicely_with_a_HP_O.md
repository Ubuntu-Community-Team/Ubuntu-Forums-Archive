---
title: "Issues getting Lucid-32 playing nicely with a HP Omni120"
date: 2012-01-23
forum: Hardware
---

### Post by wmcduff on 2012-01-23
Hey there; still a fairly rank amateur in Linux, but working on it.  Trying to get a Lucid running pleasantly on an HP Omni120, which is going...eh, not that well.

Two main issues:
1. The monitor won't recognize sizes larger than 800 * 600, which is a shame, as it's a 1600 * 900 pixel screen.
2. The wireless (RaLink 5390) is flaky and won't stay connected.

I've tried using xrandr to force the expansion to a higher screen for no dice, and tried downloading new AMD Radeon drivers, but it just said I needed ATI drivers of some sort.

Following [http://ubuntuforums.org/showthread.php?t=1600498](http://ubuntuforums.org/showthread.php?t=1600498) seems to have shut down the wireless completely.  I suspect partially because there was no HAS_ANTENNA_DIVERSITY_SUPPORT flag to flip, or maybe I shouldn't have flipped the ones I could.

[http://h10010.www1.hp.com/wwpc/ca/en/ho/WF06a/12454-12454-4144617-4144618-4144618-5146275.html?dnr=1](http://h10010.www1.hp.com/wwpc/ca/en/ho/WF06a/12454-12454-4144617-4144618-4144618-5146275.html?dnr=1) has the specs on the machine.  Anybody got any suggestions?

---

### Post by wmcduff on 2012-02-17
Still trying to work on this at work off and on, and no luck as of yet.

Updated link to the specs: [http://h10025.www1.hp.com/ewfrf/wc/document?docname=c03002819&tmp_task=prodinfoCategory&cc=ca&dlc=en&lang=en&lc=en&product=5156810#N320](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c03002819&tmp_task=prodinfoCategory&cc=ca&dlc=en&lang=en&lc=en&product=5156810#N320)

I guess the RadeonHD 6320 is just unsupported. :icon_frown:

---

### Post by wolfen69 on 2012-02-17
It seems your computer may be too new to be properly supported by an older version of ubuntu. I suggest trying ubuntu 11.10. You'll probably have better luck.

---

### Post by Bucky Ball on 2012-02-17
Have you plugged in an ethernet cable and gotten all updates then checked 'Additional Drivers'???

---

