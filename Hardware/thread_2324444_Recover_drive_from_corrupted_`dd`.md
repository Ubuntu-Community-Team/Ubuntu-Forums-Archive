---
title: "Recover drive from corrupted `dd`"
date: 2016-05-13
forum: Hardware
---

### Post by diamondburned on 2016-05-13
Two years ago I took my hard drive and zero-d out the drive using dd. However, I was a little impatient so I cancelled out the process and restarted the computer. The result is that I got an Input-Output error. Are there any solution to check and fix these errors?
**edit 1:** I did sudo dd if=/dev/zero of=/dev/sdb to zero out the drive. I cancelled when it performed the action for 5 minutes

---

### Post by weatherman2 on 2016-05-13
You'd be in the same situation even if you had let the dd command finish and zero the entire drive.  The first zero was to the partition table at the beginning of the drive.  The only downside of interrupting the command was that you didn't clear out all of your old files, only the files at the beginning of the drive.  The rest of them might still be recoverable, so if you were hoping to get rid of them completely, to prevent some other person from recovering them if you ever part with this drive, re-run the dd command and let it finish this time.

If the drive was/is healthy, to re-use the drive (assume old data completely gone), all you probably need to do is create a new partition table.  Try Gparted.  There's a menu option to create the new partition table; once you do that, you can create new partitions.

---

