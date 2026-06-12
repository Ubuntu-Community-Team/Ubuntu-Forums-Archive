---
title: "Installed 9.04 (alt CD), lost my Vista access?"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by Dan W. on 2009-04-25
Greetings Ubuntu adepts!

I'm relatively new to linux.  I installed 8.10 about 2 months ago as a dual boot with Windows Vista.  I had relatively few problems aside from a few hardware driver issues.  Windows was installed on two 320 Gb drives in RAID 1 supported by the motherboard BIOS.  8.10 was installed on a separate 320 Gb drive.  Since I installed 8.10 from the conventional live CD, it always saw the mirrored windows drives as separate, so I never wanted to write anything to the NTFS partition for fear of disturbing the mirrored drives.

When 9.04 came out, I decided to install it afresh from the altenate install CD, as my understading was that this would allow me to enable RAID support for the NTFS windows partition so that I could access the data on those drives when I was booted into linux.  During the alternate install process, I took the option to install RAID support.  I told it to partition/erase/overwrite the separate drive that had 8.10 on it for my new 9.04 installation.

Now I find that GRUB no longer shows my windows partition as an option when booting, nor do those mirrored drives show up in the places folder on the desktop.  Also, Ubuntu did not copy my windows personal music and documents when installing like it did with 8.10.

I know that I'm providing insufficient data in this initial post, but I don't know how to get the troubleshooting information I'd need to make it useful in the linux system.

I'm more than a bit worried that all my windows data is gone and I'm here to plead with help in troubleshooting.  I'm an experienced computer user, have built my own machines and am a relatively expert user using the windows OS, but am inexperienced with linux, so please type slowly and use small words :P.

Thanks in advance for your time and attention,
Dan

---

### Post by Dan W. on 2009-04-25
OK, I got enough of a clue to post the file system information, hopefully this will help any troubleshooters:

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xec2118b7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38913   312566784    7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xec2118b7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38913   312566784    7  HPFS/NTFS

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc8418ce0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       38161   306528201   83  Linux
/dev/sdc2           38162       38913     6040440    5  Extended
/dev/sdc5           38162       38913     6040408+  82  Linux swap / Solaris

---

### Post by Dan W. on 2009-04-25
After reading some similar threads, I installed the TestDisk app and analyzed the drives.  I can still see my windows files on the unaccessible partition, so my mind is eased enough that I'll be able to sleep tonight.  Below the the logfile from TestDisk, in case it's helpful:

```


Sat Apr 25 22:35:58 2009
Command line: TestDisk

TestDisk 6.11.1, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org
OS: Linux, kernel 2.6.28-11-generic (#42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009)
Compiler: GCC 4.3 - Apr 23 2009 12:34:59
ext2fs lib: 1.41.4, ntfs lib: 10:0:0, reiserfs lib: 0.3.1-rc8, ewf lib: 20080501
/dev/sda: LBA, HPA, LBA48, DCO support
/dev/sda: size       625142448 sectors
/dev/sda: user_max   625142448 sectors
/dev/sda: native_max 625142448 sectors
/dev/sda: dco        625142448 sectors
/dev/sdb: LBA, HPA, LBA48, DCO support
/dev/sdb: size       625142448 sectors
/dev/sdb: user_max   625142448 sectors
/dev/sdb: native_max 625142448 sectors
/dev/sdb: dco        625142448 sectors
/dev/sdc: LBA, HPA, LBA48, DCO support
/dev/sdc: size       625142448 sectors
/dev/sdc: user_max   625142448 sectors
/dev/sdc: native_max 625142448 sectors
/dev/sdc: dco        625142448 sectors
Warning: can't get size for Disk /dev/mapper/control - 0 B - CHS 1 1 1, sector size=512
Hard disk list
Disk /dev/sda - 320 GB / 298 GiB - CHS 38913 255 63, sector size=512 - ATA ST3320620AS
Disk /dev/sdb - 320 GB / 298 GiB - CHS 38913 255 63, sector size=512 - ATA ST3320620AS
Disk /dev/sdc - 320 GB / 298 GiB - CHS 38913 255 63, sector size=512 - ATA ST3320620AS
Disk /dev/mapper/isw_ifdjgbee_Phoenix - 320 GB / 298 GiB - CHS 625137664 1 1, sector size=512
Disk /dev/mapper/isw_ifdjgbee_Phoenix1 - 320 GB / 298 GiB - CHS 625133568 1 1, sector size=512

Partition table type (auto): None
Disk /dev/mapper/isw_ifdjgbee_Phoenix1 - 320 GB / 298 GiB
Partition table type: Intel

Analyse Disk /dev/mapper/isw_ifdjgbee_Phoenix1 - 320 GB / 298 GiB - CHS 625133568 1 1
Geometry from i386 MBR: head=117 sector=51
BAD_RS LBA=6579571 510
check_part_i386 1 type 70: no test
BAD_RS LBA=1953251627 453
check_part_i386 2 type 43: no test
BAD_RS LBA=225735265 450
check_part_i386 3 type 72: no test
get_geometry_from_list_part_aux head=1 nbr=6
get_geometry_from_list_part_aux head=8 nbr=1
get_geometry_from_list_part_aux head=16 nbr=1
get_geometry_from_list_part_aux head=32 nbr=1
Current partition structure:
 1 * DiskSecure MB            6579571 1924427647 1917848077

Warning: Bad starting sector (CHS and LBA don't match)
 2 * Sys=43                1953251627 3771827541 1818575915

Warning: Bad starting sector (CHS and LBA don't match)
 3 * Sys=72                 225735265  225735274         10

Warning: Bad starting sector (CHS and LBA don't match)
Only one partition must be bootable
Space conflict between the following two partitions
 1 * DiskSecure MB            6579571 1924427647 1917848077
 3 * Sys=72                 225735265  225735274         10
Ask the user for vista mode
Allow partial last cylinder : Yes
search_vista_part: 1

search_part()
Disk /dev/mapper/isw_ifdjgbee_Phoenix1 - 320 GB / 298 GiB - CHS 625133568 1 1
Search for partition aborted

Results

interface_write()
 
No partition found or selected for recovery
simulate write!

write_mbr_i386: starting...
write_all_log_i386: starting...
No extended partition
Partition table type (auto): Intel
Disk /dev/mapper/isw_ifdjgbee_Phoenix - 320 GB / 298 GiB
Partition table type: Intel

Analyse Disk /dev/mapper/isw_ifdjgbee_Phoenix - 320 GB / 298 GiB - CHS 625137664 1 1
Geometry from i386 MBR: head=255 sector=63
NTFS at 2048/0/1
heads/cylinder 255 (NTFS) != 1 (HD)
sect/track 63 (NTFS) != 1 (HD)
get_geometry_from_list_part_aux head=1 nbr=2
get_geometry_from_list_part_aux head=8 nbr=2
get_geometry_from_list_part_aux head=16 nbr=2
get_geometry_from_list_part_aux head=32 nbr=2
get_geometry_from_list_part_aux head=64 nbr=2
get_geometry_from_list_part_aux head=128 nbr=2
Current partition structure:
Warning: Incorrect number of heads/cylinder 255 (NTFS) != 1 (HD)
Warning: Incorrect number of sectors per track 63 (NTFS) != 1 (HD)
 1 * HPFS - NTFS                 2048  625135615  625133568

Warning: Bad starting sector (CHS and LBA don't match)
Allow partial last cylinder : Yes
search_vista_part: 1

search_part()
Disk /dev/mapper/isw_ifdjgbee_Phoenix - 320 GB / 298 GiB - CHS 625137664 1 1
NTFS at 2048/0/1
heads/cylinder 255 (NTFS) != 1 (HD)
sect/track 63 (NTFS) != 1 (HD)
filesystem size           625133568
sectors_per_cluster       8
mft_lcn                   786432
mftmirr_lcn               39070847
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS                 2048  625135615  625133568
     NTFS, 320 GB / 298 GiB
get_geometry_from_list_part_aux head=1 nbr=2
get_geometry_from_list_part_aux head=8 nbr=2
get_geometry_from_list_part_aux head=16 nbr=2
get_geometry_from_list_part_aux head=32 nbr=2
get_geometry_from_list_part_aux head=64 nbr=2
get_geometry_from_list_part_aux head=128 nbr=2
Warning: the current number of heads per cylinder is 1 but the correct value may be 128.

Results
   * HPFS - NTFS                 2048  625135615  625133568
     NTFS, 320 GB / 298 GiB
ntfs_device_testdisk_io_ioctl() unimplemented


```

---

### Post by Dan W. on 2009-04-26
After browsing many of the other threads in this forum, it seems that many people are reporting an issue with the alternate CD detecting partitions correctly during installation of 9.04.  Would running the repair process from the Live CD for 9.04 possibly repair this issue?  If so, would running the repair process from the Live CD cause issues with the FakeRaid support I was trying to get by using the alternate install CD?  Thanks for sharing any insights you may have.  Dan

---

### Post by Dan W. on 2009-04-26
I've seen several posts from people troubleshooting this issue and the helpful ubuntangels (OK, mostly Meierfra) seem to be asking for the output from sfdisk -d, so I'm including that as well.

```
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=     2048, size=625133568, Id= 7, bootable
/dev/sda2 : start=        0, size=        0, Id= 0
/dev/sda3 : start=        0, size=        0, Id= 0
/dev/sda4 : start=        0, size=        0, Id= 0
# partition table of /dev/sdb
unit: sectors

/dev/sdb1 : start=     2048, size=625133568, Id= 7, bootable
/dev/sdb2 : start=        0, size=        0, Id= 0
/dev/sdb3 : start=        0, size=        0, Id= 0
/dev/sdb4 : start=        0, size=        0, Id= 0
# partition table of /dev/sdc
unit: sectors

/dev/sdc1 : start=       63, size=613056402, Id=83
/dev/sdc2 : start=613056465, size= 12080880, Id= 5
/dev/sdc3 : start=        0, size=        0, Id= 0
/dev/sdc4 : start=        0, size=        0, Id= 0
/dev/sdc5 : start=613056528, size= 12080817, Id=82

```

And the output from fdisk -lu

```

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xec2118b7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   625135615   312566784    7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xec2118b7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   625135615   312566784    7  HPFS/NTFS

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc8418ce0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63   613056464   306528201   83  Linux
/dev/sdc2       613056465   625137344     6040440    5  Extended
/dev/sdc5       613056528   625137344     6040408+  82  Linux swap / Solaris


```

---

### Post by Dan W. on 2009-04-26
I'm not sure whether this is helpful or not, but attached is the last portion of the menu.lst file from the GRUB folder.

```

## ## End Default Options ##

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        45617075-a679-4fc3-b80d-a01a3cb2c006
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=45617075-a679-4fc3-b80d-a01a3cb2c006 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        45617075-a679-4fc3-b80d-a01a3cb2c006
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=45617075-a679-4fc3-b80d-a01a3cb2c006 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        45617075-a679-4fc3-b80d-a01a3cb2c006
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

```

---

### Post by Dan W. on 2009-04-27
One last bit of information, in case it's helpful: attached are screenshots from the 5 devices that show for GParted.

---

### Post by Dan W. on 2009-04-27
My suspicion is that the alternate CD overwrote the MBR.  I'm pretty sure I recall it asking me during the install process if that was OK, along with some statement that this was usually OK if it had detected other operation systems (which it had, Windows Vista).

Does anyone know if that would cause the problem I'm having, and if so, how to fix it?

---

### Post by Dan W. on 2009-04-28
Does anyone have any suggestions how to diagnose what went wrong with more certainty so that I can optimize my chances of using the correct online help guide to fix the issue?

---

### Post by Dan W. on 2009-05-02
I've tried fixing this issue myself, but without success thus far.  I tried using the Windows Vista install disk to fix the issue, but bootrec.exe /fixmbr succeeded, while bootrec.exe /fixboot failed, resulting in a system that now won't boot either OS without the use of the Super Grub Disk.  Using the Super Grub Disk, if I simply use the !WIN! option, I get an error 13 message.  If I use the Liveswap option, followed by the !WIN! option, it boots Windows Vista.  If I tell it to boot Linux from the second hard drive, it loads Ubuntu.  Any help would be deeply appreciated.  I'd like to be able to dual boot my system without using the Super Grub Disk.

---

