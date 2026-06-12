---
title: "mdadm software RAID 5 failed after power loss"
date: 2018-10-26
forum: Hardware
---

### Post by BatteryKing on 2018-10-26
While getting all of my hens in a row before upgrading from 16.04 to 18.04, I decided to tidy up some cables and lightly bumped the power cord and the machine hard downed.  As this whole setup has been moved around, this is not the original power cord and apparently it was not as snug of a fit as one would like, so a dug around, found one that made a more snug fit, and powered back up.  The problem is I had a software RAID 5 disk array for backup on and mounted at the time of power loss and cannot get it to mount now.  mdadm is complaining that two of the drives are missing their superblock and so cannot rejoin the array.  A RAID 5 with two drives popped out is no bueno.  I ran smartctl -a on the drives and they are in perfect health.  So no hardware fault, but something went way wrong software wise as an unmountable disk array is a lost disk array. In contrast the hardware based arrays on this same system (Avago MegaRAID 9361 with supecap and flash backup for just this scenario) is perfectly fine.  Fortunately the hardware array is my primary system and so I seem to be out of the backups I made before trying to upgrade meaning I am still on 16.04 as I am not upgrading without the latest backup on hand and ready to go.

I have gone through various threads and so far I have come across a number of answers that go nowhere, threads where nobody answered the question to what seemed to be the same problem I have, and options that sounded like they could permanently wipe / scramble the array, which I don't want to do if there is a way to recover.  The array was configured with the md array info the first thing on the disk, not in a partition.  Not sure if this is where things go wrong or if there is no solution to this problem. It seems a really big problem though.

For more detail on my setup, I have this computer on commercial grade pure sine inveter based UPS with an expansion battery box.  I have the UPS monitoring daemon setup and tested.  Also as this is a liquid cooled system running 7x24, I have an Aquaro 6 monitoring the coolant system health and its relay setup to cut power when operational parameters exceed specification by cutting pin 16 on the ATX connector.  So I have done what I can to avoid hard down situations, but such things cannot be completely eliminated.

---

### Post by BatteryKing on 2018-11-04
I have talked to various people since this post and what I have come across is it is not uncommon to lose a software RAID 5 array on Linux based systems and this includes NAS boxes that are Linux underneath.  The problem with a number of these cases are people are not checking the SMART data like I do, so when they lose an array, it is hard to say why, but the possibility is there this problem with mdadm software arrays has bitten many people.  In other words using software RAID 5 with mdadm SHOULD BE CONSIDERED FAR MORE DANGEROUS THAN A SINGLE, NON REDUNDANT DRIVE.  For this reason I am abandoning Linux software arrays entirely.  (My first attempt at software RAID 5 under Linux was back in 2000 and went badly for several reasons, pushing me to a hardware solution, which I have stuck to since, at least for my primary storage.)  I bought a SAS expander to go with my MegaRAID 9361-8i controller and moved my arrays over to it.  Conveniently the controller auto-detected the moving of drives connectivity wise and compensated, representing the arrays to the system exactly as before.  I just needed to change my monitoring routines around for the new physical addresses used inside of the controller and all is well so far.

---

### Post by slickymaster on 2018-11-04
*Thread moved to **Hardware**.*

---

