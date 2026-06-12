---
title: "Can't mount LVM at boot"
date: 2009-10-06
forum: Installation &amp; Upgrades
---

### Post by rajwani on 2009-10-06
I have installed Jaunty 9.04 with RAID1 and LVM.

Everything works well except I can't seem to be able to mount the LVM at boot time.

The message I get at startup is:

/sbin/fsck.xfs: /dev/mapper/datavg-datalv does not exist
fsck died with exit status 8

Once the system has booted, I can sucessfully do

vgchange -ay

and the logical volume becomes active.

How come vgchange is not being run at boot?

Is there some workaround for this?

Thanks,

Arif

---

### Post by rajwani on 2009-10-07
Bump....

I should add, the MD array is started successfully at boot, it's just the LVM that isn't being started

Anyone?

Arif

---

