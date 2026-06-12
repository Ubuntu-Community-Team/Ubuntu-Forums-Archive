---
title: "confused on videocard ATI vs Nvidia"
date: 2008-10-24
forum: General Help
---

### Post by SpinningAround on 2008-10-24
I'm about to buy a card and while nvidia have better drivers to ATI:s cards outperform nvidia so since I guess I will buy a ATI card would I first like to know how my ATI would work, consider that I don't play on ubuntu (use win for that) and only use some "lighter" desktop effects. Since I from time let the computer stay on do I guess that it go into sleep from time to time so how will this turn out?

Is there any good options to the standard ATI drivers?

---

### Post by starcannon on 2008-10-24
You can install the ATi proprietary drivers using the Hardware Drivers utility in the menu's: {System}>{Administration}>{Hardware Drivers}
Click on "Enable"
Reboot

If all went well you should have accelerated graphics. If not you may need to do some config file tweaking. Worst case scenario is you have to download and install them manually from [http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html)

A guide on how to install the drivers from ati.amd.com is available here: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

I would take this time to mention that the performance difference is minimal between the 2 companies, and that if your a new linux user, Nvidia is currently much easier to install under linux. Either way though, if your willing to work on it, you'll have excellent graphics and be able to enjoy compiz and full motion video.

GL and have fun.

---

### Post by porchrat on 2008-10-24
> **SpinningAround said:**
> I'm about to buy a card and while nvidia have better drivers to ATI:s cards outperform nvidia so since I guess I will buy a ATI card would I first like to know how my ATI would work, consider that I don't play on ubuntu (use win for that) and only use some "lighter" desktop effects. Since I from time let the computer stay on do I guess that it go into sleep from time to time so how will this turn out?

Is there any good options to the standard ATI drivers?

The standard Ubuntu drivers for the ATI cards are generally pretty crappy.  Luckily the ATII catalyst drivers (you get them from the ATI website) are really easy to install and they work exceptionally well.  Well enough to actually run some games in some cases (depends largely on the card in question)

Here is a [guide]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide") to show you how easy it is (you would follow the manual installation bit and trust me it is easier than it looks)

---

