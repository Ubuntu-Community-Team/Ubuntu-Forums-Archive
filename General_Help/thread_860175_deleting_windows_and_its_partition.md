---
title: "deleting windows and its partition"
date: 2008-07-15
forum: General Help
---

### Post by Cilionelle on 2008-07-15
Good evening.  I'm going to do it!  I'm going to delete Windows!

...


Um.  How do I do that again?  I have it installed on a partition (I don't even want the partition anymore, to tell the truth...) and just want to delete it.  Ta!

---

### Post by SpenceMakesSense on 2008-07-15
try using the ubuntu live cd and using the partitioner. You can delete it and resize it to your ubuntu partion

---

### Post by danwood76 on 2008-07-15
Unless the ubuntu partition is after the windows one.
That will give the partitioner problems (relocating data).

Delete the partition using gparted and re make it ext3.
You can do this from your normal ubuntu session by installing gparted through synaptic.

---

### Post by Cilionelle on 2008-07-15
Will the change in versions from 7.04 to 8.04 make a difference?  I've only downloaded/updated Ubuntu, and don't have the 8.04 disk.

---

### Post by danwood76 on 2008-07-15
You dont need the live CD it can be done from within ubuntu.

You just end up with an extra drive as opposed to more space but to be honest I'm not sure about backwards resizing in gparted anyway, it always gives errors for me.

---

### Post by sandysandy on 2008-07-15
post output of sudo fdisk -lu

regards

---

### Post by Cilionelle on 2008-07-15
'sudo fdisk -lu' gives:

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       64259       32098+  de  Dell Utility
/dev/sda2   *       64260   104647409    52291575    7  HPFS/NTFS
/dev/sda3       104647410   154015154    24683872+  83  Linux
/dev/sda4       154015155   156248189     1116517+   5  Extended
/dev/sda5       154015218   156248189     1116486   82  Linux swap / Solaris

Cheers!

---

### Post by Cilionelle on 2008-07-17
I've downloaded and had a look at gparted, but the ntfs disk is unable to be changed in any way.  There is another ntfs on the system, a 9GB one, with an exclaimation point before it on the gparted list.  I have the option to format that one, but not the one I've got mounted.

*Lights come on!*

I have to unmount it, don't I!  Ah ha!

Thanks all!

---

### Post by BLTicklemonster on 2008-07-17
but won't he have to redo fstab and also /boot/grub/menu.lst?

---

### Post by danwood76 on 2008-07-18
Yeah but thats just a formality afterwards.
It will still boot with that partition gone.

@ Cilionelle

Not sure if you know this but to unmount a partition you do this command in terminal:
```

sudo umount /dev/BLOCK_DEV_NAME

```
so to unmount your ntfs drive you do:
```

sudo umount /dev/sda2

```

---

### Post by Cilionelle on 2008-08-22
Hey!  Thanks for the help before.  I didn't follow through all the way with the changes, missed out on redoing fstab and /boot/grub/menu.lst, and was wondering if someone might be kind enough to post details on how to do that.

Cheers!

---

