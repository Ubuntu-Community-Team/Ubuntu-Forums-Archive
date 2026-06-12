---
title: "acer aspire 9400 - ata1 timeout"
date: 2006-10-04
forum: Hardware &amp; Laptops
---

### Post by lambelly on 2006-10-04
I own an acer aspire 9400 which uses the intel 915pm chipset. I would very much like to run ubuntu on this. To that end I installed the most recent version on a partition on the hard drive. However, I have severe stability issues associated with the following message in the message log:

Oct  4 17:42:17 tom-laptop kernel: [17179857.560000] ata1 is slow to respond, please be patient
Oct  4 17:42:46 tom-laptop kernel: [17179883.700000] ata1: status=0x50 { DriveReady SeekComplete }
Oct  4 17:42:46 tom-laptop kernel: [17179884.104000] sda: Current: sense key: No Sense
Oct  4 17:42:46 tom-laptop kernel: [17179884.104000]     Additional sense: No additional sense information
Oct  4 17:42:46 tom-laptop kernel: [17179886.472000] psmouse.c: TouchPad at isa0060/serio4/input0 lost synchronization, throwing 3 bytes away.
Oct  4 17:42:46 tom-laptop kernel: [17179886.472000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
Oct  4 17:42:46 tom-laptop last message repeated 2 times
Oct  4 17:42:46 tom-laptop kernel: [17179886.472000] sr: Current [descriptor]: sense key: Aborted Command
Oct  4 17:42:46 tom-laptop kernel: [17179886.472000]     Additional sense: Scsi parity error
Oct  4 17:42:46 tom-laptop kernel: [17179886.488000] psmouse.c: TouchPad at isa0060/serio4/input0 - driver resynched.

If I continue running eventually I get into a position where ata1 is timing out entirely and the system freezes. I was able to do the system upgrades although it took a couple of tries. I have tried running memtest86 and got no errors. Is there anything else I can check? Does anyone have any idea what could cause this? It seems linux specific, windows seems to run fine.

---

### Post by lambelly on 2006-10-07
This seems related to a bug in the kernel that perhaps relates to scsi modules. Does anyone have any idea which kernels this bug exists in?

---

