---
title: "Defragger"
date: 2007-09-20
forum: Hardware &amp; Laptops
---

### Post by SonicJMC on 2007-09-20
I know the Linux file systems really don't need defragging. However, my external drives that are frequently used on Windows systems most certainly do. Is there a defragger for FAT file systems that runs in Ubuntu? I also need to be able to defrag shared internal FAT drives on a dual boot system.

---

### Post by dabl on 2007-09-20
> **SonicJMC said:**
> 

Is there a defragger for FAT file systems that runs in Ubuntu? I also need to be able to defrag shared internal FAT drives on a dual boot system.

a. Not that I ever heard of.

b. Why use FAT32 when you can use NTFS?  NTFS is a "journalling" system (albeit not a very good one) and it will survive a crash/hard reboot far better than FAT.  Install the package ntfs-3g, and set up /etc/fstab to mount these partition/drives, and you can be done with most of the problem.  Then use Windows to defrag them (occasionally).  :popcorn:

---

### Post by reckless2k2 on 2007-09-20
look into fsck and fstab. you have options right in fstab and if you read a little up on fsck you can have it handled right in there. depending on how you add your externals to your system, you can run the program from the terminal as well on the mounted usb drives. 

i do believe you can run fsck on vfat. check into it but i think it's int he right direction.

---

### Post by SonicJMC on 2007-09-20
> **dabl said:**
> a. Not that I ever heard of.

b. Why use FAT32 when you can use NTFS?  NTFS is a "journalling" system (albeit not a very good one) and it will survive a crash/hard reboot far better than FAT.  Install the package ntfs-3g, and set up /etc/fstab to mount these partition/drives, and you can be done with most of the problem.  Then use Windows to defrag them (occasionally).  :popcorn:

Some of the systems my drives get used with cannot read NTFS, particularly my Pocket PC, and 2 Macs. Also, some of the Linux machines I use are not mine, so I am not able to enable NTFS support. Obviously, I had reason. Hell, one of my drives is still FAT 16

---

### Post by psusi on 2007-09-20
> **reckless2k2 said:**
> look into fsck and fstab. you have options right in fstab and if you read a little up on fsck you can have it handled right in there. depending on how you add your externals to your system, you can run the program from the terminal as well on the mounted usb drives. 

i do believe you can run fsck on vfat. check into it but i think it's int he right direction.

He asked about a defragger, not a checker.

---

### Post by rsambuca on 2007-09-20
> **SonicJMC said:**
> Obviously, I had reason... Apparently you did, but often that is not the case.  If you hang around these forums helping others too much you find that most people do not have reasons for this sort of thing!

---

### Post by dabl on 2007-09-20
> **rsambuca said:**
> 

 If you hang around these forums helping others too much you find that most people do not have reasons for this sort of thing!

Hah -- 2 points for sambuca!  :lolflag:

---

