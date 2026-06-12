---
title: "[SOLVED] Can't mount hdd's?"
date: 2008-10-23
forum: Hardware
---

### Post by Cyric78 on 2008-10-23
I had to force a shutdown today, and now I can't mount my hdd's.. it comes up with an error:

mount_point cannot contain the following characters: newline, G_DR_SEPERATOR (usually /)

What is that supposed to mean, and how can I fix it? LOL... I thought I had everything working well, had my shares setup properly, and was just about to move the file/media server into its permanent home...

---

### Post by JC Cheloven on 2008-10-23
Is it an external HD? 
Could you please post the output of ```
fdisk -l
``` and your /etc/fstab file

so that we can have a better idea of what you have?

---

### Post by Cyric78 on 2008-10-23
No, niether drive is external, they are all internal..

fdisk -l:


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d0e24

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60756   488022538+  83  Linux
/dev/sda2           60757       60786      240975   83  Linux
/dev/sda3           60787       60801      120487+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000dcee0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   83  Linux

Disk /dev/hda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x90909090

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1216     9767488+  83  Linux
/dev/hda2            1217        2432     9767520   82  Linux swap / Solaris
/dev/hda3            2433       14946   100518705   83  Linux


fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=eaf71c5b-ec3f-4cd0-ac43-ca3eb00510b8 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda3
UUID=392cd005-bf44-4228-9ff2-b48f22434ef7 /var            ext3    defaults        0       2
# /dev/hda2
UUID=53f561ba-a90b-4c6c-9475-9baf63aaa948 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

---

### Post by Cyric78 on 2008-10-23
Noone has any ideas?

---

### Post by JC Cheloven on 2008-10-23
Sorry, I've been away for a while. Let's see... allow me to think loudly:

You have two physical disks of the same size, 500Gb each, and a third one of 120Gb. All partitions in them are primary.

The first disk has a big linux partition sda1, and two tiny partitions (Mostly useless? Is it sda2 for /boot ?), of type ext and swap.

The second disk is configured in one big partition, sdb1.

The third disk has a moderate ext partition hda1 of about 10GB, a similar sized swap partition hda2 (10GB is a huge amount for swap! what is the size of your ram?), and a big ext partition hda3 that you use for /var.

Only the third disk is bootable, and all partitions in this disk are mounted at startup (as stated in fstab). So I figure out that your problem is that you can't mount the partitions in the two big disks, mainly sda1 & sdb1.

If the above is correct, try the following as a first step (if you haven't already):

--> First of all run "mount -l" to verify that only hda1 and hda3 are mounted. If you see something else mounted (namely sda1 or sdb1), and you still can't access it, umount it (for example "sudo umount /dev/sda1")

--> Have a look on your /media folder (nautilus will do for that purpose). Perhaps you'll see a directory where you used to mount the filesystems in /dev/sda1 and /dev/sdb1. If you do, visit them to verify that you find nothing inside (at a later time, you could delete these folders, as the error message you obtain tells about a problem with the name of the mountpoints). Let's create new mountpoints. For example "sudo mkdir /media/bigdisk_1" and "sudo mkdir /media/bigdisk_2".

--> Now mount the filesystems in these points: "sudo mount /dev/sda1 /media/bigdisk_1". Now try to navigate (either from nautilus or from console) to /media/bigdisk_1. You should access the filesystem in your  big partition of your first disk (sda).

--> If the previous is succesful, you could do similary with your second disk ("sudo mount /dev/sdb1 /media/bigdisk_2"). 

--> If that works, your problem is solved. Perhaps you want then to add instructions in fstab to these partitions to be mounted at startup. 

Fell free to come back to ask if you get stuck ;-)

____________________

---

### Post by Cyric78 on 2008-10-24
I'll try this out tommorow morning, see if that helps...

---

### Post by Cyric78 on 2008-10-24
Well, thanks again man, that fixed the mount issue.. 

How would I go about adding that to fstab? I'm just not sure on what goes where when it comes to editing text docs.. I much rather a pretty gui to do things like that... ;)

---

### Post by JC Cheloven on 2008-10-24
> **Cyric78 said:**
> Well, thanks again man, that fixed the mount issue.. 

How would I go about adding that to fstab? I'm just not sure on what goes where when it comes to editing text docs.. I much rather a pretty gui to do things like that... ;)

You're welcome :-)

As for adding that to fstab: if you do so, your partitions sda1 & sdb1 will be mounted and accesible from startup. I insist on this point just to be sure that it's that you want to do. 

We could do it right now with the info you provided so far, but I'd rather to mount using the UUID's (I think is safer). For that purpose, could you please post the output of
```
sudo blkid
```
Note: It seems that we are very far away. Your morning is my night. That's the main reason for the delay in our answers ;-)

---

