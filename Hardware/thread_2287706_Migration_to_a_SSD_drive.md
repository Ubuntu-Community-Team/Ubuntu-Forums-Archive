---
title: "Migration to a SSD drive"
date: 2015-07-21
forum: Hardware
---

### Post by SolomonMan on 2015-07-21
All,
Recently purchased a 250 GB Samsung EVO SSD.

Decided over last weekend to migrate my 200GB Windows 7 partition (sda2) over to the new SSD. Please note this is a dual boot system with Ubuntu and a few other partitions. Total of 7.  Original drive is a 640 GB drive.

The thoughts on this approach is move only my windows 7 partition over and then pull the original drive out entirely. The drive will be utilized in my home NAS at a later date. This approach will also be a full backup if I do not care for the pending Windows 10 upgrade. The latest version of Ubuntu will be then reinstalled most likely from scratch. (Its not my main Linux machine and is used occasionally) 

Keep in mind its been more than a few years since I have done anything similar to this as I usually just do fresh installs.

So first I fdisk'd the new drive to have the same size partition, type (NTFS), and marked the partition bootable. I then rebooted.

I then copied my Windows 7 original partition copied over using dd.
 
Initially I figured I would more than likely have to use my original Windows 7 retail DVD to recreate the master boot record. Also probably the Boot Sector for the new partition. 

Anyways,  I removed the original drive and then rebooted once the copy was completed.  Unfortunately no Windows.

So I inserted my Windows install disk and tried the repair option. Rebooted no change.
So I  did a Bootrec /FIXBOOT and Bootrec /FIXMBR from the command line using the Windows install disk and still no windows.

So I booted into Linux using a Live CD and noticed I can see the contents of the new partition. So I used the bootinfoscript to see if I can see anything wrong.

Below are the results;

                  Boot Info Script 0.61      [1 April 2012]

============================= Boot Info Summary: ===============================
 => Windows is installed in the MBR of /dev/sda.
sda1: __________________________________________________________________________
    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 34041735. But according to the info from 
                       fdisk, sda1 starts at sector 2048.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe
============================ Drive/Partition Info: =============================
Drive: sda _____________________________________________________________________
Disk /dev/sda: 232.9 GiB, 250059350016 bytes, 488397168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Partition  Boot  Start Sector    End Sector  # of Sectors  Id System
/dev/sda1    *          2,048   420,870,264   420,868,217   7 NTFS / exFAT / HPFS

"blkid" output: ________________________________________________________________
Device           UUID                                   TYPE       LABEL
/dev/loop0                                              squashfs   
/dev/sda1        F4E8F53EE8F4FFA2                       ntfs       Main Windows
/dev/sr0         2014-10-22-19-47-37-00                 iso9660    Xubuntu 14.10 i386
================================ Mount points: =================================
Device           Mount_Point              Type       Options
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)

========= Devices which don't seem to have a corresponding hard drive: =========
sdb sdc sdd sde 
=============================== StdErr Messages: ===============================
  No volume groups found


I am guessing my problem is around the boot sector because of the following phrase;

According to the info in the boot sector, sda1 starts 
                       at sector 34041735. But according to the info from 
                       fdisk, sda1 starts at sector 2048.

I have tried the windows install disk repair approach again and see no difference with the results when running the bootinfoscript.

I have also tried testdisk and rechecked with the bootinfoscript and again see no difference in results. So I am guessing I am doing something wrong (missing something).....

Please help.

Looking to get just this single partition over and running again...not afraid to start from the beginning (copy again etc)

Thanks,
Chris

---

### Post by weatherman2 on 2015-07-21
It might save you time at this point to start over with Clonezilla, which will take care of all of the boot stuff when cloning the hard drive.

---

### Post by SolomonMan on 2015-07-21
weatherman2 / all,
Will CloneZilla do a single partition from a dual boot system?

How does Clonezilla deal with Grub (separation of OS's)?

I always thought, I could be wrong, that the drive MBR boots into LILO/GRUB and then LILO/GRUB points to the individual boot sectors of each partition. Am I correct in this assumption?

Thanks for the help,
Chris

---

### Post by oldfred on 2015-07-21
Try chkdsk, that normally fixes the partition boot sector.

Or if you have to have a totally new partition boot sector.
       Use bootsect.exe to repair XP & older or Vista/7 bootsectors - Use diskpart, then list volumes to see which drive to use 
bootsect.exe /nt52 c:  *compatible* with operating systems older (XP) than Windows Vista.
bootsect.exe /nt60 c:  *compatible* with Windows Vista, Windows Server 2008 or later

Windows has a lot of internal data where it must match partition table. Was your old Windows not at 2048 first sector on drive?
Did you not have the usually install of a 100MB boot sector and then main install?

---

### Post by SolomonMan on 2015-07-21
oldfred,
The first partition of the original drive was factory installed rescue partition (decent size (16 or 20 Gig?) - can not remember size at the moment...not at the machine currently).  Then came the Windows partition.

I will look at the boot sector size and see tonight...

I will give the chkdsk a try first and then bootsect.....

Thanks,
Chris

---

### Post by weatherman2 on 2015-07-21
Clonezilla seems to be able to deal with complicated boot setups.  The last time I used it, I cloned my netbook's dual boot of Windows 8 + Ubuntu 12.04 (with LVM), also with secure boot enabled.  It handled it perfectly, except for a glitch setting up the swap partition (but that was simple to fix).

Because you are cloning to a larger drive, it might be easier to clone the entire drive first, then delete the other partitions and grow the Windows partition.

dd is a very inefficient way to clone something - because it copies everything, free and used space.  To copy just a partition, try using Gparted.  Clonezilla can copy individual partitions as well, I think and it can also save them as images (so just a directory on a backup hard drive, not needing the whole drive).

---

### Post by SolomonMan on 2015-07-21
weatherman,
Thanks for the help!

I will take a further look at Clonezilla and I have some experience with GParted (a while back).

Again thanks for the help,
Chris

---

### Post by weatherman2 on 2015-07-21
FYI, sometimes when Windows 7 is installed, it creates a small boot partition that must be copied also when migrating to a different disk.  Did you make sure there wasn't a small little Windows partition like that, that you forgot to copy?

---

### Post by SolomonMan on 2015-07-21
weatherman2,
I will take a look at that as well tonight.

Thanks again,
Chris

---

### Post by SolomonMan on 2015-07-21
oldfred/weatherman2/all

Update...

Tried the chkdsk...it  said everything looked normal except should use /f option but not able  in the install DVD....says disk is locked?

Tried the diskpart to look at volumes, partitions and such and my novice eyes did not see anything out of whack. 

Tried the bootsect.exe /nt60 c: and compared it afterwards against the bootinfoscript and it still has the same

According to the info in the boot sector, sda1 starts 
                       at sector 34041735. But according to the info from 
                       fdisk, sda1 starts at sector 2048.

For prosperity, I looked at dev/sda1 partition and its 16GB in size and only 10GB is used. 

A  question came to mind is the install DVD the reason for not letting the  boot sector be updated due to it being locked but still reporting  successful?

For clarification... I am using my original Windows  Install CD and selecting repair and it takes me to a screen which has a  command line selection. I select it and then run the command. Is there  another process....Recover CD or something like that?

Not sure why I cannot alter the boot sector but a lock may explain it.

So at this point I have begun to download CloneZilla as a backup plan.

Any input is greatly appreciated.
Chris

---

### Post by oldfred on 2015-07-21
Do you have boot flag (active partition in Windows) on your NTFS partition?
Windows only boots from, installs to, or repairs the bootable partition if it is seen as bootable with the boot flag.

---

### Post by SolomonMan on 2015-07-22
All,
Tried the CloneZilla and no luck...same flashing cursor at boot.

I booted up into a live cd and compared the bootscriptinfo results and they were identical as before.

Went through the suggestions by oldfred (bootsect,diskpart,etc) with same result.

So I installed a WxHexEditor and looked at the first 512 bytes of the drive. (Similar to the below page)
[http://blog.creativeitp.com/posts-and-articles/bios/analysing-the-master-boot-record-mbr-with-a-hex-editor-hex-workshop/comment-page-1/](http://blog.creativeitp.com/posts-and-articles/bios/analysing-the-master-boot-record-mbr-with-a-hex-editor-hex-workshop/comment-page-1/)

And the Magic Number (511 & 512 bytes) was 55 AA.  (So its valid?)

I looked further and as the example provided starting sector was 2048....I confirmed with my value and I was surprised to see they matched....meaning the bootscriptinfo may not be what I think it is or the script may be outdated/error?

I wonder where it gets the 34041735 from the statement;

According to the info in the boot sector, sda1 starts 
                       at sector 34041735. But according to the info from 
                       fdisk, sda1 starts at sector 2048.

Also I confirmed the disk is marked with the boot flag using Gparted and fdisk. I also confirmed through windows (rebooted original drive) that the original windows partition (disk Management-> Drive statuses) is a singular system and boot partition.

I would says though that the CloneZilla is a much faster process (unfortunately same result).

I think my next step is to blow away the recent copy/clone and try a fresh install of Windows 7....I am not giving up... but I would just like to see Windows boot from this new drive and this is something I can kick off before I leave for work this morning.

Any suggestion or help is greatly appreciated.

Thanks,
Chris

---

### Post by SolomonMan on 2015-07-22
All, 
Installed Windows 7 fresh from DVD and quickly installed Ubuntu 14.10. No problems and everything appears to be working properly.

I did notice two things during the install....

I left the original failed attempt partition on the Samsung SSD drive figuring that I would blow it away upon the Windows 7 install. Upon the Windows 7 install I was of course warned about the existing windows partition (expected). Not expected was the option to Upgrade Windows 7....My previous drive system was Windows 7 SP1 (after the updates etc over the years of having Windows 7). The DVD is a plain Vanilla Windows 7 DVD....Why the possibility of the upgrade?..maybe that's normal?...

Well I went the fresh install route and blew away the original partition but after the new install finished I took a look using GParted an the new system layout and I see what old fred questioned\mentioned earlier about the 100 Mg additional system partition....I now wonder if the upgrade process would possibly change my singular partition system into a new dual partition system and fix my migration issue (or at least maybe its the possibly the cause of my grief)...?

Any Suggestions are appreciated.

Thanks,
Chris

---

### Post by oldfred on 2015-07-22
You do not have to have the separate 100MB boot partition. That primarily is so you can encrypt the main partition and to get users used to separate partitions which with UEFI/gpt you have many partitions.
But many that have the 100MB boot partition, do not know it is essential. Boot-Repair now copies boot files bootmgr & BCD folder into main partition so if a user deletes Boot partition it will still boot.
I think the recovery/repair software also in in Boot partition as it should be bootable even if c: needs repairs.
If you have boot flag on current install then it should just overwrite that. Similar to an upgrade to Vista which was in one partition.
The reason your start sector in the partition boot sector says 34041735 is probably where it was on old drive as it was not first sector. Start sector in partition boot sector must match start sector in partition table. First partition now normally starts at sector 2048.

If your chkdsk did not run correctly then that is why it was not fixed. But I thought bootsect.exe wrote a totally new boot sector?

If you did not have boot flag on existing install then that also is why it would not repair and a new install would write new partitions.

---

### Post by SolomonMan on 2015-07-22
oldfred,
The bootsect /nt60 c: said it was successful. (Displayed a GUID etc).
The existing (original) has a boot flag on the sda2 partition (The source partition )

When you say "Start sector in partition boot sector must match start sector in partition table"...lets make sure I follow...When I looked at the first 512 bytes of the drive or its MBR... the Boot Record Signature was the 55 AA. So can the assumption be made that more than likely that the MBR is valid? 

If we start at the 446 byte point, assuming the 0-446 is basic programming, this should be the first partition table's info. Work thru the bytes of this table location 454 -457 should be the starting address of the first partition. Mine read 00 08 00 00.  After the endianness conversion etc its 0x800 or 2048 (not done anything like this since my undergrad degree). So with this information the 2048 is the starting address of the first partition (start sector).  So we are at the partition door step so to speak. I did confirm that the 446 (Boot Indicator) was 80 (Active). Also that 450 (Partition Type Descriptor) was 07 (NTFS).  I did not confirm the Ending CHS Values and Size but assuming CloneZilla has done this before...I would think we are good.

So is the 34041735 stored somewhere else in the partition (a file?)...It appears we are at the doorstep of the partition correctly.

When I used CloneZilla I used partition to partition not the Image option....not sure if that would help.

I am looking into the Windows Backup (Image) and restore option for Windows 7. Curious to see what it will come up with for results.

Again thanks for the help,
Chris

---

### Post by weatherman2 on 2015-07-22
In my experience, the Windows 7 installer will create the small boot partition by default, unless you create an NTFS partition ahead of time and tell it to install in that partition.  Afterward, I have found that Windows 7 boot repair DOES NOT necessarily fix/replace the boot files in the boot partition if it gets erased.  I know I have tried that to get rid of the boot partition on at least one Windows 7 installation.  I was eventually able to get rid of it but it was a bit more complicated - had to copy some files manually, do something else...and then run boot repair anyway.

---

### Post by oldfred on 2015-07-22
The partition boot sector is just like the MBR. But is the first sector in the partition. It is used by Windows for more boot code and by logical partitions for an entry to the next logical partiton.

I have used testdisk to compare a XP partition boot sector or PBR. And after running chkdsk from a Windows 7 repair flash drive it did make more fixes than XP's chkdsk, but converted it to a Windows 7 PBR. Not sure how Bootinfoscript parse all that. But using testdisk I could see old XP type PBR and newer Win7 PBR. One clearly said ntldr and the other bootmgr. But the PBR also has start & size of partition in it, and that is why after any resize of Windows you have to run chkdsk to update into. Perhaps start is not fixable, where size is with chkdsk?

       Multibooters, Pictures here worth 1000+ words - Vista but all Windows with BIOS/MBR
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
[http://www.multibooters.co.uk/articles/windows_seven.html](http://www.multibooters.co.uk/articles/windows_seven.html)
More tech info - BIOS boot process & some UEFI
[http://homepage.ntlworld.com./jonathan.deboynepollard/FGA/windows-nt-6-boot-process.html](http://homepage.ntlworld.com./jonathan.deboynepollard/FGA/windows-nt-6-boot-process.html)

I think the 55 aa is just that MBR structure is correct as MBR. Not necessarily that all info in it is correct.

---

