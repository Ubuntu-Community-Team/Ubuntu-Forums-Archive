---
title: "Fasttrak s150 TX4 And raid 1 not working."
date: 2009-01-29
forum: Hardware
---

### Post by Fredrik_b on 2009-01-29
Anyone familiar with Fasttrak s150 TX4?

I am trying to use this to run Ubuntu on 2x2,5" sata hardisks (mirror). 

But the computer doesn't seam to understand that  have set up raid 1, because changes does not mirror itself to the second hard drive.

I have lost the manual so I am not sure I am setting up the raid correctly. This installation I first installed ubuntu to Hdd1 then created a mirror withe the raid card setup and let the raid clone the original hard drive.

It seem that only the orginal clonig presist on the second hard drive. This means that mirroring is useless for now. 

The only thing that works is that the raid card thik it is a mirror so the computter can be booted without being asked to setup a raid array or press ESC.

---

### Post by electrogeist on 2009-01-29
Because that is not a real hardware RAID controller.  It has the moniker FakeRAID in the community.  Basically its software RAID with a little assistance from the card.  You can setup linux to use it as FakeRAID using the array settings made with the card.  Or just use it as a basic controller, and standard linux software RAID using mdadm.   There should be howtos around here for both methods.

---

