---
title: "[SOLVED] /var move kernel log hangs on boot, processes fail to start thereafter"
date: 2008-07-14
forum: General Help
---

### Post by wilbbe01 on 2008-07-14
Hello all, I've got a situation after I moved /var to a new drive.  The process I used is as follows.

boot into livecd
move data off of /var to new harddrive using cp -rp
once data is copied over, move old /var to /var_bk
create new /var with run and lock subdirectories
change fstab to point the new drive to /var
reboot into hard drives

Boot goes well until the Kernel log start up.  At this point it hangs for quite some time and then kernel log fails, things move on and boot goes normal besides mysql and backuppc both failing to start.  The errors for the backuppc and mysql have to do with permissions (or at least it says the backuppc one does, but mysql shows nothing more than fail).

The exact error is mkdir /var/lib:  Permission denied at /usr/share/backuppc/bin/BackupPC line 1791

Does anyone have any idea why things decide to not work after the move to a new partition?  Reverting everything back fixes all problems.


Thanks

---

### Post by wilbbe01 on 2008-07-16
Solution = Do not try and move var in the first place.  If you must move it to a different drive then rebuild the server and set the mountpoints at install.

---

### Post by dcstar on 2008-07-16
> **wilbbe01 said:**
> Hello all, I've got a situation after I moved /var to a new drive.  The process I used is as follows.

boot into livecd
move data off of /var to new harddrive using cp -rp
once data is copied over, move old /var to /var_bk
........
Does anyone have any idea why things decide to not work after the move to a new partition?  Reverting everything back fixes all problems.


"cp -rp" does not copy links, it is no wonder things didn't work.

"cp -a" may have worked better.

---

### Post by wilbbe01 on 2008-07-16
Thanks, yep, I can't see.  The rebuild worked though.  Thanks for your help.

---

