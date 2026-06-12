---
title: "usb sata hard drive issue"
date: 2011-10-20
forum: Hardware
---

### Post by kalabarigi.aditya on 2011-10-20
Hi Guys,

I have a seagate USB sata portable drive which is no longer detected in windows as my son dropped the drive couple of times in my absence and thats why I believe it is no longer readable. I have tons of pics and other stuff in the drive and I'd like to retrieve them back at least the pics.

So my firend adviced to see if linux might be able to detect and repair the disk. So I have installed ubuntu on my desktop and attached the drive. But even here I cannot see the disk. Please can someone help or point me in the right direction to get the data back.

when I do fdisk -l the system hangs as it tries to read the sata disk. Lot of read errors and IO errors in the dmesg

root@ubuntu:/home/addy# fdisk -l

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848  1221466111   610629632    7  HPFS/NTFS/exFAT
/dev/sda4      1221466112  1250260991    14397440    7  HPFS/NTFS/exFAT
^C^C^C

dmesg : output

root@ubuntu:/home/addy# dmesg | grep sdc
[ 1592.661014] sd 5:0:0:0: [sdc] 4294967295 512-byte logical blocks: (2.19 TB/1.99 TiB)
[ 1592.661647] sd 5:0:0:0: [sdc] Write Protect is off
[ 1592.661655] sd 5:0:0:0: [sdc] Mode Sense: 2f 08 00 00
[ 1592.662250] sd 5:0:0:0: [sdc] No Caching mode page present
[ 1592.662258] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[ 1592.664378] sd 5:0:0:0: [sdc] No Caching mode page present
[ 1592.664386] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[ 1592.700744] sd 5:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1592.700758] sd 5:0:0:0: [sdc]  Sense Key : Illegal Request [current] 
[ 1592.700773] sd 5:0:0:0: [sdc]  Add. Sense: Logical block address out of range
[ 1592.700783] sd 5:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[ 1592.700801] end_request: I/O error, dev sdc, sector 0
[ 1592.700810] Buffer I/O error on device sdc, logical block 0
[ 1772.668397] sd 5:0:0:0: [sdc] Unhandled sense code
[ 1772.668403] sd 5:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1772.668412] sd 5:0:0:0: [sdc]  Sense Key : Hardware Error [current] 
[ 1772.668426] sd 5:0:0:0: [sdc]  Add. Sense: Internal target failure
[ 1772.668437] sd 5:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 01 00 00 01 00
[ 1772.668454] end_request: I/O error, dev sdc, sector 1
[ 1772.668462] Buffer I/O error on device sdc, logical block 1
[ 1772.704898] sd 5:0:0:0: [sdc] Unhandled sense code
[ 1772.704903] sd 5:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1772.704910] sd 5:0:0:0: [sdc]  Sense Key : Hardware Error [current] 
[ 1772.704923] sd 5:0:0:0: [sdc]  Add. Sense: Internal target failure
[ 1772.704934] sd 5:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 02 00 00 06 00
[ 1772.704950] end_request: I/O error, dev sdc, sector 2

Thanks in advance for looking into this and appreciate your help.

---

