---
title: "IDE drives not appearing as hdX, instead appearing as sdX (SCSI/SATA naming)"
date: 2013-10-31
forum: Hardware
---

### Post by wallymann on 2013-10-31
i have installed an IDE controller card (PCI-E) in my workstation running 12.04.  linux convention is for IDE drives to appear as hda, hdb, etc.  i need to use a utility that was written to access drives directly and it expects drives to have hdX naming (i.e., only works with IDE controllers).

however, when connected to the IDE card my IDE drives appear with sda, sdb, etc as if they are SCSI/SATA drives.

looking for any insights as to why this might be happening and how to fix it or maybe there's a workaround to force SCSI/SATA devices to appear as IDE devices.  

thanks in advance!

---

### Post by oldfred on 2013-10-31
It was about 5 or 6 years ago they eliminated the use of hdX and standardized on sdX. They consolidated drivers somehow as I remember.
I think some other distributions may still use the hdX. I found this in my notes:
 SATA will use sda1 and IDE devices use hda1 in Slitaz

---

### Post by Yellow Pasque on 2013-11-01
Perhaps a symlink will work..

---

### Post by coffeecat on 2013-11-01
> **oldfred said:**
> It was about 5 or 6 years ago they eliminated the use of hdX and standardized on sdX. They consolidated drivers somehow as I remember.


That's my memory too. I found an old thread on another forum from 2007 that states it was from the 2.6.20 kernel that the kernel drivers were consolidated, which does put that at about 6 years ago. Which would mean that any distro still using the hda convention for ide drives would be using an old kernel or a special patch for a newer one, I guess.

---

### Post by warp99 on 2013-11-02
> **Temüjin said:**
> Perhaps a symlink will work..


If you symlink the drives in /dev that should work.

---

