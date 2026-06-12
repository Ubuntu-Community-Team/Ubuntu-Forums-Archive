---
title: "Ubuntu cant boot"
date: 2008-11-03
forum: General Help
---

### Post by thestig_992 on 2008-11-03
I had another similar thread recently, because i broke my partitions.
Now I have an issue because of this. What i did to fix my previous problem was to delete all my partitions, then recreate a single partition. I did so knowing full well that i wouldnt be able to boot.
But i have a plan to fix my OS, and i wanna check if it makes sense to the pros...and maybe see if anyone has a better suggestion.
Currently my hdd has a single partition, with 40gb free. To restore my mbr, i thought i would use the ubuntu installation to create a partition at the end of the disk, with a full working ubuntu. Since that was just to make the boot partition, i will then destroy it. The install should also see that there is no swap and extended partitions, and will create them. I can then use gparted to get rid of the newly installed ubuntu partition, and point grub at my original os.
Thats all i think i need to do. please comment and make suggestions if you have any.

---

### Post by thestig_992 on 2008-11-04
bump, plz dont get scared away by all the text i wrote....XD

---

### Post by thestig_992 on 2008-11-11
bump, is there a repair tool in the live cd?

---

### Post by geirha on 2008-11-11
Try the super grub disk [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by TeXtonyx on 2008-11-11
I suggest that you resize your one partition that has 40GB free.
Suppose you shrink it by 5GB, 10GB or 20GB. That creates 5, 10, or
20 GBs of unallocated space. During the Ubuntu live cd install, you
can choose 'largest free space (guided)'. Then Ubuntu will install
all the needed partitions in just the unallocated space you made for
it, 5,10 or 20. By default grub will be installed in the MBR. Did 
you leave out something to consider like whether you have another
OS already installed on the partition with the 40GB of free space,
which means unused space within the partition, not outside of the
partition which is called unallocated space, except for the live cd
terminology. If you had Windows OS installed for instance, you can
rewrite the MBR from the Recovery Console of the install cd. Or 
you can have both types of OS working which is called dual booting.

---

### Post by thestig_992 on 2008-11-13
I dont have another OS in the space, its just empty space on the same partition. Thats not a bad idea, though since my ubuntu is currently running off a single partition, no swap space, this wont entirely work...is it possibble to then delete that other ubuntu (from the fresh install) and use that space as swap space? How would i point ubuntu at that space..?

---

