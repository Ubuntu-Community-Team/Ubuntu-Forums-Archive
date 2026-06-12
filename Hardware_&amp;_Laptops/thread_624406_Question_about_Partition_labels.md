---
title: "Question about Partition labels"
date: 2007-11-26
forum: Hardware &amp; Laptops
---

### Post by dolphin_oracle on 2007-11-26
I currently have a triple boot laptop with the following partition information.  

/dev/hda

/dev/hda1 - windows xp
/dev/hda2 - gutsy (xubuntu)
/dev/hda4 - feisty (xubuntu)
/dev/hda3 - extended partition containing /dev/hda5 - swap

All installations are in working order.  I had originally installed gutsy in a dual-boot situation with xp, but hibernate wouldn't work on my old laptop.  Hibernate worked under feisty, so I set up another drive to test other things I had setup under gutsy.

long story short, I now no longer need the gutsy installation, and I want to remove it.  If I delete /dev/hda2, will the other partitions be renamed?  If the partitions are renamed, will that nuke my feisty installation?   I want to reclaim the space and add it back into my feisty partition.

Thanks.

D.O.

---

### Post by ryanVickers on 2007-11-26
They will not be changed or renamed, but there is a slim chance you won't be able to boot.  In this case, just boot a live CD and tinker with the /boot/grub/menu.lst file until is works again :p

Of course, you will have this big gap in the middle of your HD with the space not being used... seems like a waste... unless you can move feisty afterwards...

---

### Post by dolphin_oracle on 2007-11-27
That was my plan - Gparted can move and resize partitions, but I wasn't sure about the labeling.

Thanks.

D.O.

---

### Post by dolphin_oracle on 2007-12-02
Update:  I deleted my gutsy partition and added the now unused space to my hda4 partition.  No problems other than an erroneous file system check on a now non-existant partition.  I commented out the offending line in /etc/fstab, and had no problems since.  

Tip on the boot issue, set the default boot parition to something other than the drive you are deleting ahead of time.  The old menu entries will remain in grub, but at least you can boot.

---

