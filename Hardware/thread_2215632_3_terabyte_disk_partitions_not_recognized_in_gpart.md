---
title: "3 terabyte disk: partitions not recognized in gparted and not mountable"
date: 2014-04-07
forum: Hardware
---

### Post by drmtiede on 2014-04-07
I recently bought a 3tb WD30ezrx disk for storage in an external WD case (the 1,5 tera died) and had quite a lot of trouble with it not beeing recognized, being recognized as 700 gb or 2 tb and os on, so that I decided to use it as a second (temporarily: third) drive in my ACER Aspire with Win7 32bit and Ubuntu 12.04. The setup is with Win on a ssd, Ubuntu quite on the end of a 1,5 tb drive sdb7, the new 3tb one sdc. 
Was succesful in converting in gpt, let Windows create the weird 100-so MB partition at the beginning and greated a 1 MG partition unformatted as grub-boot (from live cd or the sdb7, don't remember). Today I used a gparted-live version 0.2 something boot SD to continue creating partitions and copying partitions (did get a warning reading something about the filetable having to be rewritten because of an error). In detail I testcopied a NTFS data partition to sdc3 and the sdb7 Ubuntu partition and the swap to sdc4 and 5. In Ubuntu sdb7 I ran grub-customizer to include the sdc4 in the boot menu to test it and wrote it to the ssd-mbr. Booted to Windows, data partition ok and accessible. Booted to sdc4 Ubuntu and got a perfect copy of the former sdb7 Ubuntu running, without problem.

But.

But I couldn't find the data partition I copied to the sdc3 and gparted shows unformatted drive ("partition table not recognized" - while being run on a system on sdc itself - paradox! I tried to see with gptdisk what the problem might be and this is the output:


```


GPT fdisk (gdisk) version 0.8.1


Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present


Found valid GPT with protective MBR; using GPT.


Warning! Secondary partition table overlaps the last partition by
4294966385 blocks!
Try reducing the partition table size by 17179865540 entries.
(Use the 's' item on the experts' menu.)
Disk /dev/sdc: 5860533168 sectors, 2.7 TiB
Logical sector size: 512 bytes
Disk identifier (GUID): 5A194EDA-DE20-4CFE-8BA3-9C8ADD24D4EC
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 1565565838
Partitions will be aligned on 8-sector boundaries
Total free space is 452279149 sectors (215.7 GiB)


Number  Start (sector)    End (sector)  Size       Code  Name
   1              34          262177   128.0 MiB   0C01  Microsoft reserved part
   2          264192          266239   1024.0 KiB  EF02  
   3          266240      1113288703   530.7 GiB   0700  
   4      5851037696      5860532223   4.5 GiB     8200  
   5      5813161984      5851037695   18.1 GiB    0700  
acerbig@acerbig-Aspire-M5800-M3800:~$
```

The output states that the secotro size is 512 but gparted-live and Win state the sectors are 4000. 

Needless to say that the partitions are not mountable. Any idea besides reformatting the whole thing?

---

### Post by oldfred on 2014-04-07
I know others have had issues with gpt drives partitioned with Windows.
Often better to use gparted or gdisk.

Did Windows put backup gpt partition table in middle of drive. I have seen where users have posted errors and either gdisk or gparted want to move backup to end of drive where it should be.
If you have overlap then you will have issues and it will not work.

How did you copy data? You can have issues of duplicate UUIDs or GUIDs if not just data copy.

Also some have had issues with some brands of caddy that do not correctly support very large drives.

---

### Post by drmtiede on 2014-04-07
Yes, that was the error i meant, the backup gpt partition table was moved to the end. 
and the overlap is due to this? does "secondary partition table" in the output mean "backup partition table", the one that was moved? I don't quite understand what the overlap warning in the output means. and what about the 512 sector size when it should be 4000?

The partitions were copied by gparted-live, partition to partition, not single files and accessible under windows (at least the ntfs). But as I said, what I find strange is that ubuntu boots form the drive and the partition but gparted within this running ubuntu declares it unreadable. it's like i sit on a branch of a tree and say there is no tree...

So You suggest to start from scrap and to format and write gpt with gparted-live? But don't I need the ominous 128MB microsoft partition to be able to work with the disk under windows?

---

### Post by oldfred on 2014-04-07
Windows needs the reserved partition if you were to install Windows to hard drive. Standard installs of Windows cannot be to an external, but if you were moving drive to an internal drive then you might need it.
 Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

Since I like to have Ubuntu (or some system) installed to every hard drive, I also suggest a 200 to 400MB efi partition at beginning of drive (for UEFI or future use with UEFI) and a 1 or 2 MB unformatted partition with the bios_grub flag for BIOS booting. They are not large and adding them now at beginning of drive may save major reformatting hassles later.
If gparted or gdisk moved backup partition table to end of drive you may just need to shrink last partition.


 repair gpt:
[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html)
last partition overlaps backup partition table
[http://ubuntuforums.org/showthread.php?t=1956173](http://ubuntuforums.org/showthread.php?t=1956173)
Check start & end, delete and recreate without overlap. Backup vitial just in case.
Windows adds system reserved to beginning of data drive
[http://askubuntu.com/questions/337541/how-to-recover-partially-formatted-ext4-partition-testdisk-did-not-help](http://askubuntu.com/questions/337541/how-to-recover-partially-formatted-ext4-partition-testdisk-did-not-help)
GPT (partitioning schema) on the hard disk drive is located in first 34 and last 33 sectors

---

### Post by drmtiede on 2014-04-08
Thank You for the reply. Most of my knowledge comes indeed from the rodsbooks site I read the last days.

However. I gave up trying to use the 3tb it as an external drive, the WD controller has some hardwired commands changing the partition to smaller size as soon as i connect it. So I want to expand my "gaming" computer with the drive. I can play with the drive freely until I fully fix the problem - I would need it only under windows for games and video editing. Ubuntu on the machine is only for rare internet browsing and partition maintenance or system recovery should the need arise. 

So back to my problem: doing some calculus I see that gparted shows the sizes correctly, in GiB and I suppose in sectors:

"Disk /dev/sdc: 5860533168 sectors, 2.7 TiB"

but some lines lower it says:

"First usable sector is 34, last usable sector is 1565565838"

in sectors it is roughly 1/4 of the stated 58... sectors. Has that to do with the wrong sector size (512 instead of 4048)?

This is a point not mentioned in the links you offered, but I found elsewhere before. 

So maybe the overlapping is not to be solved reducing the size of the last (swap) partition, especially because the last two are at the end:

Number  Start (sector)    End (sector)  Size       Code  Name
   1              34          262177   128.0 MiB   0C01  Microsoft reserved part
   2          264192          266239   1024.0 KiB  EF02  
   3          266240      1113288703   530.7 GiB   0700  
   4      5851037696      5860532223   4.5 GiB     8200  
   5      5813161984      5851037695   18.1 GiB    0700  

but the "last usable sector" would be somewhere in non-allocated space on the drive. 

Two distinct problems, one the sector count, the other the sector size seen in gparted under Ubuntu 12.04 (live-gparted saw everything correctly, as I see it)??? Sure the whole thing is becoming purely academic, as I could live with a windows -only readable drive.

---

### Post by oldfred on 2014-04-08
I do not know if it is then showing the 4K sectors or the 512 sectors. Most new large drives are 4K internally but still configured with software as 512, so you have compatiblity with older tools.

Almost all these links are by the same author as the rodbooks site. 

       sudo parted /dev/sda unit s print
or
sudo gdisk -l /dev/sda
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/index.html](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/index.html)
Alignment 2048 sectors Advanced Format drives
[http://askubuntu.com/questions/201164/proper-alignment-of-partitions-on-an-advanced-format-hdd-using-parted](http://askubuntu.com/questions/201164/proper-alignment-of-partitions-on-an-advanced-format-hdd-using-parted)
Technical details - from 2010 so now newer kernel resolve linux issues
[https://ata.wiki.kernel.org/index.php/ATA_4_KiB_sector_issues](https://ata.wiki.kernel.org/index.php/ATA_4_KiB_sector_issues)

 Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
it's 8-sector (4096-byte) alignment
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)
Alignment issues on 4K drives
[http://ubuntuforums.org/showthread.php?t=1635018](http://ubuntuforums.org/showthread.php?t=1635018)



Others have also posted this:
USB adapter may show drive as 1/8 size, use SATA port for 4K drives

---

### Post by drmtiede on 2014-04-09
Thx for extensive literature. I will dog into it next week when I'm away. In the meanwhile I managed to fxxx it up almost completely: used a program (test2fs or something similar) to change the UUID of the copied Ubuntu partition, lost grub, had to reinstall via grub-rescue terminal at startup, windows doesn't boot any more because it can't mount the 3tb any more, gparted live re-arranged the gpt backup, and many little tweaks here and there gave me so many steps backwards that I decided to start from scrap when I come back:
Put the hdd in the craddle (not the extermal case - that didn't work), and let windows do the job, probably w/o installing Ubuntu. If I need it I'll just use the live-usb. 
My wife is already angry enough...

Thank You again.

I'll leave the thread open and write down what I manage to accomplish with the drive.

---

### Post by gedakc on 2014-04-10
GParted 0.2 is extremely old.  Many bugs have been fixed since it was released.  I suggest using the latest GParted Live (currently 0.18.0-1).

---

### Post by drmtiede on 2014-04-10
didn't realize it was sooo old... but it's on a sd-card, so no place to write the date. thx. will try the newer one

---

### Post by gedakc on 2014-04-10
If the partitions are still not recognized when using the latest GParted Live, try double clicking on the "unallocated" space and checking the information dialog to see if there are any warnings or problems.

EDIT:  From a quick look at the initial post, it appears there is/was a problem with the partition table:
> Secondary partition table overlaps the last partition by 4294966385 blocks!

If this problem still exists then it will need to be resolved first before GParted or Parted will be able to work with the partition table.

---

### Post by albywolf on 2014-04-12
I use Kubuntu 12.04 LTS and I too suspect more recent versions of partition managers could be needed to correctly handle some big recent hard drives, in my case I had problems with an Advanced Format 1TB WD Green, the first time I partitioned and formatted it wit KDE Partition Manager all went well, but then I had an afterthought about the size of each partition, and from then on I couldn't get a correct alignment anymore, even creating a totally new partition table the problem remained. I installed GParted and it didn't solve anything (but the Gnome bits it installed so kindly changed some file type associations without asking). Then I tried GParted included in the most recent SystemRescueCD and I could fix almost everything (Disk Utility says ext4 partitions are clean, but NTFS ones aren't, but coming from 12.04 repositories it could suffer from the same problems as other tools with these new drives). But now 12.04's KDE Partition Manager complains, and from the log I saw why, it thinks cylinder alignment should be the right one, and not 4k or MiB. To not have to wait for my next dist upgrade, to 14.04 LTS, to solve the mistery, I think I'll manage from Kubuntu 12.04 just the mount points, but I'll do partition and fs checks from SystemRescueCD. Anyhow, I reinstallled KDE Partition Manager to make a last try with it, just in case, but nothing changed, and despite having proposed and backports repositories enabled, it's one of the programs for which newer versions aren't currently proposed by package managers without upgrading the whole distro.

---

### Post by oldfred on 2014-04-12
Some more info

 last partition overlaps backup partition table
[http://ubuntuforums.org/showthread.php?t=1956173](http://ubuntuforums.org/showthread.php?t=1956173)
Check start & end, delete and recreate without overlap. Backup vitial just in case.

gpt partition table in middle of drive
 launch gdisk, then type x, then type e, then type w to save your changes
[http://askubuntu.com/questions/446991/gparted-claims-whole-hard-drive-is-unallocated-and-gives-warning-about-gpt-table](http://askubuntu.com/questions/446991/gparted-claims-whole-hard-drive-is-unallocated-and-gives-warning-about-gpt-table)

---

