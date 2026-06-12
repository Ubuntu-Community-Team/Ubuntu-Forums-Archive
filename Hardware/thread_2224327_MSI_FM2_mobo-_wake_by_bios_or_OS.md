---
title: "MSI FM2 mobo- wake by bios or OS"
date: 2014-05-15
forum: Hardware
---

### Post by Frederico_Zenozzog on 2014-05-15
I am trying to set an MSI motherboard up for auto shut down and wake. The wikis tell me the CMOS setting ought to be wake by bios, in which case I am able to turn RTC wake up on. Unfortunately under these circumstances Ubuntu fails to write the system clock to the hardware clock, on shutdown.

If I set it wake by OS, the system clock to hardware clock write succeeds. Ubuntu (mythbuntu) also seems to suggest that the set wakeup.sh $time write is also successful.

However, the system never wakes. So, what should the cmos/ bios setting be to have Ubuntu manage the hardware clock and alarm? Bios or OS?

PS: the board is fm2-a85xa-g65

Thanks

---

