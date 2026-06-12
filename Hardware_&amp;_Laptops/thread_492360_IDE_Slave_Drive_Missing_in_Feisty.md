---
title: "IDE Slave Drive Missing in Feisty"
date: 2007-07-04
forum: Hardware &amp; Laptops
---

### Post by Ath0s on 2007-07-04
Just installed Feisty after using Slackware for years.  

My secondary IDE port has two CD drives.  The one configured as slave is missing in feisty.

The hardware is ok (my machine is dual-boot and windows sees it - and slackware saw it fine before).

I tried removing the current master drive, and changing the slave to be master and feisty finds it just fine, so it's not a hardware compatibility thing ... 

My primary IDE port has two hard drives, both of which feisty finds fine ... it's just the slave drive on the secondary IDE it can't seem to find.

I suspect it has something to do with the udev or automount systems, neither of which I'm very familiar with.

Feisty seems to interpret all my disks as SCSI drives (even though they're really IDE), so the device names for the found drives are:
/dev/sda and /dev/sdb for the hard drives on the primary IDE port, and
/dev/scd0 for the master CD on the secondary IDE port

I guess this means I'm missing the /dev/scd1 port ... since udev isn't automatically creating it, what can I do manually?

Any help would be GREATLY appreciated ... like Ubuntu a lot so far ...

---

### Post by Ath0s on 2007-07-04
fixed it ... sort of ...

I moved the jumpers on the drives so the slave is now master and vice-versa ... now feisty finds them both?

No idea why ... but I've got them both back now, so all is right with the world ...

---

