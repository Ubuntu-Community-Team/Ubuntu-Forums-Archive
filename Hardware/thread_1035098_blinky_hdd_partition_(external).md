---
title: "blinky hdd partition (external)"
date: 2009-01-09
forum: Hardware
---

### Post by groggin on 2009-01-09
hi all
  i'm using Ubuntu UE (gamers ed) and am having an unusual problem with an external hdd.
  the device is three years old, WD 120 gB (used to be my pc's internal secondary hdd ... ) it is formatted with two partitions, ~20 gB vFAT + ~100 gB ext3. both partitions function perfectly in windows, (i was able to play .FLAC files from the ext3 drive and video from the FAT) and in Ubuntu the vFAT drive  is fine too, and opening a folder on the ext3 drive works, but data transfers take f  o  r  e  v  e  r ..., like 3 hours for ~700 mB if they dont fail from a disk unmounting first (transfer stops and links to the disk are broken). 
  i tried reformatting the disk ext3, no change.
  i formatted it vFAT, and the first few gigs went over just fine, then it quit, and has returned to its snail's pace. 
  i went back to windows and ran chkdsk on it, fixed errors, back to Ubuntu and again first few gigs ok then no go ... wassup with this??? :confused:
     must be a way to disk check from ubuntu??

               thanks

[edit]  ok i used gparted to check the disks, still slow so i guess either the drive or the external case is dead ... any other possability?

---

