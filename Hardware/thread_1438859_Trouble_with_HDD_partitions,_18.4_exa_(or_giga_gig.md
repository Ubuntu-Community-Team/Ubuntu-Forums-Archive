---
title: "Trouble with HDD partitions, 18.4 exa (or giga giga) bytes of unallocated space?"
date: 2010-03-25
forum: Hardware
---

### Post by Ncshipman on 2010-03-25
Hi,

Firstly apologies I'm a complete beginner.

History
I was dual booting vista and ubuntu 9.10.  Ubuntu told me my hard drive was not very well.  So I bought a new one and an external HDD enclosure.  My goal was to get windows and ubuntu onto the new HDD.  First I backed up my data, then I installed ubuntu on the new disk in case things went wrong.  Then things went wrong.  The vista recovery partition kept giving me blank error messages.  I read somewhere I had to repair media direct.  I used dell mediadirect repair utility it seemed to work fine.

Problem
I turned off my computer but when I turned it on again it said "2 active partitions" and wouldn't do anything else.

So I swapped HDDs putting my old one in the enclosure and the new one with ubuntu in my laptop.  I thought I have too many partitions so I will delete ubuntu (on the old disk).  I tried to do so with Disk Utility but it errored saying "Error deleting partitions-you can't have overlapping partitions".  So I installed gparted.  But that just sees my entire old HD as unallocated space.

Other weird things
My old 160GB hard drive thinks it has 2x18.4 Exa bytes of unallocated space, one within a 28GB ubuntu partition.
Other unexpected Partitions (esp. 2.7GB NTFS inside what I thought was my 28GB ubuntu partition)

160 GB
-OS 2.7GB NTFS
-Recovery 11GB NTFS
-OS 121GB NTFS
-28GB Extended
          {-OS 2.7GB NTFS}
          {-24GB Filesystem ext4}
          {-1.1GB Swap Space}
          {-18446744071GB Free Unallocated Space}
-18446744071GB Free Unallocated Space

Sorry its so long I don't know what's important.  Any ideas anyone?

---

### Post by srs5694 on 2010-03-25
Post the results of typing:

```

sudo fdisk -l

```

This will give a much clearer and more precise indication of how your disk is partitioned.

---

### Post by Ncshipman on 2010-03-25
Thanks, ok...

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device____Boot____Start____End_______Blocks_____Id____System
/dev/sdb1__*_______19131___19458_____2620416___7____HPFS/NTFS
/dev/sdb2__________24_______1329______10485760__7____HPFS/NTFS
/dev/sdb3__*_______1329_____16031____118091797__7____HPFS/NTFS
/dev/sdb4__________16032____19458____27519986___f_____W95 Ext'd (LBA)
/dev/sdb5__________19131____19458____2620416____dd____Unknown
/dev/sdb6__________16032____18997____23824363+__83___Linux
/dev/sdb7__________18998____19130____1068291____82___     Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by srs5694 on 2010-03-25
Somewhere along the line your /dev/sdb5 has been duplicated as /dev/sdb1. It looks like this duplicate /dev/sdb1 may have replaced another /dev/sdb1, since there's an unused gap at the very start of the disk. Also, the type code (dd) on /dev/sdb5 is strange. Unless you know what it is, it's almost certainly wrong. You could try "blkid /dev/sdb5" to identify what sort of filesystem it contains.

In any event, here's how I recommend you proceed:


[list=1]
[*]Back up your existing partition table with dd. Type "sudo dd if=/dev/sdb of=sdb-backup.mbr bs=512 count=1". Be *very careful* with this command; a typo could have devastating consequences, particularly if you mix up the if= and of= parameters.
[*]Copy the backup file you made in step #1 to some safe medium that's not on either of your hard disks -- a floppy disk, USB flash drive, or CD-R will do nicely. If the procedure I describe makes things worse, you'll be able to reverse the backup process to get back to where you are now.
[*]Launch fdisk on /dev/sdb by typing "sudo fdisk /dev/sdb". You'll now be able to edit your partition table.
[*]Type "p" to verify that you're working on the correct disk.
[*]Type "d". When prompted for a partition number, type "1"
[*]Type "p" to verify that the spurious /dev/sdb1, starting at cylinder 19131 and ending at cylinder 19458, is gone, and that all the other partitions, including /dev/sdb5, remain as they're defined now.
[*]You may optionally use the "t" command to change the type code on /dev/sdb5. If the type code should be what was on /dev/sdb1, it should be 7; however, I can't know that this is correct. It could be that it should be something else entirely. If you used "blkid" on the partition, that may have given you some useful information. If you're uncertain, you may want to leave it as-is for the moment. Post back if you want more advice.
[*]If all seems OK, type "w" to write your changes.
[/list]


You should now be able to use the disk normally; however, there's still the issue of that presumed missing /dev/sdb1 partition. Windows might have problems booting without it. If so, your safest bet is to use a utility called testdisk to recover it; however, if that fails you could try fdisk again. Use "n" to create a new primary partition from cylinder 1 through 23, then use "t" to give it a type code of 27. That will *probably* create the correct partition, but I can't promise it will work.

If you left /dev/sdb5 alone, you can launch fdisk again to change its type code in the future, should you figure out what the partition is.

---

### Post by Ncshipman on 2010-03-25
Awesome sounds like a plan :-)

blkid /dev/sdb5, gives:
/dev/sdb5: UUID="AA48D3B048D37991" LABEL="OS" TYPE="ntfs"

My guess is these partitions are Dell Media Direct related, but thats just a guess and how I got two helpings...???

I did the rest of the stuff I'll plug it in and see if it works.  Thanks!

---

### Post by srs5694 on 2010-03-25
That was my suspicion concerning /dev/sdb5. It should probably be type 27; that's the type code for the Windows Recovery Environment partition, which often comes just before the Windows partition on pre-installed systems. It's conceivable it should be type 07 or something else, though.

---

### Post by Ncshipman on 2010-03-26
Ok now it gets slightly further.  It shows me the Dell logo then it says "Loading PBR for descriptor 3... done" then repeats ad infinitum.  I'm trying testdisk like you said but its going pretty slowly.  So far I have...

Disk /dev/sdb - 160 GB / 149 GiB - CHS 19458 255 63
Analyse cylinder  4518/19457: 23%


FAT16 >32M___0_1_1_____22_254_63_____369432___[DellUtility]
FAT32 LBA __23_0_1___4200_254_63___67119570___[NO NAME]

---

### Post by Ncshipman on 2010-03-26
I think I've just understood what all these numbers mean.  Testdisk has already found the missing partition but is being really slow with the other ones?  The testdisk cylinder numbers seem to be one out compared to fdisk but I'm guessing thats a numbering convention, one starts counting at 0 the other at 1?

no ignore this I don't get it after all

---

### Post by srs5694 on 2010-03-26
Actually, you do get it. The cylinder/head/sector (CHS) numbering scheme is weird. Don't worry too much about it, unless you want to have a visit from the nice people who'll fit you with a coat with sleeves that fasten in back. ;) It looks like testdisk has found your missing partition ("DellUtility"). I'd just let it run until it's satisfied, then have it rebuild that one lost partition.

---

### Post by Ncshipman on 2010-03-26
Ok I'm all sorted.  Unfortunately testdisk seemed to get stuck, someone told me this was probably because the HD was damaged which was why I was getting problems in the first place.  I took it to the I.T. technician in college and he managed to sort me out by copying the recovery partition to my new hard drive and somehow eventually reinstalling windows from there (I don't think it was easy).  Almost a shame I liked the other method but at least its working.  Thanks for all your help!

---

