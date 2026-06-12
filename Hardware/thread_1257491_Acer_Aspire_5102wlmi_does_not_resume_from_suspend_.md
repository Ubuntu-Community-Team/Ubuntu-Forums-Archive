---
title: "Acer Aspire 5102wlmi does not resume from suspend to ram"
date: 2009-09-03
forum: Hardware
---

### Post by peteyblueeyes on 2009-09-03
I'm running Ubuntu 9.04 amd64 on my Acer Aspire 5102wlmi. It suspends to disk and resumes just fine. It also suspends to ram and enters a low power state (when I click on the suspend button in the gnome panel), but when it resumes, the system doesn't respond. The caps lock key does not change the state of the caps lock LED, but the hard drive spins and its light turns on. As far as I can tell from logs, the kernel never starts back up at all.

It does not seem to be a hardware issue because Windows has no problem suspending and resuming.

I'm new to this, so please ask if I've failed to include relevant information.

---

### Post by t4thfavor on 2010-01-21
I know it's sort of an old thread, but I have the same issue with Acer Aspire 5100, I have 4GB of ram so it takes longer to suspend to disk/resume than a cold boot does. 

I believe there are some open launchpad tickets about this, but nothing much has been discovered as to why the suspend to ram is broken.

This is a very important feature that I have only gotten to work on a few models of laptop with Intel CPU/Intel Graphics, any other combination appears to be flawed at best.

---

### Post by imota on 2010-09-13
Same problem here on an Acer Aspire 5553G... 10.04 64bit

Laptop will go into suspend but never comes back to life. Need a hard reboot.

---

