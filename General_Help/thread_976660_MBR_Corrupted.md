---
title: "MBR Corrupted"
date: 2008-11-09
forum: General Help
---

### Post by jmarion47 on 2008-11-09
I have a dual boot, XP/Ubuntu(HH) with an apparently corrupted master boot record. When I try to log on to XP (via GRUB), as soon as I choose XP it reboots the system. Ubuntu loads just fine. When I look at my partitions all the sizes are wrong, and I'm unable to access any of my data. 

My partitions were (1Tb SATA):
20Gb (NTFS) XP
20Gb (ext3) Ubuntu
2Gb (pagefile)
850Gb (ext3) file system

I had installed ext2 IFS, and was using the large (850Gb) partition for all files, accessible from both OS'. Then one day I couldn't log on to XP.

Now when I look for my file system all I see is a 200Gb "undefined" partition.

I assume the master boot record is corrupted, and pray there is a way to get back the data. 

I've re-installed XP, but can't access anything else.

How do I get all my data back???

---

### Post by logos34 on 2008-11-09
Try TestDisk:

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

After you restore the partition table, fixboot of NTFS partition like this:

[http://www.cgsecurity.org/wiki/Data_Recovery_Examples#Recovery_of_a_lost_and_damaged_NTFS](http://www.cgsecurity.org/wiki/Data_Recovery_Examples#Recovery_of_a_lost_and_damaged_NTFS)

---

### Post by caljohnsmith on 2008-11-09
> **logos34 said:**
> Try TestDisk:

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

After you restore the partition table, fixboot of NTFS partition like this:

[http://www.cgsecurity.org/wiki/Data_Recovery_Examples#Recovery_of_a_lost_and_damaged_NTFS](http://www.cgsecurity.org/wiki/Data_Recovery_Examples#Recovery_of_a_lost_and_damaged_NTFS)
+1. If you want specific help using testdisk, jmarion47, and if you have your Live CD, boot that, open a terminal (applications > accessories > terminal), and post the output of:
```
sudo fdisk -l
```
Then make sure the Universe repository is enabled in System > Admin > Software Sources, and then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk with the above command, choose "no log", select HDD and "proceed", "Intel", "Analyze", and see what it shows for your HDD and what errors it might give. Then do "quick search", Y/N depending on if you have any Vista partitions, hit enter, and select "Deeper Search" so it does a deeper search, which could take a while. Post the output of that screen if you would like help recovering your partition. :)

---

### Post by jmarion47 on 2008-11-09
This is what I got following a "deeper search" with TestDisk:
```
Disk /dev/sda - 1000 GB / 931 GiB - CHS 375533 102 51
The harddisk (1000 GB / 931 GiB) seems too small! (<1000 GB / 931 GiB)
Check the harddisk size: HD jumpers settings, BIOS detection...

the following partitions can't be recovered:
     Partition     Start       End   size in sectors
Linux          16539 0 1 375549 44 48 1867572312
Linux          16543 0 1 375553 44 48 1867572312
Linux          16544 2 1 375554 46 48 1867572312
Linux          16547 0 1 375557 44 48 1867572312

[continue]
EXT3 Large File Sparse superblock Recover, 956 GB / 890 GiB
```

I also got the following:
```

Disk /dev/sda - 1000 GB / 931 GiB - CHS 375533 102 51
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 * HPFS - NTFS              0   1  1 41930 101 51  218125011
 2 P Sys=72               41931  87 11 369111  88  9 1701990410
 3 P Sys=74               140148   5 27 244718  36 29  543974724
Invalid FAT boot sector
 4 P FAT16 >32M           244718  36 30 375532 101 51  680497765
 4 P FAT16 >32M           244718  36 30 375532 101 51  680497765
Space conflict between the following two partitions
 2 P Sys=72               41931  87 11 369111  88  9 1701990410
 3 P Sys=74               140148   5 27 244718  36 29  543974724
```

---

### Post by TeXtonyx on 2008-11-10
I assume the master boot record is corupted, and pray there is a way to get back the data.
I've tried re-installing XP, but it still just reboots every time 
I select XP from GRUB.
-----------------

Well, if it boots to an grub menu.lst screen that means that grub
has been installed in the MBR. So that is working. Now XP has a
boot sector and that could be corrupted. Sometimes Testdisk can fix
that. You did not reinstall XP. When XP is installed it overwrites
the MBR which removes grub. You would have booted directly to XP
and never seen a grub menu. Then, you have to reinstall grub and
put it back into the MBR if that is how you choose to dual boot.
Even running fixmbr from the XP install disk will overwrite the MBR
and remove you grub boot screen. So I'm not sure what you did.
Reinstalling XP is done from a cd unless you have a OEM hidden partition.

I didn't see you post the result of sudo fdisk -l. 

Invalid FAT boot sector
 4 P FAT16 >32M           244718  36 30 375532 101 51  680497765

---

### Post by jmarion47 on 2008-11-10
TeXtonyx,
clearly I wasn't thinking when I mentioned the grub, so let me re-start:

I initially had a dual-boot with XP on the first partition, Ubuntu on the second, a pagefile partition, and a huge data partition (ext3). I did in fact re-install XP (on the same, first partition as previously), overwriting the grub loader, and re-writing the MBR.

Now I can run XP, but the two ext3 partitions and the pagefile partition appear corrupted. Worse still, the sizes of the partitions appear wrong (listing a 1TB disk as having 1,499.46 GB of space); leading me to believe that it's the partition table that's buggered. 

How do I fix the partition table?

---

### Post by 081103jk on 2008-11-10
&#20852;&#22885;[**&#21271;&#20140;&#25991;&#20214;&#26588;**](http://www.xa2008.cn/Chinese/bjwjg.html)&#12289;[**&#38081;&#26588;**](http://www.xa2008.cn/Chinese/bjtg.html)&#30340;&#29983;&#20135;&#35774;&#35745;&#65306;&#25991;&#20214;&#26588;&#12289;[**&#38081;&#26588;**](http://www.xa2008.cn/Chinese/bjtg.html)&#30340;&#29983;&#20135;&#24037;&#33402;&#65306;&#20852;&#22885;&#21271;&#20140;&#25991;&#20214;&#26588;&#37319;&#29992;&#20808;&#36827;&#30340;&#37240;&#27927;&#12289;&#34920;&#35843;&#12289;&#30967;&#21270;&#12289;&#39034;&#24207;&#21270;&#25240;&#24367;&#12289;&#26080;&#30165;&#28857;&#28938;&#12289;&#39034;&#24207;&#21270;&#21943;&#28034;&#31561;&#24037;&#33402;&#65292;&#22823;&#22823;&#24310;&#38271;&#20135;&#21697;&#30340;&#20351;&#29992;&#23551;&#21629;&#12290;&#23436;&#21892;&#30340;&#21150;&#20844;&#36164;&#26009;&#20648;&#23384;&#31995;&#32479;&#65306;&#20852;&#22885;[**&#21271;&#20140;&#25991;&#20214;&#26588;**](http://www.xa2008.cn/Chinese/bjwjg.html)&#20174;&#29627;&#29827;&#26588;&#12289;&#36164;&#26009;&#26588;&#12289;&#26723;&#26696;&#26588;&#12289;&#26356;&#34915;&#26588;&#21040;&#22120;&#26800;&#26588;&#31561;, &#24418;&#25104;&#20102;&#23436;&#21892;&#30340;&#21150;&#20844;&#36164;&#26009;&#20648;&#23384;&#31995;&#32479;,&#26159;&#24744;&#20648;&#23384;&#21644;&#31649;&#29702;&#25991;&#20214;&#30340;&#26368;&#20248;&#36873;&#25321;&#12290;&#20154;&#24615;&#21270;&#30340;&#35774;&#35745;&#65306;&#20852;&#22885;&#21271;&#20140;&#25991;&#20214;&#26588;&#37319;&#29992;&#20102;&#22269;&#38469;&#36890;&#29992;&#30340;&#26631;&#20934;&#23610;&#23544;&#35774;&#35745;,&#26356;&#20026;&#24744;&#26410;&#26469;&#30340;&#25193;&#23637;&#20570;&#22909;&#20102;&#20805;&#20998;&#30340;&#20934;&#22791;&#12290;&#31526;&#21512;&#20154;&#20307;&#24037;&#31243;&#30340;&#20135;&#21697;&#35774;&#35745;,&#35753;&#20351;&#29992;&#32773;&#26356;&#24863;&#33298;&#36866;&#12290;&#21271;&#20140;&#20852;&#22885;[**&#38081;&#30382;&#25991;&#20214;&#26588;**](http://www.xa2008.cn/Chinese/tpwjg.html)&#21378;&#34935;&#24515;&#30340;&#31069;&#24744;&#36523;&#20307;&#20581;&#24247;&#65292;&#24037;&#20316;&#39034;&#21033;&#65281;&#65281;&#65281;

---

### Post by TeXtonyx on 2008-11-10
I don't know how to fix the partition table. I have some advice in
[with that TestDisk report; I don't understand the Fat16 issue at all;
[http://www.cgsecurity.org/wiki/](http://www.cgsecurity.org/wiki/) (paste the url on one line into browser)
TestDisk_Step_By_Step#Partition_table_recovery ]
case you don't have a backup of your data ext2 partition. You can
try LinuxReader which runs from XP. If LinuxReader is able to mount
the data partition, you can save some data to the XP partition, or if
the Ubuntu live cd is capable of mounting your ext3 data partition,
but both this method and LinuxReader may likely just not work, but
it's worth trying as a last resort. Another thing to consider is that
testdisk has a forum which may be more specialized toward your
problem. Also UBCD and Trinity rescue disks have forums. I haven't 
seen anybody on this forum fix a problem like you have, but maybe
someone will come forth. Testdisk can sometimes fix an XP partition
table problem, which is why I asked about XP, I know that fix.

---

### Post by caljohnsmith on 2008-11-10
jmarion47, if you want help recovering your partition table, it would help if you would also post:
```
sudo fdisk -l
```
Also, from the output you posted in #4, you have only gone to the second scan screen but have not yet done the deep search. Please follow the directions again for doing the "deeper search", and post the output of that final screen.

---

### Post by jmarion47 on 2008-11-10
fdisk returned:
```
&#65279;Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x69205244

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13578   109062505+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2           13578      119522   850995205   72  Unknown
Partition 2 does not end on cylinder boundary.
/dev/sda3           45382       79243   271987362   74  Unknown
Partition 3 does not end on cylinder boundary.
/dev/sda4           79243      121602   340248882+   6  FAT16
Partition 4 does not end on cylinder boundary.

```

The first partition is a new (since crash) install of XP, which is functioning. Everything else is inaccessible. Clearly there is overlap between partitions.

I ran PhotoRec all night to see if I could recover some of the files, and all it gave me were a billion little pieces of chopped up files (generically-named, 1 second .mp3s, text files of random code, etc).

This all leads me to believe my Partition Table is corrupted, but I have no idea how to fix it.

---

### Post by psusi on 2008-11-10
I'd say your data is gone.  By reinstalling XP you made a bad situation far worse.

---

### Post by jmarion47 on 2008-11-10
Wow, that was a useful comment. 
While I fully admit that I don't know how to recover the data YET, I know for a fact that most of it is still on the disk:
It's a terabyte hard drive, the first 20 GB or so was XP, the next 20 or so was Ubuntu, and the remaining 850 GB was data. Having reinstalled XP on the first sector of the disk might not have been the best route, it certainly didn't destroy the majority portion of the disk with the valuable data on it.

---

### Post by jmarion47 on 2008-11-11
TestDisk was able to identify the corrupted partitions, but after clicking "write" to re-write the Partition Table, it made a bad situation worse. Running "Analyze" again, it no longer recognized ANY partition data.

Using a Live CD I was able to run ```
mkfs -n /dev/sda1
```
This gave me a list of 18 superblock backups. Then, using ```
e2fsck -b **98301** /dev/sda1
```I went through all 18, to no avail. Every time it said I had a bad superblock.

So, it looks like I'm really F*cked now.

Thanks anyways to those who gave constructive help. I think I'm going to wipe the drive and start over now :'(

---

### Post by TeXtonyx on 2008-11-11
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#Partition_table_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#Partition_table_recovery)

"This all leads me to believe my Partition Table is corrupted, 
but I have no idea how to fix it."
TestDisk_Step_By_Step#Partition_table_recovery

I sent you this link because I thought it would be helpful to see
pictures along with the very similar instructions that you will get
here. The partition table doesn't have the same function as MFT.

Repair NTFS MFT

"The MFT (Master File Table) is sometimes corrupted. If Microsoft Check Disk (chkdsk) failed to repair the MFT, run TestDisk and in the Advanced menu, select your NTFS partition and choose Repair MFT. TestDisk will try to repair the MFT using MFT mirror, its backup.

If both MFT and MFTMirr are damaged and thus can not be repaired using TestDisk, you might want to try commercial software as Zero Assumption Recovery , GetDataBack for NTFS or Restorer 2000."

I don't think this will work now that you reinstalled XP. On the
link above, towards the very bottom of the pages, in the black
and white dos screenshot, it shows the option [Repair MFT]
I don't think it will hurt to run "Repair MFT" but it is likely
just to restore your current MFT, not the old overwritten one.

I agree with you that there still is a decent chance of you 
getting back your 850GB data drive. By decent, I mean worth 
trying. After TestDisk, the procedure becomes complicated.

-------------------------------------------------------

[http://tldp.org/HOWTO/Partition/recovering.html](http://tldp.org/HOWTO/Partition/recovering.html)
Recovering a Deleted Partition Table

"Below are instructions for manually recovering a deleted partition table. There are utilities such as gpart or TestDisk which can make this task considerably easier. If you are reading this, however, because you have run out of luck, this is what you will have to do:"

One of the requirements is to have another partition as large
as the partition you are trying to rebuild. I think that means
another drive since the partition you want is 850GB. That means
you would rebuild the partition table on another drive. I'm
not sure how this method works out then. In any event it is good
practice to have a backup drive, though it costs $$, a 1TB drive.

There is no simple and reliable method of recovering partition
tables that can be known to work/fix the problem before you try
it. Even resizing partitions isn't 100% reliable. If you look
at the second url, you can see there is quite a bit of learning
often requiring reading documentation. Even the TestDisk
guide in the first url, isn't just click a button and wait, fix.

---

### Post by TeXtonyx on 2008-11-11
I'm not sure the bad superblock problem is catastrophic since
there are backups of the superblock. Maybe too soon to wipe drive.
I hadn't read your latest post when I sent my last post.

[http://www.cyberciti.biz/tips/understanding-unixlinux-filesystem-superblock.html](http://www.cyberciti.biz/tips/understanding-unixlinux-filesystem-superblock.html)
"If this information lost, you are in trouble (data loss) so Linux maintains multiple redundant copies of the superblock in every file system. This is very important in many emergency situation, for example you can use backup copies to restore damaged primary super block. Following command displays primary and backup superblock location on /dev/sda3:
# dumpe2fs /dev/hda3 | grep -i superblock  "

[http://www.cyberciti.biz/faq/recover-bad-superblock-from-corrupted-partition/](http://www.cyberciti.biz/faq/recover-bad-superblock-from-corrupted-partition/)
WARNING! Make sure file system is UNMOUNTED.
Find out superblock location for /dev/sda2:
# dumpe2fs /dev/sda2 | grep superblock
Sample output:

  Primary superblock at 0, Group descriptors at 1-6
  Backup superblock at 32768, Group descriptors at 32769-32774
  Backup superblock at 98304, Group descriptors at 98305-98310
[many more reported not displayed for brevity]

Now check and repair a Linux file system using alternate superblock # 32768:
# fsck -b 32768 /dev/sda2
Sample output:

fsck 1.40.2 (12-Jul-2007)
e2fsck 1.40.2 (12-Jul-2007)
/dev/sda2 was not cleanly unmounted, check forced.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
Free blocks count wrong for group #241 (32254, counted=32253).
Fix? yes

Free blocks count wrong for group #362 (32254, counted=32248 ).
Fix? yes
-----------------------------------------

I've seen Solaris issue this command with the addition switch, -o
fsck -o -b 32768 /dev/sda2

---

### Post by jmarion47 on 2008-11-11
Re:#14
I went through TestDisk and once it recognized parts of the missing partitions I clicked on "write" to write a new partition table. Now I am unable to see any partitions.

-----------------------------------------
# dumpe2fs /dev/sda1 | grep superblock
dumpe2fs: No such file or directory while trying to open /dev/sda1
Couldn't find valid filesystem superblock
-----------------------------------------

# mke2fs -n /dev/sda1
mke2fs 1.41.3 (12-Oct-2008)
could not stat /dev/sda1 --- No such file or directory

the device apparently does not exist; did you specify it correctly?

#mke2fs -n /dev/sda
mke2fs 1.41.3 (12-Oct-2008)
/dev/sda is entire device, not just one partition!
proceed anyway? (y,n) y
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
61054979 inodes, 244190646 blocks
12209532 blocks (5.00%) reserved for the super user
First data blocks=0
7453 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
superblock backups stored on blocks:
32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968, 102400000, 214990848
-----------------------------------------

#e2fsck -f -b 32768 /dev/sda1
returned the same bad superblock error.
I ran through the entire list of alternate superblocks... twice. none seem to work.

---

### Post by jmarion47 on 2008-11-23
Sadly, pragmatism beats determination, and I simply had to wipe the drive in the interest of having a working system again... I never did solve this one, but hopefully some of the tricks here will work for someone. 

Thanks all who tried to help.

---

