---
title: "GRUB: add disk-check option"
date: 2008-07-14
forum: General Help
---

### Post by flostre on 2008-07-14
Hi,

we are a robotics team and have a PC on our robot running Linux. Since we regularly take part in competitions where time matters, the automated hard-drive check can be a PITA. I already found out how you can disable it, but of course you have to perform it from time to time. I am thinking about a non-default GRUB option which always performs a hard-drive-check before booting. But I have no idea how to do this.

On another avenue, I it would be ideal if the robot would beep on boot-up how often the hard-drive has been booted without being checked. This way, one would eventually be annoyed enough to run hard-disk check and not forget it.

Best,
flostre

---

### Post by justborn on 2008-07-14
> **flostre said:**
> Hi,

we are a robotics team and have a PC on our robot running Linux. Since we regularly take part in competitions where time matters, the automated hard-drive check can be a PITA. I already found out how you can disable it, but of course you have to perform it from time to time. I am thinking about a non-default GRUB option which always performs a hard-drive-check before booting. But I have no idea how to do this.

On another avenue, I it would be ideal if the robot would beep on boot-up how often the hard-drive has been booted without being checked. This way, one would eventually be annoyed enough to run hard-disk check and not forget it.

Best,
flostre




dude,do the following
1.download "startup manager"
2.& then open startup manager
3.in the boot options tab u will find 'default operating system'




the rest i think u will undestand automatically

---

### Post by flostre on 2008-09-03
> **justborn said:**
> the rest i think u will undestand automatically

I'm afraid I don't. If you could elaborate?

---

### Post by Zorael on 2008-09-03
As for the disk-check option, perhaps one solution would be to install a minimal linux installation on a separate partition (Puppy? Damn Small Linux?), set it to automatically do filesystem checks, and then reboot.

---

