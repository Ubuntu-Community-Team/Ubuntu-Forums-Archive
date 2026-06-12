---
title: "Asus 900 sd card reader problem????"
date: 2009-02-03
forum: Hardware
---

### Post by Zipper-Shut on 2009-02-03
OKay, 

Ive got a problem.

When I bought my new SD Card, I put it in the slot, and no mounting, nor showing of a new item was present.
I left it alone, and just played with my USB Stick instead since that worked rather good.

But now, i'm going to upgrade my PCIe-SSD to the 32GB from SuperTalent.
So, as i was downloading a new linux distro to my USB Drive It told me that it could not write blah blah blah, after 2 1/2 hrs of downloading the distro. I can fix that.... no problem. I hope ;)

But, I have very little space on my PCIe-SSD right now and cannot download another distro without my USB or SD Card.

Basically this is what I am doing. Since the ASUS doesnt have a CD DRIVE.:
I'm downloading a linux distro (preferably ubuntu again) on to my USB DRIVE, then using UNETBOOTIN to transfer all the ISO image to my SD Card. So when I upgrade my "hard drive" I can just install very easily.

My problem is with the SD CARD or SD CARD READER....
I cannot even get the READER to show my SD CARD to MOUNT it... BUT, when I run fdisk -l this is what shows...

> Disk /dev/sda: 1977 MB, 1977614336 bytes
110 heads, 61 sectors/track, 575 cylinders
Units = cylinders of 6710 * 512 = 3435520 bytes
Disk identifier: 0x0002edb3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         576     1931263+   c  W95 FAT32 (LBA)
Partition 1 has different physical/logical endings:
     phys=(240, 109, 61) logical=(575, 70, 8)

Disk /dev/sdb: 4034 MB, 4034838528 bytes
255 heads, 63 sectors/track, 490 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000cbb0a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         462     3710983+  83  Linux
/dev/sdb2             463         490      224910    5  Extended
/dev/sdb5             463         490      224878+  82  Linux swap / Solaris

Disk /dev/sdc: 4009 MB, 4009230336 bytes
124 heads, 62 sectors/track, 1018 cylinders
Units = cylinders of 7688 * 512 = 3936256 bytes
Disk identifier: 0xc7d78881

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        1018     3911796    b  W95 FAT32
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 1, 1) logical=(0, 1, 2)
Partition 1 has different physical/logical endings:
     phys=(486, 254, 63) logical=(1017, 79, 61)
Partition 1 does not end on cylinder boundary.
/dev/sdc2            1018        1019        3436+  83  Linux
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(487, 0, 1) logical=(1017, 79, 62)
Partition 2 has different physical/logical endings:
     phys=(487, 109, 6) logical=(1018, 66, 52)
Partition 2 does not end on cylinder boundary.

By the way when i usually run that code in the terminal it only takes 2 seconds... but when the SD CARD is in the slot it takes about 2-5 minutes.

Can anyone help me....?

I would really appreciate it.

Thank you.

---

### Post by jimv on 2009-02-03
Have you tried repartitioning/formatting your SD card?

---

### Post by Zipper-Shut on 2009-02-03
> **jimv said:**
> Have you tried repartitioning/formatting your SD card?


Thats the thing, the fdisk -l sees it, but i cannot do anything to it...
I will try though.... maybe it will work.

I will let you know. Thanks

---

### Post by Zipper-Shut on 2009-02-03
Let me know if i am doing this right....
> 
pinwyn@pinwyn-laptop:~$ sudo mkfs.vfat -n 'SDCARD' -l /dev/sda
mkfs.vfat 2.11 (12 Mar 2005)
No device specified!
Usage: mkdosfs [-A] [-c] [-C] [-v] [-I] [-l bad-block-file] [-b backup-boot-sector]
       [-m boot-msg-file] [-n volume-name] [-i volume-id] [-B bootcode]
       [-s sectors-per-cluster] [-S logical-sector-size] [-f number-of-FATs]
       [-h hidden-sectors] [-F fat-size] [-r root-dir-entries] [-R reserved-sectors]
       /dev/name [blocks]
pinwyn@pinwyn-laptop:~$ sudo mkfs.vfat -n 'SDCARD' -l /dev/sda1
mkfs.vfat 2.11 (12 Mar 2005)
No device specified!
Usage: mkdosfs [-A] [-c] [-C] [-v] [-I] [-l bad-block-file] [-b backup-boot-sector]
       [-m boot-msg-file] [-n volume-name] [-i volume-id] [-B bootcode]
       [-s sectors-per-cluster] [-S logical-sector-size] [-f number-of-FATs]
       [-h hidden-sectors] [-F fat-size] [-r root-dir-entries] [-R reserved-sectors]
       /dev/name [blocks]


Am i not? I have no clue now....

---

### Post by Zip247 on 2009-02-03
What is your disto...you could use gparted.  Should be under partition editor.

wdecker

---

### Post by Zipper-Shut on 2009-02-03
> **wdecker said:**
> What is your disto...you could use gparted.  Should be under partition editor.

wdecker



Ubuntu 8.10....... I dont see any Partition Editor...

also, i was looking online for answers.... and i did some things....

> pinwyn@pinwyn-laptop:~$ dmesg | tail
[ 5409.576843] end_request: I/O error, dev sda, sector 3862512
[ 5409.576852] Buffer I/O error on device sda, logical block 482814
[ 5589.582805] sd 2:0:0:0: timing out command, waited 180s
[ 5589.582833] sd 2:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 5589.582842] sd 2:0:0:0: [sda] Sense Key : Hardware Error [current] 
[ 5589.582851] sd 2:0:0:0: [sda] Add. Sense: Unrecovered read error
[ 5589.582862] end_request: I/O error, dev sda, sector 3862512
[ 5589.582871] Buffer I/O error on device sda, logical block 482814
[ 6380.781977] FAT: invalid media value (0x06)
[ 6380.781992] VFS: Can't find a valid FAT filesystem on dev sda.


What does this mean.... i dont mean to feel like a newbie...
sorry

---

### Post by Zipper-Shut on 2009-02-03
had to download gparted.....

will try that.



So after downloading gparted it found the SD CARD... had a warning... and i tried to reformat but an error occurred.

what should i do?

delete partition, and start fresh?

---

### Post by Zip247 on 2009-02-04
Deleting the partition and creating a new one is an option.  If you are going to use unetbootin to create a live disk out of the SD, I would create a fat 16 partition.

wdecker

---

### Post by pwyll on 2009-02-04
Where did you get the card?  I had almost exactly the same problems you're describing last year with a 4gb Sandisk I got from eBay--turned out to be a hacked 1gb labeled and sold as a 4gb...

Hope your issue is not the same as mine, but you may want to check into it just to be sure.


Good luck,

Scott

---

