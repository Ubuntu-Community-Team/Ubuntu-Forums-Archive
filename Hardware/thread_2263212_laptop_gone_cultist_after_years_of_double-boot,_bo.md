---
title: "laptop gone cultist: after years of double-boot, boots only windows, no linux anymore"
date: 2015-01-30
forum: Hardware
---

### Post by emk on 2015-01-30
I have two laptops, more or less identical. Screen resolution for the display differs (one WXGA, the other WUXGA), that should be about it in terms of differences. 

Dell Latitude D830, 4 GB RAM, Intel SSD, dual-boot systems with Windows 7. Both of them have the latest Ubuntu Vivid Vervet installed.

One and *only one of them* doesn't boot Linux all of a sudden. The boot sequence stops. If I dual-boot, Windows boots without a problem.
Hardware testing (memtest, manufacturer partition with diag tools) doesn't show anything unusual. All the tests give an OK result. Windows shows no errors.

**I tried with four different distributions, none of them will boot, neither from HD, nor from CD or USB. **Ubuntu 12.04LTS, 14.04LTS, 13.10, 15.04, and Parted Magic, a rescue Linux distribution with a completely different system (the latest from Jan 15) all hang at boot. Booting into rescue doesn't make a difference. The system hangs and shows something like 'detected keyboard' before it hangs. Parted Magic shows a 'Searching for devices...', this is about the only indicator I have.

The other laptop continues to run Linux fine, there's no problem at all with it (as it should).
I have a theory, but don't want to present it so I get unbiased ideas. What could the problem be? And what could I do to locate the problem / remedy it?

---

### Post by weatherman2 on 2015-01-30
Anything plugged into one of the laptop's USB ports?  If so, remove it and try again.

If not - try physically removing the hard drive if you can and try again.

---

### Post by tgalati4 on 2015-01-30
Did you update the BIOS recently?  It sounds like a Secure Boot issue.  Perhaps a recent Windows Update changed a setting that enforces Secure Boot.  If that is the case, then your computer is working correctly.

---

### Post by emk on 2015-01-30
> **tgalati4 said:**
> Did you update the BIOS recently?  It sounds like a Secure Boot issue.  Perhaps a recent Windows Update changed a setting that enforces Secure Boot.  If that is the case, then your computer is working correctly.

Computer is from pre-UEFI times, from 2007. No secure boot on this one. No recent BIOS updates, either.

---

### Post by emk on 2015-01-30
> **weatherman2 said:**
> Anything plugged into one of the laptop's USB ports?  If so, remove it and try again.

If not - try physically removing the hard drive if you can and try again.

Removed everything attached and also disabled the internal WWAN card which has an USB connection. No change.

Pulled out hard drive, tried to boot from CD and USB - no change.

Retried Windows from disk - machine boots, all is well. wtf...

---

### Post by weatherman2 on 2015-01-30
I'd also try removing the CD/DVD drive if there is one.

Next I would try resetting the BIOS to default settings.  I'd even try clearing CMOS settings by removing the CMOS (RTC) battery, but sometimes, depending on the laptop design, the CMOS battery is hard to access so may not be worth the hassle.  Sometimes you can get to that battery easily.  Once you do that, you'll have to reset the clock; if you don't have to, you didn't do it right or didn't leave the battery out long enough (also unplug power, unplug the main battery).

Speaking of the clock: are you sure the clock didn't get set back or way forward in time?

If none of this works, you may simply have a hardware problem, maybe something on the motherboard has failed, but Windows doesn't check as stringently as Linux does when booting up.  In Windows, if you can boot up a working install (not the live disk), you could look in Device Manager and see if any devices now have a yellow (?) or (!) next to them, when they don't on the other laptop.  You might also find errors in Event Viewer that could give you hints about hardware issues that aren't fatal in Windows.

---

### Post by emk on 2015-01-31
> **weatherman2 said:**
> I'd also try removing the CD/DVD drive if there is one.
We have a winner. It was the optical drive. As soon as it got removed, Linux booted without so much as an entry in dmesg log. I reinserted it, and the problem is gone.

I didn't think of removing the optical drive first because it was functioning - I booted from it, it played and everything. Still, after removal and reinsertion, the problem is gone. One experience more, I guess.

Thanks for all the other suggestions, even if they didn't need to be applied. One of the best posts for me in terms of what to look for, especially for mentioning the event viewer. My knowledge of Windows is limited, and I wouldn't have known where to look.

---

