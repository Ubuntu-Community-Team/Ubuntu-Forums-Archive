---
title: "Overlapping partitions on a dual-booting Dell..."
date: 2008-09-06
forum: General Help
---

### Post by Karpah on 2008-09-06
(I've posted this message previously on the Dell board, but this board seems to get a lot more traffic, so I'm posting it here as it's not a Dell-specific question anyway... if I'm in the wrong, just delete this message.)

A couple of months ago I purchased a Dell Inspiron 1525 that came pre-loaded with Vista. I wanted Ubuntu on it as well, so I had a friend do some partitioning and I installed Hardy (Desktop version) on it. I still have all the Dell partitions and Vista as well.

Fast forward to now and I wanted to adjust the partitions, to make the Ubuntu one bigger and the Vista one smaller (and also possibly make another for shared data). I tried to use gparted for this and it said I had a hard drive of unallocated space, because of overlapping partitions.

Running fdisk -l gives me the following:

```

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x80000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *       14267       14594     2620416    c  W95 FAT32 (LBA)
/dev/sda2               9        1314    10485760    7  HPFS/NTFS
/dev/sda3   *        1315        9111    62629402+   7  HPFS/NTFS
/dev/sda4            9112       14594    44035158+   f  W95 Ext'd (LBA)
/dev/sda5           14267       14594     2620416   dd  Unknown
/dev/sda6            9112        9372     2096419+  82  Linux swap / Solaris
/dev/sda7            9373       14266    39311023+  83  Linux

Partition table entries are not in disk order

```

I don't know much what it means, but I can see the overlap between sda1, sda4 and sda5. Doing a quick forum search leads me to testdisk, which gives me following output for testdisk /list:

```

Disk /dev/sda - 120 GB / 111 GiB - CHS 14593 255 63, sector size=512

Disk /dev/sda - 120 GB / 111 GiB - CHS 14593 255 63
     Partition			Start        End    Size in sectors
 1 * FAT32 LBA            14266 230 45 14593  33 32    5240832 [MEDIADIRECT]
 2 P HPFS - NTFS              8   8  1  1313 114 17   20971520 [beta]
 3 * HPFS - NTFS           1314   0  1  9110 254 63  125258805 [alpha]
 4 E extended LBA          9111   1 62 14593  33 32   88070317
Only one partition must be bootable
Space conflict between the following two partitions
 4 E extended LBA          9111   1 62 14593  33 32   88070317
 1 * FAT32 LBA            14266 230 45 14593  33 32    5240832 [MEDIADIRECT]
 5 L Sys=DD               14266 230 45 14593  33 32    5240832
   X extended              9111   1 63  9371 254 63    4192840
 6 L Linux Swap            9111   2  1  9371 254 63    4192839
   X extended              9372   0  1 14265 254 63   78622110
 7 L Linux                 9372   1  1 14265 254 63   78622047

```

alpha: my Vista partition
beta: Dell recovery partition (should keep this one!)

I'm hesitant to just accept everything testdisk offers me on an analyze because it offers me this:

```

Disk /dev/sda - 120 GB / 111 GiB - CHS 14594 255 63
     Partition               Start        End    Size in sectors
* FAT16 >32M               0   1  1     7 254 63     128457 [DellUtility]
P FAT32 LBA                8   0  1  4185 254 63   67119570 [NO NAME]
P Linux Swap            9111   2  1  9371 254 40    4192816
L Linux                 9372   1  1 14265 254 56   78622040
L FAT32 LBA            14266 230 45 14593  33 32    5240832 [MEDIADIRECT]

```

where I believe [NO NAME] is my former alpha partition (but if I press p to list files, it says the filesystem is damaged), and beta has disappeared entirely! And DellUtility didn't even turn up in the previous listings but I sense I need it too..

How can I get out of this situation with the least amount of damage? :confused: And is there some Linux tool I can run that will back up the entire hard drive, all the partitions, before I start doing anything?

Hoping anyone can help,
Rebecca

ps. I asked the same friend who did the initial partitioning to have a look at it, and he insisted either I had damaged it, or I had a failing hard drive, so no help there :(

---

### Post by caljohnsmith on 2008-09-06
You didn't say what partition editor your friend used, but obviously your partition table is munged at this point, so most likely it was your friend's fault and not yours. But regardless, you have a good chance of fixing it with testdisk, but you need to have testdisk do a "deep search" through your entire HDD. Here's essentially what you would do:

At the testdisk main screen, select "no log", select HDD and "proceed", "Intel", "Analyze", then do "proceed", "Y" to find Vista partitions, and see if it finds your Vista partition. Hit enter and select "search!" so testdisk does its deeper search which will take a while. When it finds them, if you select them and hit "P" you should be able to see the contents of the partition, so that will help us figure out which partitions are which.

Once testdisk finds all your partitions, post the results so we can help you sort through them. And let us know what partitions you think are valid. I'm guessing you have the following partitions:
[LIST=1]
[*]Dell backup/recovery
[*]Vista
[*]Ubuntu main partition
[*]Ubuntu swap
[/LIST]
Do you have any additional partitions, maybe for data? 

Also, testdisk only tries to fix your HDD's partition table which is in the master boot record (MBR), so it won't change the rest of your HDD; therefore, if you want to backup your entire HDD that is fine, but I don't think it is absolutely necessary at this point. What I would recommend doing is backing up your HDD's partition table, so you can always get back to the point where you started (even though the partition table is corrupt at this point):
```
sudo dd if=/dev/sda of=MBR.bin bs=512 count=1
```
That will save a file "MBR.bin" to the directory you are currently in. And make sure "sda" is indeed your HDD. Anyway, let me know how it goes. :)

---

### Post by Karpah on 2008-09-06
Thanks for a quick and informative reply :)

I believe my friend used gparted, which makes it even more baffling that gparted can now not read the partitions it itself created, and I'm positive I have not touched the partitions myself. Curiouser and curiouser. Anyways.

I tried to follow the exact sequence of instructions for testdisk, but did not get a '"Y" for Vista partitions' step, it went straight into scanning. Did I miss something? :/

Right now I'm not sure if I need to keep all the Dell junk that came pre-installed, but for now I think I should concentrate on fixing the table and I can always nuke them later. So I should have:

1) DellUtility
2) Dell recovery ('beta')
3) Dell MediaDirect
4) Vista + data ('alpha')
5) Ubuntu + data 
6) swap

and a 7) shared data can be implemented later.

The results of a deep search of testdisk are as follows:

```

Disk /dev/sda - 120 GB / 111 GiB - CHS 14594 255 63
     Partition               Start        End    Size in sectors
* FAT16 >32M               0   1  1     7 254 63     128457 [DellUtility]
D FAT32 LBA                8   0  1  4185 254 63   67119570 [NO NAME]
D HPFS - NTFS              8   8  1  1313 114 17   20971520 [beta]
D HPFS - NTFS           1313 114 18  9110 114  5  125258793
D HPFS - NTFS           1314   0  1  9110 254 51  125258793 [alpha]
D HPFS - NTFS           1314   0 13  9110 254 63  125258793
P Linux Swap            9111   2  1  9371 254 40    4192816
D Linux                 9372   1  1 14265 254 56   78622040
D Linux                 9373   2  1 14267   0 56   78622040
D Linux                 9380   1  1 14273 254 56   78622040
D FAT32 LBA            14266 230 45 14593  33 32    5240832 [MEDIADIRECT]

```

Where pressing P on [NO NAME] says 'No file found, filesystem seems damaged.' and pressing P on [beta] gave me a segmentation fault and testdisk exited :(

I'll run the deep search again and check the contents of the rest of the partitions... but they look OK on the surface (though I don't know why they're all duplicated and marked as deleted!)

-Rebecca

---

### Post by caljohnsmith on 2008-09-06
What version of testdisk are you running? On any of the testdisk screens it usually says at the top. And just to clarify, are you running testdisk from the Ubuntu Live CD, or are you using testdisk from some other rescue CD? 

When you say you have the following partitions:
[LIST=1]
[*]DellUtility
[*]Dell recovery ('beta')
[*]Dell MediaDirect
[*]Vista + data ('alpha')
[*]Ubuntu + data
[*]swap
[/LIST]
Do you remember by chance which ones were part of the extended partition? In other words, which partitions were logical?

---

### Post by Karpah on 2008-09-06
I'm running testdisk version 6.8, August 2007. The one piece of advice my partitioning friend gave me was to download Ubuntu Rescue Remix, so I've been using that.

And I don't know which partitions were what type, unfortunately :(

(The testdisk is still deep-searching for the second time so I can check the rest of the partitions and their contents. I'm at least heartened to see alpha and beta have turned up now. I kinda like them. But if all else fails, they can go, as long as Ubuntu stays <.<)

---

### Post by macabro22 on 2008-11-14
Hi I also lost all my partitions. 

Here's some more info:

sudo fdisk -l gives

```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          10       80293+   6  FAT16
/dev/sda2              11        4188    33559785    c  W95 FAT32 (LBA)
/dev/sda3   *       18876       19202     2620416    c  W95 FAT32 (LBA)
/dev/sda4           19203       38914   158336640    f  W95 Ext'd (LBA)
/dev/sda5           23201       37956   118527536   83  Linux
/dev/sda6           37957       38586     5060432   82  Linux swap / Solaris
/dev/sda7           38587       38914     2620416    c  W95 FAT32 (LBA)

```

I am running testdisk's  deep search now and will post the results later.

 I am at exactly the same situation. linux and the partitions following it (sda 4 to 7) are extended logical partitions. I suppose 5, 6 and 7 are into 4.I also have the dell recovery wich I deleted form the vista partitioner which screwed up the partition table and now thats where i stand.

I was able to mount and backup the entire ubuntu system. Now, could you guys please help me out using testdisk to get the partition table fixed and my windows system back?

Thanks

---

