---
title: "Raon Everun Note: powernow-k8 module missing in generic kernel"
date: 2009-04-28
forum: Hardware
---

### Post by Schugy on 2009-04-28
Hello guys,

the powernow-k8 code compiled into the generic kernel doesn't support my Turion X2 TL-56 1,2GHz in my Raon Digital Everun Note D60H.

powernow-k8: ignoring illegal change in lo freq table-4 to 0x0
powernow-k8: transition frequency failed

The processor never switches to 800 MHz.

In KUbuntu 8.10 I could [change the module]("http://www.schugy.de/Linux/Raon%20Everun%20Note/powernow-k8-src.zip") with this code but 9.04 Jaunty hasn't a module.

Well, the module code I've compiled for Ubuntu 8.10 only supports the conservative governor. The userspace/ondemand governor crashed the system almost immediately.

This bug costs quite a lot of the possible mobility.

I hope someone will take that buggy powernow-k8-code out of the kernel image and will put it into the linux-modules again.

---

### Post by Neotelos on 2009-04-30
Hey Schugy! :)

I took code from the working powernow-k8 and fixed the issues in the one one (as far as working on the Everun note) and compiled it all in a new kernel.

See my wiki page for the downloads, etc.
[http://kumquatpc.com/wiki/index.php/Everun_Note](http://kumquatpc.com/wiki/index.php/Everun_Note)

*The packages are only designed for the Everun note hardware.

ALSO, the module isn't missing in 9.04, it's just built into the kernel.

---

### Post by Schugy on 2009-05-01
Wonder whether we can get ondemand/userspace governor working.

[Bug at launchpad.net]("https://bugs.launchpad.net/bugs/355232")

---

