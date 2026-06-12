---
title: "new 2TB Hard Drive not found by system"
date: 2013-10-05
forum: Hardware
---

### Post by markMDW on 2013-10-05
I connected a new SATA3 2TB Toshiba hard drive that's  supposed to be compatible with Windows, Mac and Linux.  The Bios did find the drive.

 Ubuntu 10.04 (SATA3) desktop and Xubuntu 12.04 laptop (using USB2 converter kit) didn't mount anything after booting up.  There isn't an icon under the folders when I looked.   

I plugged it into my Xubuntu 12.04 laptop as a USB drive, but nothing mounted.  

under Xubuntu 12.04, while attached to the USB2 converter.  I used terminal: 
>sudo gparted 
but the program doesn't show the hard drive under gparted either

I also tried:
>cd /dev
>ls *s

but I didn't recognize anything that looked like a hard drive..

I'm trying to figure out how to format and partition it for use with Ubuntu 10.04 (I suppose FAT32).  Thanks to everyone who posts advice!

---

### Post by powder on 2013-10-05
Connect the drive directly to a SATA port and open up Disk Utility. You should be able to see it on the left hand side.

---

### Post by oldfred on 2013-10-05
Do not use FAT32. It cannot store a file over 4GB and does not have a journel so running chkdsk may not repair it or may take forever on a very large drive. Also some older Windows will not support a FAT32 on that large of a drive.
If you need compatibility with Windows use NTFS.

Some of the USB caddies used for drives do not work with USB3 or very large drives. Have you verified that your converter does work?

---

### Post by markMDW on 2013-10-06
[ 						 							]("http://ubuntuforums.org/member.php?u=171")OLDFRED, what do you recommend for the File System?

The drive is now mounted, FAT32, and still empty.

It's connected directly to SATA again.   I see it under Disk Utility and Gparted.   It turns out I had misconnected it to the power supply.  When the Bios had found it, it had been connected correctly, but then I had reconnected it to an inactive (molex?) power cable when I connected the Ubuntu boot drive up.

At some point, I'd like to be able to take the hard drive out and plug it into the USB converter kit, and have it compatible with both Windows and Linux if possible.  But, if Ext4 is much better, I'd consider that to.

Disk Utility says the partition is misaligned by 512 bytes and suggests repartitioning.  Is that because of FAT32?

---

### Post by SuperFreak on 2013-10-06
NTFS is compatible with both Windows and Linux. You will have problems reading EXT file systems from Windows, but it is possible with the right win program installed [SEE THIS]("http://www.howtogeek.com/112888/3-ways-to-access-your-linux-partitions-from-windows/")

---

### Post by oldfred on 2013-10-06
The Linux NTFS driver is generally better at reading & writing than most of the Windows drivers that may read only Linux formatted partitions.
So for compatibility best to use NTFS.  
If only for Linux then ext4 would probably be the best choice.

Some Linux tools have old errors on cylinders. The only issue is with new 4K drives which yours may be.
       Alignment 2048 sectors Advanced Format drives
[http://askubuntu.com/questions/201164/proper-alignment-of-partitions-on-an-advanced-format-hdd-using-parted](http://askubuntu.com/questions/201164/proper-alignment-of-partitions-on-an-advanced-format-hdd-using-parted)
Technical details - from 2010 so now newer kernel resolve Linux issues
[https://ata.wiki.kernel.org/index.php/ATA_4_KiB_sector_issues](https://ata.wiki.kernel.org/index.php/ATA_4_KiB_sector_issues)

 [http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/index.html](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/index.html)

---

### Post by powder on 2013-10-06
> **markMDW said:**
> 

At some point, I'd like to be able to take the hard drive out and plug it into the USB converter kit, and have it compatible with both Windows and Linux if possible.  But, if Ext4 is much better, I'd consider that to.

Disk Utility says the partition is misaligned by 512 bytes and suggests repartitioning.  Is that because of FAT32?

Don't use FAT32, it's really a crappy filesystem. You should use NTFS since you want to read/write to it from both Windows and Linux.

If you use gparted it will create an aligned partition automatically. You should also be using GPT since your drive is 2TB.

1. Open gparted and select the disk in the top right corner
2. Go to Device -> Create partition table
3. Click Advanced and select GPT from the drop down menu
4. Create a new NTFS partition and apply the changes

---

### Post by markMDW on 2013-10-06
Thanks powder.. will be using NTFS and GPT

---

### Post by Yellow Pasque on 2013-10-06
> You should also be using GPT since your drive is 2TB.
The MBR limit is 2.2TB, so it's not necessary.

---

### Post by markMDW on 2013-10-06
[**[COLOR=#000000]Temüjin[/COLOR]**]("http://ubuntuforums.org/member.php?u=327594")

Temujin, will do, Thanks!   Thanks everyone that posted: SuperFreak, powder, oldfred, Temujin.

---

### Post by powder on 2013-10-06
> **Temüjin said:**
> The MBR limit is 2.2TB, so it's not necessary.

Thanks for the correction. Good to know.

---

### Post by Yellow Pasque on 2013-10-07
You're welcome. Also, note that even if the limit was 2TB, a "2 TB" disk wouldn't hit it because deceptive marketing is now standardized in the disk industry and it's actually 2 TiB.

---

### Post by oldfred on 2013-10-07
I still suggest gpt for new drives with some exceptions. It is the newer improved partitioning system.
But if installing Windows you must boot with UEFI when you have gpt. Also Windows XP cannot read a data partition on a gpt drive.
But if a data drive or Ubuntu drive you can boot with BIOS or UEFI and still have gpt partitioning. All partitions are in effect primary as it only has one type. It does have a limit of 128 partitions, where with logical partitions there is no real limit, but who has 128? And gpt has a way to expand the 128 limit if really required.

       GPT Advantages (older but still valid)  srs5694 post #2:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
GPT or MBR
[http://ubuntuforums.org/showthread.php?t=1625285](http://ubuntuforums.org/showthread.php?t=1625285)

---

