---
title: "[SOLVED] Replaced motherboard is causing slowdowns in accelerated graphics"
date: 2008-03-10
forum: Hardware &amp; Laptops
---

### Post by CSMatt on 2008-03-10
I sent my laptop in to the OEM to get fixed.  While at the OEM apparently the motherboard stopped working for them so they replaced it with an identical one.  Windows had to reinstall all of the drivers automatically before it would work with the new motherboard, but Ubuntu seemed to be doing fine.  However the accelerated graphics on my ATI card are now slowing down to a crawl.  The LiveCD plays graphics at full speed, so it's not a hardware issue but apparently Ubuntu's existing drivers not working with the replacement.  I tried installing and uninstalling fglrx to see if that would fix it but that didn't work.  I really don't want to reinstall my system from scratch, so is there any other way that I can get Ubuntu to try and re-detect my hardware and reinstall the appropriate drivers without a full format?

---

### Post by Rocket2DMn on 2008-03-10
Have you tried reconfiguring X the old fashioned way?
```
sudo dpkg-reconfigure xserver-xorg -phigh
```
That should reset do the default install xorg.conf.  Then you can reinstall fgrlx as you did before.

---

### Post by CSMatt on 2008-03-11
That did it.  The new xorg.conf reveals that my video card has changed.  Further diagnostics revealed that the replacement motherboard is from the wrong model.  Apparently the new card doesn't have as much memory as the old one did and can't handle the Virtual resolution set in xorg.conf and accelerated graphics at the same time.  I'll be sure to contact the OEM about this mix up, but for now commenting out the Virtual subsection has restored full acceleration.  Thank you.

---

