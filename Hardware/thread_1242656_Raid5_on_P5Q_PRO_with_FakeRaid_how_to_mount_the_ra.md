---
title: "Raid5 on P5Q PRO with FakeRaid how to mount the raid ?"
date: 2009-08-17
forum: Hardware
---

### Post by cherva on 2009-08-17
I installed and configured FakreRaid according [https://help.ubuntu.com/community/FakeRaidHowto#Live%20CD%20Installation%20(Ubiquity%20graphical%20installer)]("https://help.ubuntu.com/community/FakeRaidHowto#Live%20CD%20Installation%20(Ubiquity%20graphical%20installer)") this howto but I don't want to have windows so I skiped the Congiuring GRUB step now my RAID 5 is ok but when I try to mount it with ```
mount /dev/mapper/WHATEVER /media/WHATEVER 
``` I get wrong file type ... adding ```
-t ext3
``` doesn't help ... anyone having a clue how to mount it :confused:

---

