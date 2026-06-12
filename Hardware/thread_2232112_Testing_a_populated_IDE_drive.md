---
title: "Testing a populated IDE drive"
date: 2014-06-29
forum: Hardware
---

### Post by squakie on 2014-06-29
Due to something stupid by me my new 4-month old laptop is broken (I broke the screen) and it's not covered under warranty.  Currently I am using an OLD Acer Apsire.  I had this set up with xubuntu to help my sister and brother in-law out while I fixed their laptop.

My sister had said this things would suddently stop working for long periods of time.  Now that I'm using it, I do notice this as well.  This laptop only has 512mb or memory - hopefully that's enough for xubuntu.  But when this thing stops, the disk activity light is on solid, not blinking.  Usually, if I wait 5 minutes or more, it will start blinking and then the computer comes back to life.  It does this even when just doing very simple web surfing with Firebird.

So, I'm wondering if this thing is having disk problems - perhaps high failure/recovery counts.  With a SATA drive I know how to have the drive do the testing and report back the results via the SMART interface.  However, this thing is using an IDE drive.  Are there any Linux tools available to surface scan and test the entire disk but still leave my contents on it?  I've left my sister and brother in-law's information on here so they would have a pseud backup machine if their nice laptop fails again, and I haven't backed that up, nor have I wanted to.  But I still don't want to jeopardize anything by using some sort of disk scanner/tester.

Any help would be greatly appreciated!

Thanks in advance!

;)

---

### Post by squakie on 2014-06-29
Ok, I've learned something I didn't know - I used smartmontools with the gui'd front-end and found this IDE drive does support smart.  And better yet (or worse, depending on how you look at it ;) ) it shows many pre-failure errors and everything else is marked as old-age.  So I guess that pretty much confirms it - a dieing drive.  Now to find some cheap IDE laptop drive to replace it (and th dreaded backup and restore).

---

