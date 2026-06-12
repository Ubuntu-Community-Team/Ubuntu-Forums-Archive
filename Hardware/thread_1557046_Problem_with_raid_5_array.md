---
title: "Problem with raid 5 array"
date: 2010-08-20
forum: Hardware
---

### Post by Godsbrother on 2010-08-20
Hi,

Not getting any replies in teh general section so reposting here..

I have 10.4 and am trying to add 3 x Samsung 1TB drives (HD103SJ) connected via a generic SIL-3114 controller (not using raid).

I am using webmin (current version) and when attempting to use mdadm to create a raid 5 array get the following error -

Failed to create RAID : mdadm in --create mode failed :

mdadm: array /dev/md0 started.

Now when you go back and look at the raid array it shows as active but degraded with a failed drive and is recovering.

I can't figure out why?

Anyone got any suggestions......

---

### Post by ronparent on 2010-08-20
Were any of the three drives used in a MB with the raid turned on, If so metadata has been written to the drive that has to be erased prior to trying to use it/them in a non fakeraid environment. If so, you should also subsequently uninstall dmraid.

---

### Post by Godsbrother on 2010-08-24
No all three are brand new drives. Incidently the pci card has since failed! so I'm thinking this may be the casue so a soon as I source a replacement I shall have another go....

---

