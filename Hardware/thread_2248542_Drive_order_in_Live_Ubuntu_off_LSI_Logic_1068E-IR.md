---
title: "Drive order in Live Ubuntu off LSI Logic 1068E-IR"
date: 2014-10-15
forum: Hardware
---

### Post by matthew57 on 2014-10-15
I'm working on installing a new server which uses Ubuntu as the OS. The installer package boots to a live Ubuntu off the DVD and then installs a hardened version of Ubuntu with the server software.

I have a Dell PowerEdge T710 server with a LSI Logic 1068E-IR SAS controler, hosting 5x 500GB drives (2 WD, and 3 Dell Branded WD drives). I have slots 0 and 1 tied into a RAID1 for the OS and server files. Install documentation suggests leaving the remaining disks out of a raid until after the install, and that they would be joined into a ZFS RAID5 during configuration of the 3'rd party software post-install.

Here is my problem; The installer requires the install disk to be device HDA, however my RAID1 keeps coming in as HDD after the 3 un-RAIDED disks taking positions HDA-HDC. I cannot figure out how to swap these around for the life of me. The support desk suggested I create 3 single disk RAIDs for the 3 drives, but the controller does not allow this to happen. Any suggestions for how to make this work?

---

