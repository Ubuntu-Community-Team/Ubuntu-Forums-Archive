---
title: "How to Restore grub or use vista bootloader"
date: 2008-12-11
forum: Installation &amp; Upgrades
---

### Post by keypox on 2008-12-11
So the situation is:
1TB samsung (2 Partition 1:vista, 2:Games,downloads etc)
320 Seagate (4 partitions Root, home, Swap, Windows 7)

I had vista then install ubuntu got grub with vista.  Just installed win 7 now all i have is win 7 and vista.  

I tried booting into ubuntu with live cd but could not mount drives. 

Woould try neogrub but dont know how to use it.  How can i find out all the commands for the drives IE: Where things are drive 0 partition 1 etc

---

### Post by dstew on 2008-12-11
I think neogrub is used under EasyBCD, which is a bootloader that works with Vista. See the [EasyBCD site]("http://neosmart.net/dl.php?id=1") and the [neogrub wiki.]("http://neosmart.net/wiki/display/EBCD/NeoGrub")

---

### Post by Mark Phelps on 2008-12-11
How about doing a "sudo fdisk -lu" so we can at least see if the Linux partitions still exist on the second drive.  I would hate to think that "7" removed them, but with MS, you never know.

Also, did you write GRUB to an MBR when you installed it, or did you write it to the Linux boot partition?

---

### Post by cariboo on 2008-12-11
I would suggest using Super Grub Disk to repair grub. It is available here:

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

I've used it several times to repair grub after I,ve done something stupid. :)

Jim

---

### Post by keypox on 2008-12-11
ok thanks guys will do as soon as i get home. 

Would sudo fdisk -lu work on a live disk?  I dont think the drives are mounting.

---

### Post by Partyboi2 on 2008-12-11
> **keypox said:**
> ok thanks guys will do as soon as i get home. 

Would sudo fdisk -lu work on a live disk?  I dont think the drives are mounting.
It should do

---

### Post by keypox on 2008-12-11
> **Mark Phelps said:**
> How about doing a "sudo fdisk -lu" so we can at least see if the Linux partitions still exist on the second drive.  I would hate to think that "7" removed them, but with MS, you never know.

Also, did you write GRUB to an MBR when you installed it, or did you write it to the Linux boot partition?

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xff8b4745

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   163842047    81920000    7  HPFS/NTFS
/dev/sda2       163842048  1953519615   894838784    7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00061753

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63    29302559    14651248+  83  Linux
/dev/sdb2        29302560    89851544    30274492+   5  Extended
/dev/sdb3        89851904   253691903    81920000    7  HPFS/NTFS
/dev/sdb5        29302623    87891614    29294496   83  Linux
/dev/sdb6        87891678    89851544      979933+  82  Linux swap / Solaris

SuperGRub Disk Failed :(

I just followed this [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)  im about to reboot. Hope i didnt lose vista now. BRB

---

### Post by keypox on 2008-12-11
Ok so that above link did "fix" my grub.  But its not part of the MBR?  I say that because my vista bootloader is still there.  And i had to select the boot drive to drive 2/hd1.  And that found grub, but when i select the vista longhorn at the bottom it gives an error.  

I think i need to edit the grub file to point to the right place?  Then i can just set the 2nd drive as the default boot drive.  I think this should work?

Ok soe my menu.lst has this entry
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

which seems right but doesnt work?

---

### Post by keypox on 2008-12-13
bump anyone know why this did work? 

title Windows Vista/Longhorn (loader)
root (hd0,0)
savedefault
makeactive
chainloader +1

I get error 14.  

I tried (hd0,1) as well.  Which didnt work

EDIT: Got it to work.   Using (hd1,0)  Very weird right?  Because the Fdisk showed it being on hd0???  O Well it worked, I guess people should try all combinations if it doesnt work. 

Grub is very easy to work with thanks guys.  Now to try to get that Win 7 added :), should use same command as vista just different hd part combo.

---

