---
title: "Resizing and Deleting Partitions."
date: 2008-12-08
forum: Hardware
---

### Post by Ratchet-- on 2008-12-08
First, It is my sincere apologies if this has already been asked, or this is in the wrong category.

Second, here's where we get down to business ;D

I had an ubuntu, 8.04(Gnome) I believe to be exact. This particular ubuntu had a problem with my wireless, so I restored my entire computer to rid of it. Then, my father found a newer version, 8.10 Gnome, and I installed that. Now I have a working wireless. (Thanks developers for this!).

However, I notice in 'Places' there's my File System (Ubuntu Files), but there's also a 37.3GB media and a 20.1 GB media. When I first installed ubuntu (the 8.04) there was only a File System, and the GB Media which was my windows half. So what I am thinking is one of them would be the partition left behind from when I restored to rid of the broken ubuntu. So, I was wondering if I could delete one of the Media's, and possibly add the space I lose to the Ubuntu partition.

To help with the 'Media' drives, the 37 GB Media has windows files, and the 20GB has left over ubuntu files, therefore the 20 I should delete, correct?

---

### Post by Ratchet-- on 2008-12-10
I've gotten GPARTED, but I'm having trouble deleting the one I want because it tells me 'logiccally unmount any driver bigger than 5' and I'm trying to delete 5.. -.-

---

### Post by jman6495 on 2008-12-10
Your Going To Need To Find Out Which Is Which And When You Have,Yes
I Would Think You Should Delete

BUT
You Will Not Be Able To Run Gparted In Your Ubuntu.
It Wont Let you Cause Your Changing The Drive Your On,
You Must Insert The Live Cd And From There You Can Access GParted From The Menu There.
Good Luck
   Jman6495
"Vista With 512MB Of Ram...Or A Tortoise Pulling A Mini":p

---

### Post by logos34 on 2008-12-10
you have to unmount the partition before you can delete it.

Better post your disk layout.  In a terminal run:

sudo fdisk -l

and

cat /etc/fstab

---

### Post by Ratchet-- on 2008-12-10
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4535    36427356    7  HPFS/NTFS
/dev/sda2            4536        8398    31029547+   5  Extended
/dev/sda3            8399        9729    10691257+   c  W95 FAT32 (LBA)
/dev/sda5            5841        8286    19647463+  83  Linux
/dev/sda6            8287        8398      899608+  82  Linux swap / Solaris
/dev/sda7            4536        5778     9984334+  83  Linux
/dev/sda8            5779        5840      497983+  82  Linux swap / Solaris





I need to rid of sda5. You say access it in menu of live, but I fail to see gparted anywheres on the live cd. may I get directions for this?

---

### Post by logos34 on 2008-12-11
> **Ratchet-- said:**
> Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4535    36427356    7  HPFS/NTFS
/dev/sda2            4536        8398    31029547+   5  Extended
/dev/sda3            8399        9729    10691257+   c  W95 FAT32 (LBA)
[COLOR="Red"]/dev/sda5            5841        8286    19647463+  83  Linux
/dev/sda6            8287        8398      899608+  82  Linux swap / Solaris[/COLOR]
/dev/sda7            4536        5778     9984334+  83  Linux
/dev/sda8            5779        5840      497983+  82  Linux swap / Solaris


I need to rid of sda5. You say access it in menu of live, but I fail to see gparted anywheres on the live cd. may I get directions for this?

you don't need to boot the live cd.  Just do

sudo umount /dev/sda5

or

sudo umount /media/disk

or wherever it's mounting and then use gparted to delete it.  

sudo apt-get install gparted

gksudo gparted

Get rid of the old swap too (I assume its sda6--doublecheck).  

Remove those entries from /etc/fstab so the system won't try to mount them.

---

