---
title: "Problem installing with RAID"
date: 2008-12-06
forum: Installation &amp; Upgrades
---

### Post by aehirst on 2008-12-06
Im trying to install 8.10 on my pc with 2 500GB drives in RAID 0 using my Asus P5K-E.

When try to sort out my partitions the installer only sees 2 blank 500 GB drives.

Could anyone offer any help?

Thanks an advance

---

### Post by aehirst on 2008-12-07
Bump before I buy a seperate drive :)

---

### Post by RansomStark on 2008-12-07
Linux doesn't recognise the BIOS RAID that most desktop motherboards have, as it's not true RAID, its what is called FAKERAID. Basically, remove the RAID setup from the BIOS, and then use software RAID from within Linux when setting up your partitions.

---

### Post by aehirst on 2008-12-07
I think I might be easier just to use 2 drives. I already have 2 partitions 1 windows, 1 data with about 300GB on it. Is there an easy way to transfer this to one drive?

Thanks

---

### Post by rknoesel on 2008-12-08
Have you tried the Alternate installation CD?  It detected the RAID0 in my older ICH8R ok.  Supposedly the Alternate CD has some automatic FakeRAID support built in.

---

