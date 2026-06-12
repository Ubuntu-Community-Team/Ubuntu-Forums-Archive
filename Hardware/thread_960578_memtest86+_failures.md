---
title: "memtest86+ failures"
date: 2008-10-27
forum: Hardware
---

### Post by nathan_l on 2008-10-27
So I installed ubuntu and all was going great until it froze on a boot when I was playing with my xorg.conf.  I figured I just screwed up the X settings so I rebooted to the recovery mode but I got a kernel panic.  I rebooted and tried again, another kernel panic in a different spot.  Kept getting panics at different areas.  So I tried the memtest, failure.  I took out one stick of ram, the remaining stick failed at 000000004b0, I thought that must be the culprit, so I took it out, put the other stick back in, also failed at 000000004b0.  I thought maybe it was the slot the ram was in, so I tried both sticks in the other slot, both fail at the same address.

Anyone had any experience with this?  I'm assuming it's a problem with the motherboard?  Anyone care to verify that?

Thanks,
Nathan

---

### Post by jespdj on 2008-10-27
It could be a problem with the motherboard.

Check the speed and voltage settings of the RAM in the BIOS settings. Are you sure the speed and voltage is set to values that your RAM can handle?

---

