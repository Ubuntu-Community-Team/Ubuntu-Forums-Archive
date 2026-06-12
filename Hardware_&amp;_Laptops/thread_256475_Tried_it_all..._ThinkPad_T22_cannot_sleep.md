---
title: "Tried it all... ThinkPad T22 cannot sleep"
date: 2006-09-13
forum: Hardware &amp; Laptops
---

### Post by veebis on 2006-09-13
ThinkPad T22 w/latest BIOS update + Ubuntu 6.06.1

Searched far and wide, tried everything I can find. ](*,) 

**With acpi**, *Suspend* initiates just fine, but will not wake. Hard crash, won't even restart until AC & battery are  both removed/reset.

**With apm** ("acpi=off apm=on noacpi"), *Suspend* blanks  the screen briefly, starts screensaver for a second, then "wakes up" and asks for password to re-enter. Doing so gets me back to a desktop that  crashes soon after (becomes unresponsive to clicks).

I'd REALLY like to be able to suspend this puppy. Any fresh insights would be greatly appreciated!

Thanks,
-Vb

---

### Post by Mark Stosberg on 2006-10-27
For reference, this user did solve the problem, by [upgrading to edgy]("http://ubuntuforums.org/showthread.php?t=268642"), where everything worked with no configuration.

---

