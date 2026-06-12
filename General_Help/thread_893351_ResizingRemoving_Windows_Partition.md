---
title: "Resizing/Removing Windows Partition"
date: 2008-08-18
forum: General Help
---

### Post by ragflan on 2008-08-18
[IMG]http://ramipage.googlepages.com/Screenshot--dev-sda-GParted.resized.png[/IMG]


1.) That's how my system is partitioned. I have tried to resize the Windows partition by shrinking it in Vista (after defragmentation) but it cannot be shrunk any further. Only half of the 80gb is actually being used by Windows Vista. I cannot resize the Windows partition through GParted found under System -> Administration. Must I have to do this using a GParted liveCD or will I get the same results?

2.) If I cannot resize the partition and decide to remove it, can it merged into **/** mount point without affecting my system?

---

### Post by cdtech on 2008-08-18
You must use the "gparted live cd" to do any partitioning on the primary drive that you boot into. You wont loose any data if it's done correctly.

Hope this helps......

---

### Post by Too Late on 2008-08-18
You have to install ntfsprogs package to enable NTFS resizing with gParted. The LiveCD already has this feature, but you can install it to your system, too (with Synaptic).

I'm not sure if I understood the 2nd question correctly, but as far as I know, gParted (or any else program) cannot merge ntfs and ext3 partitions together.

---

### Post by tfosorcim on 2008-08-18
Don't know if it's true or if it's been done but I heard you sometimes need to disable system restore points in Vista before resizing the partition.

---

### Post by ragflan on 2008-08-18
> **Too Late said:**
> You have to install ntfsprogs package to enable NTFS resizing with gParted. The LiveCD already has this feature, but you can install it to your system, too (with Synaptic).

I'm not sure if I understood the 2nd question correctly, but as far as I know, gParted (or any else program) cannot merge ntfs and ext3 partitions together.

Oh, the second question means that if I delete the Windows partition, won't it be just empty space? Can I then format it and join it to the / mount point?

---

### Post by ragflan on 2008-08-18
> **tfosorcim said:**
> Don't know if it's true or if it's been done but I heard you sometimes need to disable system restore points in Vista before resizing the partition.

I shall try this. I've got some assignments due this week and once I'm done with them, I'll try this and try resizing.

---

### Post by cdtech on 2008-08-18
If you delete the Windows partition, yes it will be empty space. Just extend whatever partition you want to fill the empty space.

---

### Post by ragflan on 2008-08-18
> **cdtech said:**
> If you delete the Windows partition, yes it will be empty space. Just extend the ext3 to fill the empty space.

And that won't affect my exiting Ubuntu installation right? And also, do I just extend the empty space or do I need to format it to ext3 before extending - I think it's just extend the empty space, correct? I just wanna make sure. I don't wanna screw up my Ubuntu installation and have no Vista on the partition?

---

### Post by Too Late on 2008-08-18
> **ragflan said:**
> Oh, the second question means that if I delete the Windows partition, won't it be just empty space? Can I then format it and join it to the / mount point?
You can delete the Windows partition, and then grow the current sda2 partition to the left. Of course, you can also create a new partition there, and mount it somewhere else than /. Or then you can do both (grow the current sda2 a bit and create a new partition in the beginning of the disk).

---

### Post by cdtech on 2008-08-18
correct, no need to format. It will transfer all of the data for you. I've done this with great success.

---

### Post by Too Late on 2008-08-18
> **ragflan said:**
> And that won't affect my exiting Ubuntu installation right? And also, do I just extend the empty space or do I need to format it to ext3 before extending - I think it's just extend the empty space, correct? I just wanna make sure. I don't wanna screw up my Ubuntu installation and have no Vista on the partition?
Is's possible that you have to edit your /boot/grub/menu.lst and /etc/fstab files after partitioning things. Also, if (and when) your grub image files are installed in the sda2, you might need to reinstall grub, since their location on the disk may change (during resizing) so that the bootloader (in MBR) can't find them. But these are just minor things.

---

### Post by ragflan on 2008-08-18
To actually be confident enough to remove the Vista partition, is it sufficient to have VirtualBox and a copy of my Windows installation disc in case I ever need it?

---

### Post by cdtech on 2008-08-18
> **ragflan said:**
> To actually be confident enough to remove the Vista partition, is it sufficient to have VirtualBox and a copy of my Windows installation disc in case I ever need it?

Sure. I personally run a dual drive setup (keeping Vista on the secondary drive) and boot through GRUB's bootloader. I also use VMware with XP through my Ubuntu OS. If you really want to wipe Windows just be sure it's what you want to do. Having the install disc helps.

---

### Post by ragflan on 2008-08-22
Oh one more question. Ummm. Let's say I do these steps:

1.) I remove the Windows Vista partition (I've been wanting to remove it and install Windows XP for a while now anyway), 
2.) I distribute my space to my home folder and **/** mount point.
3.) I leave about 15-20gb for Windows XP. 
4.) **First Question. **15-20 is plenty for XP, isn't it? Or can I do with lesser?
5.) **Second Question.** If I install XP, will it screw up my GRUB? If it does, how do I replace GRUB?

---

### Post by redester on 2008-08-25
I have a new and larger HD on which I wish to transfer my current partitions, effectively doubling some.  I have created (Fdisked) and DD'd the first two and it looks good so far.     

 Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63     1510109      755023+   6  FAT16
/dev/sdb2         1510110   343871324   171180607+   c  W95 FAT32 (LBA)
/dev/sdb3       625040955   625105214       32130   82  Linux swap / Sola
/dev/sdb4       343871325   625040954   140584815   83  Linux

Partition table entries are not in disk order

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x06f290f1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63     1510109      755023+   6  FAT16
/dev/sdc2         1510110   343871324   171180607+   c  W95 FAT32 (LBA)

I would like to double the size of /dev/sdc2 before creating a swap and Linux partition.  I would use the remainder of the drive as linux. I would then DD /dev/sb4 to /dev/sdc4.

Would linux see the larger size of its new partition or would it have to be extended also?

Also..a new MBR/partition table will have to be created for the new drive.
How may that be achieved?

I'm on new and shaky ground here!  :)  Any help will be appreciated,

Ray

---

