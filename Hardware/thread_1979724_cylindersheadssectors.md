---
title: "cylinders/heads/sectors"
date: 2012-05-14
forum: Hardware
---

### Post by Randymanme on 2012-05-14
[SIZE=3]Is there an app for Ubuntu that will identify the C/H/S of my hard drive (I want it for Testdisk – re: [http://ubuntuforums.org/showthread.php?t=1978570](http://ubuntuforums.org/showthread.php?t=1978570)).  For the computer in my signature, the hard drive is a one terabyte ATA WDC WD10EADX-22T.

I've done about 3 hours of googling this topic and, so far, I just keep getting dumber.  My computer's BIOS says LBA/Large Mode, and 16 sectors.  Am I to understand that   all hard drives larger than 8.4 Gbs are [COLOR=#000000][FONT=Arial][SIZE=2]16383 cylinders, 16 heads, and 63 sectors?[/SIZE][/FONT][/COLOR][/SIZE]
 

 [SIZE=3][COLOR=#000000][FONT=Arial][SIZE=2]Fdisk -l's  “255 heads, 63 sectors/track, 121601 cylinders,” is almost the same as TestDisk's  “CHS 121602 255 63,” which I know is not correct (testdisk numbers).  Is there static figures some place that remain the same regardless of what's written to disk?[/SIZE][/FONT][/COLOR][/SIZE]
 

 [SIZE=3][COLOR=#000000][FONT=Arial][SIZE=2]As always, your help and advice are much appreciated.  Thank you.[/SIZE][/FONT][/COLOR][/SIZE]
 

 

 [SIZE=3][COLOR=#000000][FONT=Arial][SIZE=2]~$ sudo fdisk -l [/SIZE][/FONT][/COLOR][/SIZE]
 [SIZE=3][COLOR=#000000][FONT=Arial][SIZE=2][sudo] password for randymanme:  [/SIZE][/FONT][/COLOR][/SIZE]
 [SIZE=3][COLOR=#000000][FONT=Arial][SIZE=2] [/SIZE][/FONT][/COLOR][/SIZE]
 [SIZE=3][COLOR=#000000][FONT=Arial][SIZE=2]Disk /dev/sda: 1000.2 GB, 1000204886016 bytes [/SIZE][/FONT][/COLOR][/SIZE]
 [SIZE=3][COLOR=#000000][FONT=Arial][SIZE=2]255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors [/SIZE][/FONT][/COLOR][/SIZE]
 [SIZE=3][COLOR=#000000][FONT=Arial][SIZE=2]Units = sectors of 1 * 512 = 512 bytes [/SIZE][/FONT][/COLOR][/SIZE]
 [SIZE=3][COLOR=#000000][FONT=Arial][SIZE=2]Sector size (logical/physical): 512 bytes / 512 bytes [/SIZE][/FONT][/COLOR][/SIZE]
 [SIZE=3][COLOR=#000000][FONT=Arial][SIZE=2]I/O size (minimum/optimal): 512 bytes / 512 bytes [/SIZE][/FONT][/COLOR][/SIZE]
 [SIZE=3][COLOR=#000000][FONT=Arial][SIZE=2]Disk identifier: 0xe90be90b [/SIZE][/FONT][/COLOR][/SIZE]
 [SIZE=3][COLOR=#000000][FONT=Arial][SIZE=2] [/SIZE][/FONT][/COLOR][/SIZE]
 [COLOR=#000000]   [SIZE=3][FONT=Arial][SIZE=2]Device Boot      Start         End      Blocks   Id  System [/SIZE][/FONT][/SIZE][/COLOR]
 [SIZE=3][COLOR=#000000][FONT=Arial][SIZE=2]/dev/sda1   *          63    36853095    18426516+   7  HPFS/NTFS/exFAT [/SIZE][/FONT][/COLOR][/SIZE]
 [SIZE=3][COLOR=#000000][FONT=Arial][SIZE=2]/dev/sda2        36853110    37061942      104416+   7  HPFS/NTFS/exFAT [/SIZE][/FONT][/COLOR][/SIZE]
 [SIZE=3][COLOR=#000000][FONT=Arial][SIZE=2]/dev/sda3        37062656   319743984   141340664+   7  HPFS/NTFS/exFAT [/SIZE][/FONT][/COLOR][/SIZE]
 [SIZE=3][COLOR=#000000][FONT=Arial][SIZE=2]/dev/sda4       319757760  1953536129   816889185    f  W95 Ext'd (LBA) [/SIZE][/FONT][/COLOR][/SIZE]
 [SIZE=3][COLOR=#000000][FONT=Arial][SIZE=2]/dev/sda5       332328960   516440063    92055552   83  Linux [/SIZE][/FONT][/COLOR][/SIZE]
 [SIZE=3][COLOR=#000000][FONT=Arial][SIZE=2]/dev/sda6       516442112   528490479     6024184   82  Linux swap / Solaris [/SIZE][/FONT][/COLOR][/SIZE]
 [SIZE=3][COLOR=#000000][FONT=Arial][SIZE=2]/dev/sda7       528492544  1156065279   313786368   83  Linux [/SIZE][/FONT][/COLOR][/SIZE]
 [SIZE=3][COLOR=#000000][FONT=Arial][SIZE=2]/dev/sda8      1156075520  1209481215    26702848   83  Linux [/SIZE][/FONT][/COLOR][/SIZE]
 [SIZE=3][COLOR=#000000][FONT=Arial][SIZE=2]/dev/sda9      1209483264  1222066159     6291448   82  Linux swap / Solaris [/SIZE][/FONT][/COLOR][/SIZE]
 [SIZE=3][COLOR=#000000][FONT=Arial][SIZE=2]/dev/sda10     1222068224  1513129975   145530876   83  Linux [/SIZE][/FONT][/COLOR][/SIZE]
 [SIZE=3][COLOR=#000000][FONT=Arial][SIZE=2]/dev/sda11     1513132032  1558945791    22906880   83  Linux [/SIZE][/FONT][/COLOR][/SIZE]
 [SIZE=3][COLOR=#000000][FONT=Arial][SIZE=2]/dev/sda12     1558947840  1621862399    31457280   83  Linux [/SIZE][/FONT][/COLOR][/SIZE]
 [SIZE=3][COLOR=#000000][FONT=Arial][SIZE=2]/dev/sda13     1621864448  1953503231   165819392   83  Linux [/SIZE][/FONT][/COLOR][/SIZE]

---

### Post by Randymanme on 2012-05-14
[http://forums.linuxmint.com/viewtopic.php?f=190&t=102102&p=579571#p579571](http://forums.linuxmint.com/viewtopic.php?f=190&t=102102&p=579571#p579571)         [Re: cylinders/heads/sectors]("http://forums.linuxmint.com/viewtopic.php?f=190&t=102102&p=579571#p579424")

             [[IMG]http://forums.linuxmint.com/styles/linux-mint/imageset/icon_post_target.gif[/IMG]]("http://forums.linuxmint.com/viewtopic.php?p=579424#p579424")by **[srs5694]("http://forums.linuxmint.com/memberlist.php?mode=viewprofile&u=79806")** on Mon May 14, 2012 11:17 am 



                            CHS geometry is a fiction, and has been for at  least two decades. Back in the 1980s, it reflected the underlying  reality of how disks were structured, but then disks began using  variable geometry -- cramming more sectors along the outer tracks than  the inner ones -- to get more storage on a disk. When this happened,  disks began lying about their CHS geometries to keep the BIOS and OS  happy. This worked for a while, but over various generations, the  interpretation of the CHS values kept changing. Today the CHS fields in  the [Master Boot]("http://www.cruisercustomizing.com/rear-master-cylinder-boot-harley-davidson-fl-models-58-69/part/BC-49-0700")[[IMG]http://s.skimresources.com/img/dollar.png[/IMG]]("http://www.cruisercustomizing.com/rear-master-cylinder-boot-harley-davidson-fl-models-58-69/part/BC-49-0700")[[IMG]http://s.skimresources.com/img/dollar.png[/IMG]]("http://www.cruisercustomizing.com/rear-master-cylinder-boot-harley-davidson-fl-models-58-69/part/BC-49-0700") Record (MBR) partition table are 24-bit values that top out at about 8 GB, so CHS geometries are not only fictions, they're *useless* fictions on most disks.

Instead  of CHS values, modern OSes and utilities encode MBR partition start  points and sizes using 32-bit logical block addressing (LBA) numbers,  which top out at 2 TiB. On GUID Partition Table (GPT) disks, 64-bit LBA  values are used, for a maximum size of 8 ZiB. The fields set aside for  CHS values still exist in MBR, and for partitions at the start of the  disk they may be set correctly, but in practice they're seldom used. GPT  doesn't even include any provision to use CHS values (except in the  protective MBR, where they're unimportant).

TestDisk continues to  use CHS values in its user interface, and I suspect internally,  although I've not checked the source code. IMO (no "H" there, as I've  written disk partitioning utilities and so know a lot about the  subject), this is a Bad Decision. CHS values are confusing and, as I've  just detailed, irrelevant on modern disks. Because CHS values are  largely irrelevant today, you can ignore the correspondence (or lack  thereof) of CHS values between what TestDisk reports and what anything  else reports. If you need to translate a value between two programs, you  should try to use LBA values, which are precise to the sector. *Never*  use the cylinder value alone, since today, most utilities create  partitions that begin "mid-cylinder," in CHS terms. If you can only get  partition data in CHS values, either translate it to LBA values or  ensure that the sector and head counts of the two programs are  identical, in which case they can be moved over as CHS values -- but be  sure to copy over all three numbers. The number of cylinders follows  logically from the number of sectors on the disk and the number of heads  and sectors in the CHS scheme; but the value could be rounded up or  down, depending on the utility. fdisk seems to round down, whereas  TestDisk seems to round up.

TestDisk has a known bug (or did a  while ago; it may have been fixed by now) in that it would sometimes  create an extended partition too big for the disk. I *suspect,*  but don't know for a fact, that this is a result of its using CHS  values; they're imprecise enough that most disks end "mid-cylinder," by  those values. When a disk is properly partitioned such that the last  logical partition ends in that last "partial cylinder," TestDisk gets  confused and creates an extended partition to hold that logical  partition that ends on a "cylinder boundary," which is beyond the end of  the disk. I'm guessing it rounds the cylinder values up to permit this,  but it can cause libparted-based tools to claim that the disk is  completely empty (because of a bug in libparted). The fix is to  re-create a properly sized extended partition. You can do this with some  effort with sfdisk, or a bit more simply with [FixParts.]("http://www.rodsbooks.com/fixparts/")

---

### Post by nicolasdiogo on 2012-05-14
just an adition, to 'align' partitions can have a performance imporvement on demanding systems such as database servers.

---

