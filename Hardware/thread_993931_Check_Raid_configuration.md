---
title: "Check Raid configuration"
date: 2008-11-26
forum: Hardware
---

### Post by André_R on 2008-11-26
Hello,

I've installed Ubuntu Server 8.04 LTS on a machine and set it up in RAID5 configuration with 4 drives.

The system boot's and all looks fine, but:
-how can I check if the spare is "available"
-does the system boot on a spare drive if the first crashes, or do I have to setup/install something for that?
-how do I get notified if a disk has crashed

I'm using Webmin on the system but I can't find the information.
(I've only started using Ubunt since a while ago, so I might me looking in the wrong direction ... ;-))

Thanks

---

### Post by rgbtxus on 2008-11-26
mdadm -D /dev/mdXX will tell you if you have spares allocated to mdXX.
If you do and a drive fails a spare will automagically be swapped in to the array.  Depending on the size of the array this will take some time (often hours) as every block must be computed and written to the new drive.  You can watch the progress with watch cat /dev/mdstat.  If you have no spares and want one, then find/add a new partition of the same size or larger (but the larger part will be wasted) than the current components of the array and add it like this mdadm --add /dev/mdXX /dev/sdXY.

If you crash/reboot while array is degraded and on reboot the array is missing do not panic.  Your data is just fine.  Just manually reassemble the array (see any of the numerous references on linux raid to the howto).  I have been using linux raid for years and have yet to lose any data (cringe, now that was a really stupid thing to say!)

Most recently I had a sequence of transient hardware errors drop 2 drives from a 5 drive raid5 rendering it in theory totally dead (you can lose only 1).  But since the drives hadn't actually died I was able to reassemble the array and back it came (of course the resync took hours, but the array was online all the while)

---

