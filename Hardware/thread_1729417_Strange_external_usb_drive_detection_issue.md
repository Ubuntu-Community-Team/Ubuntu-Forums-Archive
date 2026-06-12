---
title: "Strange external usb drive detection issue"
date: 2011-04-14
forum: Hardware
---

### Post by dcymbal on 2011-04-14
Ubuntu 10.10
Kernel 2.6.35-28-generic #49-Ubuntu SMP Tue Mar 1 14:39:03 UTC 2011 x86_64 GNU/Linux

I have two older Maxtor IDE drives (93071U6 and D740X-6L) that I connect as external drives via an ULTRA USB 2.0 to IDE/SATA kit.  Both drives are jumpered as cable select.

I am noticing that these drives are only detected once and after that I need to restart Ubuntu (do not need to cycle the machine) to detect them again.

For example:  (1) Boot system.  (2) login (3) attach one of the above drives - it is auto detected and mounted (4) eject drive / detach.  (5) Reattach either of the above drives - it is not detected - dmesg shows nothing (I can attach other drives and they will be detected).  System stays in this state until I restart Ubuntu and then I have a one-time only detect again.  

As I mentioned, I swap a lot of drives in/out in this manner with no problems, it is just these two.

Anything I can look at to resolve or at least workaround having to restart the os?

---

