---
title: "upgrading to hardy - now no cd drive"
date: 2008-04-28
forum: Hardware
---

### Post by LCollins on 2008-04-28
I just upgraded to 8.04 using the alternate CD for the i386 system. I run a dual boot Windows XP and (now) ubuntu 8.04 system. Upon upgrade, the cd drive no longer works in both ubuntu and windows. Hardy itself has a lot of trouble running programs (they become unresponsive about 50% of the time) - thought this may give some clues.

Any ideas? Thankyou in advance.

---

### Post by justotech on 2008-04-28
> **LCollins said:**
> I just upgraded to 8.04 using the alternate CD for the i386 system. I run a dual boot Windows XP and (now) ubuntu 8.04 system. Upon upgrade, the cd drive no longer works in both ubuntu and windows. Hardy itself has a lot of trouble running programs (they become unresponsive about 50% of the time) - thought this may give some clues.

Any ideas? Thankyou in advance.

Based on the fact that it's not working with either OS I'd say it's going to be an actual hardware problem.  If you're running a desktop I'd crack it up open and disconnect the CD drive's power and IDE or SATA connector for a minute.  Be sure you pull the power from the back of the machine before hand.  It might have just died.

Check your BIOS also to see if the motherboard can even detect it plugged in.

---

### Post by thure on 2008-04-28
> **LCollins said:**
> I just upgraded to 8.04 using the alternate CD for the i386 system. I run a dual boot Windows XP and (now) ubuntu 8.04 system. Upon upgrade, the cd drive no longer works in both ubuntu and windows. Hardy itself has a lot of trouble running programs (they become unresponsive about 50% of the time) - thought this may give some clues.

Any ideas? Thankyou in advance.

I have the same problem; after having installed Ubuntu -- my CD drive is not detected in neither Ubuntu or WinXP. The funny thing is, that it is detected in bootup drives-list and it is also possible to boot up on a CD. It just seems like, at a point after GRUB, the CD drive cannot be detected. weird!

I have also described it in
[http://ubuntuforums.org/showthread.php?t=768239](http://ubuntuforums.org/showthread.php?t=768239)


BTW: I really don't think it is a hardware problem, since the drive worked before installation of Ubuntu and during installation, and it is even detected at bootup.

Please help.

EDIT: The CD drive it detected when booting on the Ubuntu LIVE CD! - Which makes it even weirder. Is it a Grub thing?

---

