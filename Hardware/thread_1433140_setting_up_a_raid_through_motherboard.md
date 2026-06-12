---
title: "setting up a raid through motherboard"
date: 2010-03-18
forum: Hardware
---

### Post by medphys on 2010-03-18
Hi all,

While reading and looking at my bios, I can set up a sata raid (1-5) with my bios.  Has anyone done this with Linux.  I am running Ubuntu 9.10 and my motherboard is a MSI P55-GD80 1156 I7 motherboard.

Will this be safer than using mdadim software or will I need to do a combination of the two.  I am just learning and reading about raid and I thought it would be an easier way to go.  I have two 1 Terabye SATA drives and am planning to set up a raid 1.

Thanks in advance

---

### Post by jrssystemsnet on 2010-03-18
> **medphys said:**
> Hi all,

While reading and looking at my bios, I can set up a sata raid (1-5) with my bios.  Has anyone done this with Linux.  I am running Ubuntu 9.10 and my motherboard is a MSI P55-GD80 1156 I7 motherboard.

Will this be safer than using mdadim software or will I need to do a combination of the two.  I am just learning and reading about raid and I thought it would be an easier way to go.  I have two 1 Terabye SATA drives and am planning to set up a raid 1.

Thanks in advanceMy recommendation is DON'T use the fakeraid on your motherboard - it still uses the CPU for the work, you don't actually get any benefit out of it, and it exposes you to a lot more potential for nastiness down the road.

Just use mdraid.  It'll perform far better than the motherboard fakeraid, and if your motherboard croaks in a year you won't have to find another motherboard with the exact same chipset of fakeraid and pray to $deity that it detects everything OK; you can just slap the drives into whatever hardware you like and it will Just Work.

---

