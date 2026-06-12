---
title: "Wireless led gone after upgrade to Hardy"
date: 2008-05-01
forum: Hardware
---

### Post by trzmiel on 2008-05-01
Hello,

I recently updated to Hardy. It went pretty smooth, except for that my blue wifi led is gone. It works in Windows which I dual boot, so the led itself is fine.

It's HP nx7300 with Intel PRO Wireless 3945. I tried creating /etc/modprobe.d/ipw2200.modprobe with "options ipw2200 led=1" inside, but it had no effect (I think it wasn't supposed to work, because it's not the right file for my card). I also added "options ipw3945 led=1" to /etc/modprobe.d/ipw3945 (I think this is the right file), but it didn't work either.

Any ideas? Thanks in advance.

PS. Unsuprisingly, Compiz doesn't work with Java apps (I don't think it ever did). Anyway that's beside the point.

---

### Post by pierlo on 2008-06-17
same here, please help us! 
also, i tried the backports trick mentioned somewhere on the forum, but that didn't work as expected too... any clue?

---

### Post by ukripper on 2008-06-17
Hardy uses iwl3945 driver and this driver has bug of led not working on launchpad already reported. 

this driver works better than ipw3945 but has its downfall of not displaying led.

If you need better working wireless stick to this driver otherwise use backport from gutsy for ipw

---

