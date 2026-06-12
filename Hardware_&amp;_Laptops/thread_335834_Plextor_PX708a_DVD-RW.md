---
title: "Plextor PX708a DVD-RW"
date: 2007-01-10
forum: Hardware &amp; Laptops
---

### Post by xjas05 on 2007-01-10
hey.. i started using ubuntu yesterday, and liked it enough to replace mandrake with it... only problem is, i can't burn CD's/DVD's i have a Plextor PX708-A.. i guess it didn't load a driver? i have no idea where to go from here... :-k

---

### Post by xjas05 on 2007-01-11
anyone?... i really need a burner..](*,)

---

### Post by RandomJoe on 2007-01-11
What happens when you put a blank disk in?  Absolutely nothing?  How about when putting in a regular data disk?

I have a Plextor PX-712A, which worked just fine out of the box.  It does have a very annoying behavior of "forgetting" about the disk after a minute or two if I don't immediately start doing something with it.  As long as I'm reading/writing to the disk, it'll be fine but if I put the disk in and let it sit a minute before trying to access it the drive acts like nothing is there!  Opening/closing the tray gets it working again.

Other than that, the modules that should be loaded are 'cdrom', 'sr_mod' and 'ide_cd'.  (At least, those are the CD-related modules loaded on mine.)  They should load automatically, if not try running 'dmesg' and make sure the kernel saw the drive when it booted.

---

