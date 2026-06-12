---
title: "Strange: No splash screen"
date: 2007-11-07
forum: Hardware &amp; Laptops
---

### Post by agger on 2007-11-07
I just installed Gutsy on a new MSI S271 laptop with and AMD Sempron 3400+ processor.

Afted the Grub screen, the screen goes dark/blank and nothing happens. Getting impatient, I press CTRL+Alt+F1 to leave the graphic mode and see whatever output there may be - i says something about "kinitd", and now the text-based boot process seems to begin, detecting and setting up all hardware etc.

And from this point, the machine boots normally into Gnome, and everything works fine (everything except hibernation which is due to a known bug in the fgrlx ATI driver which I need to play Urban Terror).

So, everything works fine except I get no splash screen and the boot process doesn't start till I press CTRL+Alt+F1.

What can this be - any ideas? I tried switching to the  "ati" graphics driver but it didn't help (and didn't allow me - my son, actually - to play Urban Terror :-)).

Note i've installed from the "normal" (32 bit) live CD even though I believe the Sempron is actually 64 bit - this shouldn't be a problem though, or what?

Thanks in advance for any help. :-)

---

### Post by adam0s on 2007-12-08
had the same problem after a little searching i found [http://geekybits.blogspot.com/2007/11/fix-for-no-splash-in-ubuntu-710.html](http://geekybits.blogspot.com/2007/11/fix-for-no-splash-in-ubuntu-710.html)
and after changing the usplash I got it working like normal

---

### Post by agger on 2007-12-08
Thanks a lot - it really worked! :-)

Only difference is I used 1280x800, which is my laptop monitor's native resolution, instead of 1024x768

---

