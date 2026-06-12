---
title: "Boot Disk Check Error"
date: 2008-10-22
forum: General Help
---

### Post by camoanimal on 2008-10-22
This has been a regular event for about two weeks.  Whenever I boot Ubuntu the loading bar gets about 35% done then the Fstab disk checker start examining my HDD.  After getting through about 5% of the check it runs into an error that requires me to log in as the admin in a terminal like screen (without X of course).  After logging in as admin to allow it to finish the process it gives off a repetitive error saying that a certain file is missing.  I don't remember the exact file, but it wasn't an important one by any means.  At this point Fstab errors out and quits, then waits for me to restart the system.  At this point I restart the system only to get the same disk check at which point I opt out by pressing 'ESC' and continue to GDM.  Everything runs fine once its done loading.  What should I do to fix or disable this error?  :confused:

---

### Post by dcstar on 2008-10-23
> **camoanimal said:**
> This has been a regular event for about two weeks.  Whenever I boot Ubuntu the loading bar gets about 35% done then the Fstab disk checker start examining my HDD.  After getting through about 5% of the check it runs into an error that requires me to log in as the admin in a terminal like screen (without X of course).  After logging in as admin to allow it to finish the process it gives off a repetitive error saying that a certain file is missing.  I don't remember the exact file, but it wasn't an important one by any means.  At this point Fstab errors out and quits, then waits for me to restart the system.  At this point I restart the system only to get the same disk check at which point I opt out by pressing 'ESC' and continue to GDM.  Everything runs fine once its done loading.  What should I do to fix or disable this error?  :confused:

```
gksudo gedit /etc/default/rcS
```

Make:

FSCKFIX=YES

Now it will automatically answer "y" to the fsck on boot and (hopefully) fix the filesystem errors. You will still need to replace the missing/corrupted file.

---

