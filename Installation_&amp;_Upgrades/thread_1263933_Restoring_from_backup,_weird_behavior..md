---
title: "Restoring from backup, weird behavior."
date: 2009-09-11
forum: Installation &amp; Upgrades
---

### Post by creiss on 2009-09-11
Hello all!

Due to a hdd change I backed up my entire / via rsync (-av) to an external (ext2) hdd. The process went smooth, and I did it twice just to be sure. Anyway, the backup is OK - or so i believed.

Anyway. New HDD in, gave old to friend who wiped it first thing. So I reinstalled a fresh system from the alternate installation system (due to encrypted hdds). The system was up and running. Now I booted from the live cd, apt-get'ed cryptsetup and mounted the old and new hdds. Even took a backup of the new /etc backup (for fstab, blk* and cryptdevices) and did a restore (rsync -av --delete) from the external hdd to the new one, just replacing the new ones etc files (those 3 I mentioned above). 

Now I recognized something evil: I did not back up my /boot partition, it was not mounted at the time I took the backup! So i went with the newly created /boot partition. 

The status of the system:

/ is old data, with new files in /etc (fstab, crypt*, blk*)
/boot is new data, with no modifications from the old hdd

Off to a reboot with the new system. To my suprise it found the encrypted partitions, decrypted it, found the initramfs, booted the system all the way up to the login screen. Just two things are weird and annoying:

- The splash screen (ubuntu) goes away after I entered the LUKS password, showing the ugly console logging stuff. (all ok). How can I put the splash screen back? All the way to X?

- **Edit: Solved after 2 reboots: **The bootup pauses for a long time during dkmps (or so) for the modules  for virtualbox and fglrx. This used to be way faster **[SOLVED]**

- I installed (the old system) from an Ubuntu 9.04 system and did regular updates. The new /boot partition never got those updates, but its registered as "updated", as the apt-cache is on /, not reflecting the changes.


I guess it boils down to this question: How can I repopulate /boot from scratch, "syncing" it with the "rest of the world"? 

Thank you all for your continued support for Ubuntu!
I know this might be a hard one.

cheers!
-Christian.

---

