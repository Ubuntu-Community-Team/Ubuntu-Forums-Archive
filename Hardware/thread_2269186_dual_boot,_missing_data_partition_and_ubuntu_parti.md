---
title: "dual boot, missing data partition and ubuntu partition"
date: 2015-03-13
forum: Hardware
---

### Post by ashutoshdhingra on 2015-03-13
Hello, 

Windows Data partition with all my partition is showing blank in the  disk managment and I am not able to change the drive letter [http://www.sevenforums.com/attachments/installation-set...]("http://www.sevenforums.com/attachments/installation-setup/199766d1379307898t-help-partition-not-showing-up-my-computer-capture.png"). 

Please help, all my data is there. Reason for the problem. During  Windows update, I had many other programs open and the sytem ran out of  memory and crashed. On re boot, I showed boot manager missing. I was  able to repair the boot manager problem with windows repair and get  windows to boot but now having this drive issue. Also my linux (its a  dual boot system), is not showing at all and the drive is also missing  or have been merged with the recovery partition. Please help! 

thank you very much      

I am trying with ubuntu 12.04 live usb, and ran

     
sudo fdisk -l

 the output is

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x1048db7f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2   *      207648   276842159   138317256    7  HPFS/NTFS/exFAT
/dev/sda3      1415108608  1465147391    25019392   27  Hidden NTFS WinRE
/dev/sda4       276842222  1415108607   569133193   83  Linux
Partition 4 does not start on physical sector boundary.

Partition table entries are not in disk order

Disk /dev/sdb: 8012 MB, 8012390400 bytes
246 heads, 40 sectors/track, 1590 cylinders, total 15649200 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x74f02dea

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048    15646719     7822336   73  Unknown

Disk /dev/sdc: 2004 MB, 2004877312 bytes
16 heads, 32 sectors/track, 7648 cylinders, total 3915776 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        8064     3915775     1953856    c  W95 FAT32 (LBA)

Disk /dev/sdd: 3932 MB, 3932160000 bytes
1 heads, 62 sectors/track, 123870 cylinders, total 7680000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *          56     7679999     3839972    b  W95 FAT32
ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: LABEL="SYSTEM" UUID="E28E050E8E04DCC3" TYPE="ntfs" 
/dev/sda2: UUID="1E8AD6E48AD6B80B" TYPE="ntfs" 
/dev/sda3: LABEL="SAMSUNG_REC" UUID="3EC6100FC60FC5DD" TYPE="ntfs" 
/dev/sdc1: LABEL="UUI" UUID="1418-1D3D" TYPE="vfat" 
/dev/sdd1: LABEL="GPARTED" UUID="5222-A811" TYPE="vfat" 
ubuntu@ubuntu:~$ ^C
ubuntu@ubuntu:~$ 


Gpart is showing on 698  GB with 

/dev/sda1 ntfs for media system 100 MiB
/dev/sda2 ntfs 131 GiB - boot (this is windows)
/dev/sda4 unknown  542 GiB (I need to recover this data)
/dev/sda3 ntfs samsung recovery

---

### Post by weatherman2 on 2015-03-14
What files system was sda4?  NTFS?  ext4?  Anything special about it?  Was it a Windows dynamic disk?  Encrypted?

If NTFS, try a file recovery program like Recuva.  Otherwise, try testdisk.

---

### Post by ashutoshdhingra on 2015-03-14
thanks for your response, it my data partition from windows. Recuva is not working, displaying can not read file system.

---

### Post by ashutoshdhingra on 2015-03-14
Below is infomation obtained from running testdisk


Disk /dev/sda - 750 GB / 698 GiB - CHS 91201 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 P HPFS - NTFS              0  32 33    12 223 19     204800 [SYSTEM]

Bad relative sector.
 2 * HPFS - NTFS             12 236  1 17232 159 63  276634512

Bad relative sector.
 3 P Windows RE(store)    88086 111 26 91201  52 51   50038784
No ext2, JFS, Reiser, cramfs or XFS marker
 4 P Linux                17232 160 63 88086 111 25 1138266386
 4 P Linux                17232 160 63 88086 111 25 1138266386



*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
>[Quick Search]  [ Backup ]

---

### Post by Bucky Ball on 2015-03-14
This is your issue, last line in bold:

```
Device Boot Start End Blocks Id System
/dev/sda1 2048 206847 102400 7 HPFS/NTFS/exFAT
/dev/sda2 * 207648 276842159 138317256 7 HPFS/NTFS/exFAT
/dev/sda3 1415108608 1465147391 25019392 27 Hidden NTFS WinRE
/dev/sda4 276842222 1415108607 569133193 83 Linux
**Partition 4 does not start on physical sector boundary.**
```

You have overlapping partitions. Looks like Windows tried to eat the unknown Linux EXT partition when it ran out of disk space and got hungry! ;)

You might see what you can dig up [here]("https://duckduckgo.com/?q=Partition+does+not+start+on+physical+sector+boundary"). Hopefully someone who knows the fix for this will jump in. Good luck.

---

### Post by oldfred on 2015-03-14
The physical sector boundary means its start is not divisible by 8. You must not have created partition with newer partition tools that support newer 4K drives or SSDs. But Windows since Windows 7 and about a year later all Linux tools changed to start on sector 2048 and use correct rounding on new partitions.

       First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
it's 8-sector (4096-byte) alignment
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)
Alignment issues on 4K drives
[http://ubuntuforums.org/showthread.php?t=1635018](http://ubuntuforums.org/showthread.php?t=1635018)

If sda4 was a NTFS partition, it looks like you overwrote it with a Linux type partition?

---

### Post by ashutoshdhingra on 2015-03-14
Dear all, 

thank you very much for your kind replies. Actually, I do not understand much. I am a Biology student and want to know how can I recove my data. I do have back from 2 months back but not very recent work. Is there a tool that I can use to get the data out. Shall I take out the HDD and try on another system and what software tools would I need for it. 

Please help. 

Thanks a lot!

---

### Post by oldfred on 2015-03-14
Go back to Post #2, those that use Windows seem to recommend it the most, particularly for NTFS partitions.

Otherwise testdisk and photorec if you want Linux tools.

---

