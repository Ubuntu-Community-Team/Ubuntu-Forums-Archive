---
title: "ubuntu 11.04 resume freezes X"
date: 2011-08-26
forum: Hardware
---

### Post by tjh_ltsp on 2011-08-26
I just installed ubuntu 11.04 and downloaded all updates.

pm-suspend suspends without problems. Resume however leads to a frozen X11 login screen. ALT-F2 Terminal still works.
dmesg reports: *ERROR* invalid frame buffer id. I use the radeon module. Hardware is X800GTO.

One "solution" to the problem is using the boot parameter radeon.modeset=0. Unfortunately however than the new UBUNTU one desktop does no more work.:cry: Can you provide a better solution to the suspend&resume problem?

Maybe I have to recompile the kernel , with radeon as kernel part? Please advice.

---

