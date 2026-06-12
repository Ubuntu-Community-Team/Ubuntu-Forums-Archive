---
title: "please i need help to uninstall ubuntu"
date: 2008-08-12
forum: General Help
---

### Post by pythoran on 2008-08-12
hi evrey one

 i have a big problem with my hp laptop i cant reinstall windows again, let me explain i switched forever from win to linux since one month and every thing is going easy for me i just have a little brother who driving me crazy to put windows again, thank to forger and ryadt yesterday they told me in thsi forum how to format the hard disk inorder to install win because when i try to boot with the cd it doesn't detect any hard drive so i cant' do anything,i tried to format the partition with the ubuntu cd in ntfs mode hoping it will work but same thing please help me te resolve this problem i'm going to throw my litlle brother from the windwo(s)hehe

---

### Post by ByteJuggler on 2008-08-12
Have you changed the boot order in the BIOS to ensure you're actually booting from the hard disk?  (E.g. are you just inserting the CD but in fact still trying to boot off the internal hard disk due to the BIOS boot ordering?)

---

### Post by xodus1 on 2008-08-12
Try using gparted iso, hopefully you still have access to a cd burner.
You can google gparted.iso

---

### Post by pythoran on 2008-08-12
i don't have a problem in booting with the cd neither to resize or delete a partition i just can't reinstall windows xp interface says that windows does not detect any hard drive, i have formate"d all the hard drive ans creat a new partitions 30000 for ext3 and 1000 for the swap the rest i formated it in ntfs mode ok till here but when i try to boot with the xp cd the instlalation process can't go on because i don't know lol

---

### Post by Ryadt on 2008-08-12
> **pythoran said:**
> i don't have a problem in booting with the cd neither to resize or delete a partition i just can't reinstall windows xp interface says that windows does not detect any hard drive, i have formate"d all the hard drive ans creat a new partitions 30000 for ext3 and 1000 for the swap the rest i formated it in ntfs mode ok till here but when i try to boot with the xp cd the instlalation process can't go on because i don't know lol
Hi 
Did you switch from ahci to ata in BIOS?

---

### Post by Mgiacchetti on 2008-08-12
erase the ntfs part, and move the others to the end of the disk so the beginning is empty??

---

### Post by Mgiacchetti on 2008-08-12
and is it sata, do you need sata drivers for setup??

---

### Post by tarps87 on 2008-08-12
Is the xp cd a backup cd or the full xp cd?

---

### Post by Mgiacchetti on 2008-08-13
do you have a floppy?? 
you could try going with a 98 boot floppy and running fdisk and format
then pop the cd in and go.
If its a full xp cd, you *should* be able to do this from there, but again, you may need sata drivers.
Try looking up your model lappy and find out from the manufacturer's site (hp.com) what is needed for drivers.

Also, if this is one of those disks that you made yourself, it probably isnt a full xp cd, just a backup.

You May have to get an OEM version disk of your XP Distrobution, (I had to get an XP MCE 2005 OEM disk from an unnamed source that hosts certian files for people to download using a program that starts with a U and ends with Torrent.)  :)

---

