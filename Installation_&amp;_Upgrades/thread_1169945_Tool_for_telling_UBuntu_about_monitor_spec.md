---
title: "Tool for telling UBuntu about monitor spec"
date: 2009-05-25
forum: Installation &amp; Upgrades
---

### Post by artsci2 on 2009-05-25
Choosing System>Administration>Display on hardware that was present during install seems to work well for setting or resetting screen resolution. However changing to a different monitor is troublesome when it comes to setting screen resoulution. 

This is also true (even more so) of systems using ATI drivers. Monitors are not correctly detected and selecting "detect monitors" does nothing.

The systems I have do not show resolution settings in the xorg.conf file. they usually have an "as detected" reference.

This problem has existed for years yet it seems the solution has to be straightforward since these systems install and run just fine before any hardware is changed. Why cant the same code that detects hardware and sets config files be used to redetect and reset the config files?

If that is not straightforward then would some little tool be made to  directly allow updating the "as detected files"??? 

Please dont take offence here I'm just frustrted with having such basic problems.....

---

