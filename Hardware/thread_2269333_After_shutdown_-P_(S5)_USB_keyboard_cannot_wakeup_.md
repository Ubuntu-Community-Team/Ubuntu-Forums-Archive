---
title: "After shutdown -P (S5) USB keyboard cannot wakeup the PC"
date: 2015-03-14
forum: Hardware
---

### Post by ako673de on 2015-03-14
I have a HTPC with yaVDR 0.5, which runs Ubuntu 12.04.5-LTS, and I want  to power it on with my Logitech K400r wireless USB keyboard/touchpad.

Unfortunately  on my hardware (motherboard GA-Z68MA-D2H-B3) this only works from S3,  but not from S4 and S5 states (even though 5VUSB power is present, and  Wake-on-Lan is working even from these states). However I didn't yet  manage to get S3 to work reliably (in 4 of 5 cases - even with all  modules unloaded when entering S3 - simply nothing happens upon resume:  no HDD activity, black screen, hard reset required), therefore I'm  stuck.

Is it really a hardware given fact that USB wakeup doesn't  work from S5? Or is it maybe just one configuration option (in the  kernel?) away?

I read that on my motherboard USB wakeup from S4  has been supported up to some (ancient) BIOS version. Maybe this version  is not too old (for my CPU and stuff). So, basically, would it be  possible to suspend to S4 but (instead of resuming) start the PC  normally? yaVDR team says that in this case there might be problems with  not cleanly unmounted disks, but are these really critical, or even  easily workaroundable?

Or how about a USB to PS/2 adapter? I made  sure, that the computer wakes up properly from any PM state if a PS/2  keyboard is connected. The PS/2 socket on the motherboard backplane even  shows both colours. But does that mean that it can accept mouse and  keyboard one at a time or at the same time? And in case of the latter:  Is the K400r ready for operation behind a USB to PS/2 adapter anyway?  Has anybody tested this setup successfully with my or a similar keyboard  type?

Any ideas welcome...
ako673de

---

