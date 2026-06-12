---
title: "Dell Inspiron w/ Dell 1470 Wireless Still Causing Lots of Troubles"
date: 2010-05-04
forum: Hardware
---

### Post by spudgunner on 2010-05-04
So I've started a thread a couple of years ago about this here:

[http://ubuntuforums.org/showthread.php?t=740632](http://ubuntuforums.org/showthread.php?t=740632)

But I'll rehash the original problem/solution:

Wireless card didn't work and I ended up having to blacklist modules b43, rfkill_input, mac80211, as well as ensure that ndiswrapper started before b44. This still works in Ubuntu 10.04

However, a new problem has cropped up. Turns out stuff in the Dell must be super interconnected 'cause I can't get the USB ports to work while the wireless is working. I was playing around with modules and the blacklist last night and found that I only really need to blacklist b43 to get the wireless to work, but the USB won't work. (When wireless isn't working, USB does, it's weird).

So... any suggestions?

---

### Post by tgalati4 on 2010-05-04
dmesg | more

Look for hardware errors or any strange entries.  It could be an I/O chip failure.  There's no reason that wireless and USB should clobber each other.  Check your interrupts:

cat /proc/interrupts

---

