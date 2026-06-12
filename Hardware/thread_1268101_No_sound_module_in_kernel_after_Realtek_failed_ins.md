---
title: "No sound module in kernel after Realtek failed install"
date: 2009-09-16
forum: Hardware
---

### Post by VanEyler on 2009-09-16
I had the sound working on my MS-1715B when I was running Ubuntu 7.10, but after upgrading to 8.10 it no longer worked.  I was able to open the sound configuration stuff in the GUI, but no sound would play.

MSI apparently doesn't recognize anything except WinXP as an OS, so I went on Realtek's website and downloaded their drivers and tried to install them, but that has only caused the problems to get worse.  The kernel sound modules are no longer present on my system:

$ sudo alsaconf 
modinfo: could not open /lib/modules/2.6.27-7-generic/kernel/sound/core/snd.ko: No such file or directory
modinfo: could not open /lib/modules/2.6.27-7-generic/kernel/sound/core/snd.ko: No such file or directory
modinfo: could not open /lib/modules/2.6.27-7-generic/kernel/sound/core/snd.ko: No such file or directory

Where/how can I re-install these modules in an attempt to eventually get sound working?

---

