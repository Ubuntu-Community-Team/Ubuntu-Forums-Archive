---
title: "Is there a way to force driver activation from the command line?"
date: 2010-03-12
forum: Hardware
---

### Post by Kir_B on 2010-03-12
[SIZE=1]Does anyone know a way to force a driver activation, or driver install from the command line in recovery mode?

Even better, is there a way to force a driver installation from the "(initramfs)" prompt?

Thanks everyone. Kirby  [-o<



[/SIZE]

---

### Post by IcarusR on 2010-03-12
modprobe -f or insmod -f will force load a module from terminal. See man pages.
Don't know if modprobe is available from recovery console though. Would have to try it.

---

### Post by Kir_B on 2010-03-12
[SIZE=1]Thanks for the tip IcarusR[/SIZE][SIZE=1]. We'll be reading up on your suggestions, if and when our current attempt fails. Judging by our luck to this point, there's a pretty good chance.  ](*,)

Thanks again. Kirby  #-o
[/SIZE]

---

