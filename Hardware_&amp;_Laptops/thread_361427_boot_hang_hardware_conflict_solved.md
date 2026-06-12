---
title: "boot hang hardware conflict solved"
date: 2007-02-14
forum: Hardware &amp; Laptops
---

### Post by mgmiller on 2007-02-14
Since this is the second time this has happened to me, I thought I would create an informational post.

This first happened to me running Dapper last year, but just happened again with Edgy.  As it turns out, it is not an Ubuntu or even a Linux problem, but is hardware specific.

First; my relevant specs:
ASUS A8V deluxe mobo
AMD 64 3200+
512 x 4 = 2 gig Mushkin ram
SATA HD (only 1 drive, not using raid)
Geforce 6800 and Geforce 7600GT (AGP)
PCI USB 2.0/firewire card
Samsung PATA DVD burner
ASUS PATA DVD rom

The Geforce 6800 was used in Dapper and the 7600GT is being used in Edgy.

In both cases, after installing the video cards and rebooting, I experienced either a normal boot to my desktop or noticed some slight delays in POST and or starting Ubuntu.

After another few reboots, however, the system hangs at the beginning of the graphical boot loading process.  I also noticed an increased time spent in POST. ](*,)

Trying recovery mode kernel does not help.
trying earlier kernel does not help.

Disconneting the SATA HDD and disabling the motherboeard SATA controller, thus taking the HDD out of the system entirely and trying to boot from a live CD, either Ubuntu or Kororaa, still hangs at the  same spot.

Going to command line mode with the SATA HDD on or off shows the system hanging at the "Begin: Starting Up RAIDS" line.   It will not progress beyond this point.

RAM tests good.  All dust cleaned from system, contacts for RAM and video card cleaned, has no effect.

What I discovered was the PCI USB 2.0/firewire controller card was creating a conflict.  Just powering the system off and unplugging it did not help.  The card must be physically removed from the system for a minute or so and then reinstalled.  This forces its bus mastering to reinitialize and the problem is resolved.   \\:D/
(Until the next time I put in a new video card)

The second time this happened to me, I also moved the card to a new slot.

The fact that the system hangs while beginning the RAID startup is not useful information, RAID had nothing to do with it.  It was all DMA/IRQ conflicts on the MOBO, even though it was set to automatic for this function and the card supposedly supports this function.

If you are having similar problems, try removing ALL PCI cards and adding them back in 1 at a time to resolve the conflicts.  I have used this same technique on balky Win XP systems.

Hope someone finds this info useful.

---

### Post by ebichuhamster on 2007-03-01
thx a lot man,, for some reason my network adapter was disabled on the boot options, so i think the computer didn't recognize it, and that's why it hanged

woot woot!!

---

