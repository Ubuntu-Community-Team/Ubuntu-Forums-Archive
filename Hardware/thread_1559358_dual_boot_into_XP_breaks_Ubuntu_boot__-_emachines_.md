---
title: "dual boot into XP breaks Ubuntu boot  - emachines 250-1915"
date: 2010-08-23
forum: Hardware
---

### Post by braindead0 on 2010-08-23
I've installed Ubuntu on a separate partition with XP on another, everything works fine until I boot into Windows XP SP3.    

After a boot into XP, when I select Ubuntu from the Grub menu I get a screen with Ubuntu 10.0.0.4 (I think that's the correct numbers) and it hangs there.  

I can boot in recovery mode, re 'install' grub (from the recovery menu) and it works fine again.  I had first tried the netbook version, with the same results.  

The netbook is an emachines 250-1915, all hardware is functioning fine under Ubuntu.  I tried searching, but this is a tough one to find decent keywords for..at least for me.  

This is a fresh installation from last week, Ubuntu fully updated.

tia.

---

### Post by braindead0 on 2010-08-25
More details that maybe will help.

When I select a normal boot I get Ubuntu 10.04 ..... on the screen.  During a normal boot the screen mode changes and the text gets smaller, the period turn red and it boots.

In the case where it doesn't boot, the larger Ubuntu 10.04 ..... stays on the screen and nothing.

I also just noticed that if I go into the system bios settings and save (making no changes, perhaps just going in caused the problem)...  

Every time if I reinstall Grub from the recovery boot option it works fine.

---

### Post by braindead0 on 2010-09-03
It appears to be perhaps  BIOS problem.  It only happens if I do a warm boot, cold boots everything works fine... now that I know that it's easy enough to work around.

---

