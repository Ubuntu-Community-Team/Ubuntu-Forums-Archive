---
title: "[SOLVED] Restoring swap space"
date: 2008-11-14
forum: General Help
---

### Post by thestig_992 on 2008-11-14
I dont know if anyone remembers my other threads, but basically i broke my comp, and im now in the final stage of fixing it. I have a single partition on my 250g drive running ubuntu. Explaining why is kinda a long story...so i wont! Anyways, I just made the drive bootable again with supergrub, and now i need my swap space and extended partitions back.

I dont know the sizes nor the partition numbers from the original setup, though i could make a reasonable guess. Also, I'm fairly competent with fdisk, if that helps...

---

### Post by WWSmith36 on 2008-11-14
You can use gparted from the LiveCD (System-> Administration-> Partition Editor) to create your swap and extended partitions.  You will have to resize you single ubuntu partition to create space.  Your swap partition should be 1.5-2.0 times the size of your RAM and your extended data partitions may be anysize you choose.

Hope this helps

---

### Post by thestig_992 on 2008-11-14
how will ubuntu know that these are swap and extended partitions though? Is it a type of partition that gparted will prompt me for?

---

### Post by taurus on 2008-11-14
You don't have to create an extended partition.  If you want to shrink your / partition, making room for swap partition, you must use gparted from the LiveCD since you cannot shrink a partition while you are using it.  

So, boot your machine with the LiveCD and use gparted to make some room for a swap at the end of the drive.  Then, you need to mount your / from the LiveCD and edit /etc/fstab (on the harddrive) to add an entry for the swap.  You can also add an entry in /etc/fstab for your swap once you boot your machine up again from the harddrive.

---

### Post by thestig_992 on 2008-11-14
ty, so swap is just mounted in fstab? Im sure ill be able to work it out now...XD

btw, what does extended do?

---

### Post by taurus on 2008-11-14
Basically, you can only have four primary partitions and if you need more than four, you need to make one of those four primaries into an extended partition.  Then under than extended partition, you can create a bunch of logical partitions.  Since you will use only two partitions, one for / and one for swap, make both primaries then.  Easy and clean.

---

### Post by thestig_992 on 2008-11-14
kk, ty

---

### Post by thestig_992 on 2008-11-15
Im on the live cd now, and i can see that my fstab has the UUID tag for the partition rather than the /dev/sda2. I found that i can use blkid to list the uuid, but when i do it, nothing happens...how do i fix this, or can i just use /dev/sda2 instead?

EDIT: Nvm, fixed it by using sudo...

---

