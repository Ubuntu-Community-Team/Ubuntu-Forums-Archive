---
title: "Dell Perc/5i RAID1, utility shows mirrored pair, when booting says no boot device"
date: 2016-11-01
forum: Hardware
---

### Post by therealchriscurtis on 2016-11-01
Hello All.  I have some services running on a Dell PowerEdge-2950 with a Perc 5/I controller.  When I built this system I setup the two 150GB drives for RAID1 (mirrored) and created the array.  I then installed Ubuntu Linux 12.04.4 and it ran for years without a flaw.  While recently checking the unit I realized drive 1 (second drive) had failed.  I replaced it, verifying the drive 0 would boot by itself before doing so.  Booting back into the Perc software, and adding the new drive, it shows a clean mirrored array.  On boot up I get a no boot device.  If I remove the "new" or replaced drive, it boots again.  

Its my understanding I replaced the drive correctly, initialized it by adding it to the existing array, and then remirrored correctly.  Then way no boot device?  Thankful for any guidance given!

Chris Curtis

---

