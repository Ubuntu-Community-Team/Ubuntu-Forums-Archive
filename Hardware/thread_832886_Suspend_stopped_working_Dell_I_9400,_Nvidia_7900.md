---
title: "Suspend stopped working Dell I 9400, Nvidia 7900"
date: 2008-06-18
forum: Hardware
---

### Post by krausest on 2008-06-18
For many weeks (during beta releases and after the production release of 8.04) suspend to ram worked like a charm on my Dell Inspiron 9400 with a nvidia 7900 Go.
Some weeks ago suspend to ram stopped working. After resuming I'm getting a very defective looking screen (mostly white with a little purple, some greyish interlaced pattern running from top to bottom).

I tried almost anything I could find, but it didn't help. Has anyone some a good idea what I could try?

Here's what I already did:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/226279](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/226279)
Reverting even to kernel Kernel 2.6.24-15 doesn't help
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/226279/comments/25](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/226279/comments/25)
Adding ehci-hcd to unload_modules doesn't help
All thing noted on 
[https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend](https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend)
Reverting to NVIDIA-Linux-x86-173.08 didn't help either.


Version information:

NVidia binary driver 173.14.09

Kernel Version (from -proposed)
Linux delle 2.6.24-19-generic 

lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.04.1
Release:	8.04
Codename:	hardy

---

