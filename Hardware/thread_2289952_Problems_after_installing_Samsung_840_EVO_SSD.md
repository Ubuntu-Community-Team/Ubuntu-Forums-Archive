---
title: "Problems after installing Samsung 840 EVO SSD"
date: 2015-08-08
forum: Hardware
---

### Post by mbuom on 2015-08-08
Recently i've replaced my HDD with a Samsung 840 EVO SSD (120Gb). Since then i've experienced random freezes from which i could only recover by rebooting. System has become more and more unstable, giving  more and more system errors (kernelsoops, null pointer).

I'm pretty sure the cause is the queued TRIM command bug, since i did infact update the firmware to the latest when the SSD was still in use on the windows machine. I've read that this has been 'fixed' by putting the SSD's on a 'blacklist' so the faulty command is no longer given.

Thing i need your help with guys is what do i need to do to make my system stable again? If i do a clean reinstall will that solve my problems? Has this new 'blacklist' been entered in the current LTS release? Or do i have to install 14.10 ? Either is fine but 15.04 is a no-go for compatibility reasons.

Sorry i can't find these answers myself i'm still pretty new to ubuntu.

My source: [https://bugs.launchpad.net/ubuntu/+source/fstrim/+bug/1449005](https://bugs.launchpad.net/ubuntu/+source/fstrim/+bug/1449005)

Any help is appreciated. Thanks!

---

### Post by wirywolf on 2015-08-08
Was Ubuntu freshly installed on your new SSD? Did you enable continuous TRIM?

---

### Post by mbuom on 2015-08-09
Yes it was. I didn't alter any settings concerning the SSD nor did i arrange for any TRIM to run on the disk.

I ended up reinstalling on the same disk, fresh format, and to be sure i disabled NCQ altogether. I also make a cronjob to run fstrim daily (most posts i read say this method is preferred over the discard option in fstab). All seems fine. For now...

I guess i was just unlucky. Had I installed the new disk a month later there would have been made an addition in the kernel that had corrected for the faulty new firmware.

---

