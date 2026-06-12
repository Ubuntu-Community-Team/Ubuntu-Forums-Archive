---
title: "4*SSD software RAID0 (mdadm) - disk IO performance issues"
date: 2012-04-20
forum: Hardware
---

### Post by streetdaddy on 2012-04-20
The short story: new laptop with fakeraid and 4*SSD 64G has _terrible_ disk IO (20-30MB/s) at random intervals.

Any suggestions for optimisation or configuration options I might have missed?

The long story:

I've just had a new laptop delivered - Sony VAIO VPCSE custom build.  I requested an upgrade to 256G SSD, and what I received is 4*64G SSD's in RAID 0 configuration (fakeraid)...

First, I deleted all of the partitions, but kept the fakeraid.  Ubuntu 11.10 64bit installation was _very_ slow ie. 40-50 minutes, I thought I'd let it finish anyway. The install finished, and boot time was great (<10s from powering on to login screen), however once the desktop was loaded the disk I/O was sometimes fantastic (ie. 250-350MB/s writes), then other times it would slow right down for no apparent reason (20-30MB/s).  When it slowed down, the laptop was pretty much unusable and a reboot or hard shutdown was needed.  Once rebooted, the same problem would come back at random.

I blamed the fakeraid, so I disabled the RAID controller in the BIOS and setup mdadm software RAID 0 via the Ubuntu installer.  This time installation was much quicker, however the same problem with disk I/O exists, however not as frequently as it was with the fakeraid.  

Any suggestions of how I can trace the cause would be appreciated.

---

