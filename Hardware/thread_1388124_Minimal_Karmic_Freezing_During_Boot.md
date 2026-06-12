---
title: "Minimal Karmic Freezing During Boot"
date: 2010-01-22
forum: Hardware
---

### Post by l2e on 2010-01-22
I did a fresh install of minimal karmic on a zotac 9300 mobo and about 50% of the time during reboot or cold boot it would freeze right after this message:
 
nforce2_smbus ....Error probing SMB2
 
I found many posts saying that appending GRUB_CMDLINE_LINUX="acpi_enforce_resources=lax" to grub fixes the problem.  Actually, it only suppresses the onscreen boot message but still freezes.
 
I have installed this on 3 separate mobos with nvidia 9300 chipsets and all exhibit this behaviour to some extent.  Any ideas on fixing this problem?

---

