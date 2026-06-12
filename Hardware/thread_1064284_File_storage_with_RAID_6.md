---
title: "File storage with RAID 6"
date: 2009-02-08
forum: Hardware
---

### Post by mn_voyageur on 2009-02-08
I have been looking at file storage.  

The easy, but expensive would be to attach an NAS to my network.

Cheaper would be to purchase an 8-bay hot-swap chassis.  Set 4 bays to run RAID 6 with a hot spare.  Extra slots would allow me to compare my back-ups and verify them.  

Every week, install a drive and back-up the files to another HDD.  Rotate 4 HDD's as back-ups.

This chassis would not contain that boot disk, so I would not have the problems with trying to boot from a RAID drive.  I also have a small solid state SATA drive that I could actually boot.  

If I am backing up weekly, and I lost my RAID controller, I would only lose the last few days of data.  So the raid controller becomes less critical.(?)   

Is this reasonable?  

Any suggestions?

mn

---

### Post by Cracauer on 2009-02-13
raid6 with a hot spare would be a minimum of 5 drives, not 4. I assume you mean a plain raid-6 with 4 drives.

Overall it's a good idea, you get a 8-drive setup, 4 of them are primary backup with capacity of x2. Then, assuming the important data is only 1/2 of the total data on the first array, you have 4 generations of older backups.

---

