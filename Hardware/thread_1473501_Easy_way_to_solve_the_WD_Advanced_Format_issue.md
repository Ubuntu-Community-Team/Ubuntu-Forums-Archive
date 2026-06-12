---
title: "Easy way to solve the WD Advanced Format issue"
date: 2010-05-05
forum: Hardware
---

### Post by jeditech on 2010-05-05
Recently I bought a WD10EARS 1TB disk with the Western Digital Advanced Format. Then I read several threads concerning the alignment of 4k sectors and the related performance loss. The solutions I have read until now requires quite an effort and understanding of the file system and are still error-prone (e.g. mistakes in calculation of the beginning addresses of the partitions, especially if you want to create multiple partitions)

Now if you have a Windows installation on the computer, there is an easy way to solve the problem, without all the headache. I don't know if anybody has come up with this idea, but it worked perfectly in my case.

1. Connect the disk to your system and boot your existing Ubuntu installation (or use the live-CD or a boot-CD e.g. Parted Magic if Ubuntu is not installed yet)
2. Create the partitions as you like on the disk (I used GParted), all partitions should be created as !!! FAT32 !!!
3. Now boot your Win installation and install the WD Alignment tool. Start the tool and let it align all the partitions on the HD ;) (1 or 2 reboots)
4. Boot Ubuntu again as in step 1
5. Change the partition type to ext2/3/4 or swap (again with GParted). The disk is now ready for Ubuntu installation.

The whole procedure took less than 10 minutes, including the alignment. Performance now is as expected.

Have fun with your new disk.

jeditech

---

### Post by AllGamer on 2011-08-15
this is definitely the best workaround thus far.

using gparted directly to format to ext4 without using the WD aligment software, doesn't work all that great

but as you said, if you first format it as fat32, align it, then change it back to ext4 then it works great

however that's a horrendous tedious task to do, when you need to do it for 20 or more HDDs ... :(

---

