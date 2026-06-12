---
title: "[SOLVED] Expand Ext3 Partition and Linux Swap"
date: 2008-09-02
forum: General Help
---

### Post by r4wj4 on 2008-09-02
I'm dual booting ubuntu/xp. I deleted the D drive which just had windows recovery partition. So now i have about 10GB of free space. How do I expand the ubuntu partition to use that 10GB. Also want to expand my Linux Swap using some of that free 10GB space. Tried using gparted live cd...didn't see any option which let me incorporate that free space to my existing ext3 partition.  

new to ubuntu.

Any help please?

---

### Post by joenix on 2008-09-02
GParted should do the trick. There is indeed no explicit option to incorporate free space into another partition, but instead you will need to resize/move the existing partitions.

---

### Post by jigsaws on 2008-09-02
You can also make new partition with fdisk and mount it somewhere in the filesystem.

In the future it's good idea to use LVM to easy add space/disk to existing filesystems (and more).

---

### Post by Elfy on 2008-09-02
Why do you need to increase swap - if you used the guided option it would have set swap as it was needed iirc.

---

### Post by r4wj4 on 2008-09-02
Isn't the general rule of thumb to have the swap be 2x more than the physical ram. i have 2GB ram installed...so shouldn't the swap be 4GB then? because ubuntu just choose 1.3GB...is this enough?

thanks all.

---

### Post by Elfy on 2008-09-03
The general rule of thumb is 2XRAM but once you get to 1Gbof RAM it doesn't need to be as high, I would guess that you will rarely touch the swap at all - with 1.3GbRAM I hardly touch my swap.

But if you want to hibernate then swap should be equal to or greater than RAM

---

### Post by r4wj4 on 2008-09-03
so basically there is no way i can expand my ext3 partition to include the free 10gb space? what about LVM? can i use that for this purpose and how do i do it?

---

### Post by Elfy on 2008-09-03
I didn't say that, you must run either the buntu livecd and use the gparted on there to do so or a partition editor. Not sure about lvm - never used it.

Without knowing how the partitions have been made it is likely that the ubuntu partitions are within an extended partition - if you run this in a terminal

```
sudo fdisk -l
``` I'll be able to answer that question with the output you get.

If the buntu partitions are in fact inside an extended then that has to be expanded first, then you can add to the ubuntu partition, but without the info that is a guess:)

---

### Post by r4wj4 on 2008-09-03
output of sudo fdisk -l:

Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *         948       32317   251979525    7  HPFS/NTFS
/dev/sda3           32318       36481    33447330    5  Extended
/dev/sda5           32318       36304    32025546   83  Linux
/dev/sda6           36305       36481     1421721   82  Linux swap / Solaris

---

### Post by Elfy on 2008-09-03
Well at a guess - sda1 would have been the partition you are talking about. To resize the linux partition the unallocated space has to be next to the linux partition.

I _believe_ that the gparted [livecd]("http://gparted.sourceforge.net/livecd.php") will allow you to add at either end; the version on the ubuntu livecd will only iirc add to the end.

What you have to do is move the unallocated space to be next to the extended partition - sda3, once it is there you can resize sda3 to include all of the unallocated space.

Once the extended partition is 10Gb bigger you can then increase the size of the linux partition (sda5).

It could take a long time to complete - do not turn it off, or think that it has hung/crashed.

If you have important data on any of your drives make sure you have suitable backups, there is always a possibility of problems and you are editing partitions here.

---

### Post by louieb on 2008-09-03
Given where the free space is located the easiest thing to do is turn it back into a primary partition, format it ext3 and use it for a data partition or a place to keep backups. Once you created the partition and format it Ubuntu should detect it and and add to the places menu.

Trying to move the unallocated space to where you could use it to make the Ubuntu partition larger is kinda scary to me. Certainly nothing I would do without a full disk backup.

---

### Post by r4wj4 on 2008-09-04
yeah i'll boot into gparted live cd and try moving it next to my ubuntu partition. yeah i did format it into fat32 and it worked fine if i wanted to share things between xp and ubuntu but i just want ubuntu to use that space and include it in it's partition.

thank you forestpixie and other for all the help, really appreciate the community support.

---

