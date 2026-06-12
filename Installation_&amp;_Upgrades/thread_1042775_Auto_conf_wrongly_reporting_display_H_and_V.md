---
title: "Auto conf wrongly reporting display H and V"
date: 2009-01-17
forum: Installation &amp; Upgrades
---

### Post by kororke on 2009-01-17
I have just installed Ubuntu 8.10.
It appears that the Auto conf (Or whatever it is called)is wrongly reporting the H and V parameters of my display 
(Benq FP553) with the result of no X and a long error message ending in Screens found. None usable..
In Xorg.0.log those values are reported as
Ranges V min:48  V max: 49
H min:49 H max: 50, Which of course is ridiculous, and no wonder that the @#*&%& thing cant find any usable screens.
I have had this problem with the 7x versions but was able, with pico, to edit the Xorg.conf and this was a permanent cure.
I have in 8.10 edited the xorg.conf and added the normal Monitor section, but to no avail as that entry is ignored and the Auto configure values are used instead.
There must be a method of PERMANENTLY overwriting those incorrect values with correct ones.
Surely there could have been added a choice of manual or auto configuration.
As it stands I cannot use Ubuntu and have to once again depend on Mr Gates.

kororke

**Further thoughts**
Would it be feasible**** to uninstall/kill the application that does the Auto configuration and then add an standard xorg.conf?
If so what application is doing this crazy Auto thing?

---

