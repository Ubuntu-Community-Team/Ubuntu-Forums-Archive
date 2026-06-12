---
title: "ASRock N68C-S UCC"
date: 2012-03-16
forum: Hardware
---

### Post by jhmgbl on 2012-03-16
Hallo

Recently my old K7S5A went up in smoke. So I had to buy a new motherboard (see Title). But my old Mythbuntu 10.04 didn't boot any more. So I tried Mythbuntu 11.10 and 12.04 with the same result: The root partition can't be found (I also tried Suse, Debian and Knoppix). I assume that there is a problem with the SATA driver. I have attached two IDE-Drives to the IDE-Port and one DVD-Drive with an adapter to the SATA-Port. In Bios SATA is set to IDE. Are there any Kernel parameters I can use to make Mythbuntu using IDE Mode? Or what else are the possible options to boot with this board (XP SP3 did install without problems).

Regards Hans

---

### Post by jhmgbl on 2012-03-16
I finally could boot mythbuntu 11.10 after disabling the IDE-Port. But now I am without Harddrives. So how do I get the IDE-Ports working.... The only Error Message I get is "SATA link down (SStatus 0 SControl 300)"   > **jhmgbl said:**
> Hallo

Recently my old K7S5A went up in smoke. So I had to buy a new motherboard (see Title). But my old Mythbuntu 10.04 didn't boot any more. So I tried Mythbuntu 11.10 and 12.04 with the same result: The root partition can't be found (I also tried Suse, Debian and Knoppix). I assume that there is a problem with the SATA driver. I have attached two IDE-Drives to the IDE-Port and one DVD-Drive with an adapter to the SATA-Port. In Bios SATA is set to IDE. Are there any Kernel parameters I can use to make Mythbuntu using IDE Mode? Or what else are the possible options to boot with this board (XP SP3 did install without problems).

Regards Hans

---

### Post by jhmgbl on 2012-03-17
Solved.

One Drive wath running with UMA5 and one with UDMA6(133). After I set both to 100 it worket! With XP this workaround was not necessary.

---

