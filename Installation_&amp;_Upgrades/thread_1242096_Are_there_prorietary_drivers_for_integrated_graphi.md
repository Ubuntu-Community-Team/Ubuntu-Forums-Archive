---
title: "Are there prorietary drivers for integrated graphics cards?"
date: 2009-08-16
forum: Installation &amp; Upgrades
---

### Post by shresthanator on 2009-08-16
Are there proprietary graphics card drivers for this integrated card? 
[http://www.intel.com/support/graphics/intel845g/](http://www.intel.com/support/graphics/intel845g/)
(aka Integrated Intel Extreme 3D Graphics ) 

this is for a ~4 yo Dell Dimension 2400 computer. I want to know weather or not it is even possible to enable all the fancy things with compiz like 3d desktop and whatnot, only using integrated graphics processor. 

If not Ill get like a cheap PCI card, and go from there. Thank you.

---

### Post by Rocket2DMn on 2009-08-16
I don't believe intel has restricted drivers.  You should still be able to use desktop effects with Compiz.  You can install compizconfig-settings-manager and access it from System->Preferences->CompizConfig Settings Manager to configure it.  Desktop effects are enabled from System->Preferences-?Appearance, Visual Effects tab.

You probably won't get excellent performance out of the card, but it should still work.

---

### Post by lswb on 2009-08-16
The intel drivers are open source and on the install CD. I have intel 855 graphics and compiz effects work well. However, the driver and kernel packages for intel that shipped with 9.04 have some serious problems with video playback. There are some fixes you can do to make 9.04 work, or you you can use 8.04, or wait till 9.10 is released. Personally I had too much trouble with 8.10 to recommend it but others report good results, YMMV.

---

