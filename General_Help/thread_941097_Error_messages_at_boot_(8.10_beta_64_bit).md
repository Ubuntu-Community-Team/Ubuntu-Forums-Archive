---
title: "Error messages at boot (8.10 beta 64 bit)"
date: 2008-10-07
forum: General Help
---

### Post by Athanasius on 2008-10-07
I have an Asus P5n-E SLI motherboard with the Nvidia nForce 650i chipset.  8.10 beta 64 bit is installed and when I boot up there is an annoying beep and the following error message is shown:
```
[1.800900]  uvesafb:  failed to execute /sbin/v86d
[1.800952]  uvesafb:  make sure that the v86d helper is installed and executable
[1.801003]  uvesafb:  Getting VBE info block failed (eax=0x4f00, err=-2)
[1.801053]  uvesafb:  vbe_init() failed with -22
[2.924017]  hub 1-0:1.0: unable to enumerate USB device on port 2

```
After about 10 seconds the annoying beeping stops and I am in ubuntu.

Is this something that others see?  Perhaps there is something that I did not configure in the BIOS?

---

### Post by Athanasius on 2008-10-07
ah, they are bugs on launchpad... should have looked there first.  I hope it is fixed by release.

---

### Post by ^[H3ad-Tr1p]^ on 2008-11-01
hi

I have the same problem on my laptop

what had you done to fix the problem?

thanks

---

### Post by ^[H3ad-Tr1p]^ on 2008-11-01
hi

I have the same problem on my laptop

what had you done to fix the problem?

thanks

---

