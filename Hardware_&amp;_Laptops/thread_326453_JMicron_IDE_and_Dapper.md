---
title: "JMicron IDE and Dapper?"
date: 2006-12-27
forum: Hardware &amp; Laptops
---

### Post by jolt256 on 2006-12-27
I have a P965-based motherboard with the _[infamous ]("https://wiki.ubuntu.com/Core_2_Duo_Support")_ incompatible JMicron IDE controller. After a lot of trouble, I finally managed to get Dapper installed onto the machine, but of course without support for the JMicron and the DVD drive connected to it. I'd like to get this drive working.

All the guides I see suggest that the controller works in Edgy. However, my system is also set up with software RAID (linux md, not fakeraid), and supposedly upgrading from Dapper to Edgy is _[broken under this condition ]("http://www.ubuntuforums.org/showthread.php?t=286066")_.I tried downloading vanilla 2.6.19 kernel sources and running make-kpkg - the resulting kernel got the DVD drive working, but completely borked networking (iptables, notably, did not work).

Does anyone have suggestions on how to get this JMicron controller working? I'm willing to upgrade to Edgy if the RAID problems have been fixed; otherwise, a Dapper solution would be best.

Thanks!

---

### Post by jolt256 on 2006-12-27
After fighting make-kpkg for 4 hours or so, I finally have a custom kernel that has it all working.

---

