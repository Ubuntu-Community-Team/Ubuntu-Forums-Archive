---
title: "Dell D620 - signal lost?"
date: 2007-06-01
forum: Hardware &amp; Laptops
---

### Post by magicPants on 2007-06-01
Hi,

I'm helping a blind colleague of mine with running the live version of Ubuntu 7.04 on his Dell D620. When booting up we get so far on the black Ubuntu screen with the progress bar, then the screen seems to stop sending a signal and nothing more is displayed. However, the system still boots and we hear the startup music, but no display! Note: the laptop is docked into a workstation cradle and I've tried this on another Dell D620 in the office.

Has anyone else experienced this?

Many thanks

Dave

---

### Post by dwingojr on 2007-06-01
In the BIOS (F2), insure that the default video adapter is "System" not "Dock". Worked on my D820 ;-)

---

### Post by magicPants on 2007-06-04
Hi dwingojr,

I couldn't see anything in the BIOS relating to "system" or "dock", but I did notice that the dock was set to using  it's own display card rather than the PC's. So I changed this to use the PC's own.

On booting up I noticed that the screen went into power save mode (different), just after the Ubuntu logo turns into a blinking cursor (loading xWindows, I'm assuming).

Any ideas?

Cheers

Dave

---

### Post by magicPants on 2007-06-06
bump

---

### Post by magicPants on 2007-06-07
For those interested, I ended up booting up in safe graphics mode. Then the Nvidia drivers could be loaded (if needed).

I still think Ubuntu has a long way to go till these kind of issues are ironed out. It's making progress, but very slowly. There were times where I didn't know what was going on when booting as the progress bar crashed, at least with Suse you can press ESC and see what's happening!

I'd like to see more support for Braille & screen readers right from boot up (wishful thinking) along with a better, more usable, experience for access technologies. 

Dave

---

