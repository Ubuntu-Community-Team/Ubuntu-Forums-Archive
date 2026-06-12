---
title: "Failure to boot due to CD-ROM drive or IDE controller"
date: 2010-08-21
forum: Hardware
---

### Post by Azazel on 2010-08-21
I cannot boot into ANY version of Linux (some live-cd's don't even work) if my CD-ROM drive is plugged in. Windows boots just fine. I replaced the IDE cable with a brand new one, no help.

In ubuntu, boot hangs just after GRUB with a black screen and blinking cursor, completely unresponsive. I can boot into recovery mode and make it up to TTY-6. At TTY-7 it hangs at "setting sensors limits"

Everything worked fine before I upgraded my motherboard to a BioStar TA870+ (also upgraded to 64-bit edition)

Any ideas? I would like to be able to use my CD drive

---

### Post by jhoyland on 2011-08-22
I have exactly the same problem. Ubuntu 11.04 boots fine if I unplug my LG CD ROM drive. Otherwise it freezes during bootup.

James

---

### Post by dandnsmith on 2011-08-22
I get a hint of an old problem - USB device, with insufficient power at boot to support the hardware plugged in.
If this is what the problem is, then using a powered USB hub is the way to go.

---

