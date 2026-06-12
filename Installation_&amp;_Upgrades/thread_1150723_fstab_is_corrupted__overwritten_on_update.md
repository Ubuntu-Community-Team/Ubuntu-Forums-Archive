---
title: "fstab is corrupted / overwritten on update"
date: 2009-05-06
forum: Installation &amp; Upgrades
---

### Post by davemiles871 on 2009-05-06
With Hardy Heron 8.04 I regularly get a problem where /etc/fstab is overwritten (seemingly back to its original state) each time a software update is run. I have 2 disks each with a single partition and /dev/sdb1 contains /home. I manually edit the file to add the line 

/dev/sdb1 /home ext3 defaults 0  2

This lets me mount the volume and subsequent reboots it mounts ok, but then along comes an update or two and the line disappears.

Any Ideas ?

I'm running this particular system as a VM under VMware ESX with two virtual SCSI disks, if that helps

Regards

Dave

---

