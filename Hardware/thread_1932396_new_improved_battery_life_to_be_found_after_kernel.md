---
title: "new improved battery life to be found after kernel/grub tweeks :)"
date: 2012-02-27
forum: Hardware
---

### Post by mr_manny on 2012-02-27
Battery life has been around 2hrs for sometime now...what can you expect from older gear?

Or that's what I thought...

Added the following entries to my grub, and was presently surprised to see it extended to 3hrs :)

   pcie_aspm=force i915.i915_enable_rc6=1 


some info at the following sites:
 
[http://foolcontrol.org/?p=1511](http://foolcontrol.org/?p=1511)
[http://www.phoronix.com/scan.php?page=article&item=linux_aspm_solution](http://www.phoronix.com/scan.php?page=article&item=linux_aspm_solution)
[http://skyshadows.net/](http://skyshadows.net/)


seems to work with kernel 2.6.38 and up...


Have been playing around with 12.04 alpha2 on my test box (dell d430) which required grub entries to be added.

manny

---

