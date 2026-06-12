---
title: "Boot Hang with 2.6.24-20-server"
date: 2008-07-25
forum: General Help
---

### Post by mrb88 on 2008-07-25
Hey all - I have a fresh install of Ubuntu 8.04 Server on an older computer with an Athlon XP 2600 processor. With the .19 kernel it started out with, I had no problems booting. When I upgraded to the .20 kernel, it hangs following the line "Checking 'hlt' instruction... OK.

I checked my log and the next line should be:

SMP alternatives: switching to UP code.

However, I never see this. It just hangs after saying OK to checking hlt instruction.


Helllp!

---

### Post by chrisccoulson on 2008-07-25
You might want to take a look at:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/251344]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/251344")
and
[http://ubuntuforums.org/showthread.php?t=868249]("http://ubuntuforums.org/showthread.php?t=868249")
:)

---

### Post by mrb88 on 2008-07-25
Oi. Hope this is fixed soon.

---

### Post by mordak13 on 2008-07-26
> **mrb88 said:**
> Oi. Hope this is fixed soon.

I have the exact same issue as mrb88
My install of Xubuntu hangs at - "Checking 'hlt' instruction... OK.
The .19 kernel boots fine. I piled on the launchpad band wagon about this bug.

---

