---
title: "Live CD does not recognize IDE harddisk"
date: 2013-03-16
forum: Hardware
---

### Post by dyno7351 on 2013-03-16
I am trying to install 12.04.2 LTS to a blank 40G IDE hard-drive that was previously used in a raid array under windows XP. I used GParted to delete the existing partition on the drive leaving the disk blank. The desktop CD could not even see this drive. I then tried partitioning/formatting the disk with an ext4 primary partition. The installer still could not see the drive. I'm guessing that when the drive was used as part of a raid array, some part of the drive has information still present that says it is part of a raid array. If that is what is preventing this drive from visible to the installer, how do I clear everything having to do with its previous raid usage. Note, it will NOT be part of a raid array from now on.

---

### Post by ac5jw on 2013-03-16
Hi, I think I have the reverse problem.  My hard drive behaved like it did not exist until I put in a live/install DVD.  It turns out that my computer was ignoring live/install CDs.  Once I realized what my PC was accepting and rejecting, I sorted my media by type and now I just use CD media on my backup computer.  But, all my DVDs will work on my primary computer and the backup.  Could the media type be a factor in your case?  If you are able to boot live with the CD, then the fact of it being a CD media should not be a problem for you.

I only mention this because I initially tried to install Ubuntu 12.04.2 LTS with CDs from Canonical, and they would only work on my backup PC.  My primary refused to install the software until I obtained a live/install DVD media for it.

Good luck !

---

### Post by ronparent on 2013-03-17
dyno:

>  I'm guessing that when the drive was used as part of a raid array, some part of the drive has information still present that says it is part of a raid array.
This is probably your problem. Once written to a disk by the MB raid bios the raid designation persistently remains in as metadata on the drive until explicitly erased. To erase it, boot to a live CD session, open a terminal, and enter the command -
> sudo dmraid -Er /dev/sda - or whatever designation applies to your drive
That will erase the metadata and should solve your problem. Post how you make out.

---

### Post by dyno7351 on 2013-03-18
Thanks for the suggestion. I will give this a try.

---

