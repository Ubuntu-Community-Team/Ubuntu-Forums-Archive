---
title: "My eth0 wifi disappered after upgrade"
date: 2006-04-04
forum: Hardware &amp; Laptops
---

### Post by nemik on 2006-04-04
Hello,

I'm on breezy and just now did a regular upgrade with update manager and it got a new kernel and kernel headers. but now my eth0 wifi card is gone. i have a dell 700m and a ipw2200 card built in. everything worked PERFECTLY before and now this happened.

I have no idea what broke it or how to fix it. botting into the recover option also did nothing, there is no eth0 when i do iwconfig.

what should I do? :(

---

### Post by florizs on 2006-04-04
what is your current kernel version?
to find that out type:
uname -r
currently i'm running a laptop with a ipw2200 card and kernel 2.6.12-10-386. it has no problems with me.
maybe you should try to select another kernel from the bootloader and boot see if it works.

---

### Post by nemik on 2006-04-04
i just booted into 2.6.12-9-386 and it worked, but was going into 2.6.12-10-386 for a while before and all was fine. just 5 minutes ago i did an update with update manager. it got a new kernel image, kernel headers and after a reset, i no longer had eth0 and still don't.

at least 2.6.12-9-386 still works though but this sucks.

---

