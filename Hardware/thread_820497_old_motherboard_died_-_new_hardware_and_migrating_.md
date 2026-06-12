---
title: "old motherboard died - new hardware and migrating LVM ?"
date: 2008-06-06
forum: Hardware
---

### Post by moodog on 2008-06-06
I think my old system has died and I'm looking at upgrading some parts. I'll probably get the following replacement parts:

ABIT AN52S motherboard
AMD BE2400 CPU
2GB RAM

I'll be reusing the existing hard drives I have - 4 (I think)

I have one of these disks (ATA) set up with mythbuntu 8.04, and the other 3 are in an lvm configuration. The old system is dead, so I'm not able to run any commands on it. I'm just wondering if the following procedure should be successful:

[LIST]      Pull apart old system[/LIST]
[LIST]       Put in new parts[/LIST]
[LIST]       Put in disk with OS on it and boot to ensure system is running fine[/LIST]
[LIST]       Put in remaining hard disks and reboot[/LIST]
[LIST]       Ensure LVM disks are detected and run vgscan/vgchange -ay to make new system recognise LVM disks[/LIST]
[LIST]       Proceed with mythtv goodness on new beefier system[/LIST]



Any problems foreseen with this approach? I'm assuming there should be no problem unplugging an OS disk from one hardware configuration and plugging booting it in a new system with different configuration?

(FYI, old system was AMD Athlon 3200)

Any help/suggestions welcome.

---

