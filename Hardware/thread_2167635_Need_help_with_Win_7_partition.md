---
title: "Need help with Win 7 partition"
date: 2013-08-14
forum: Hardware
---

### Post by NMWJE3p on 2013-08-14
Following is the partition of my hard disk:

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *        2048   445399039   222698496    7  HPFS/NTFS/exFAT
/dev/sda3       445401086   488396799    21497857    5  Extended
/dev/sda5       445401088   482123775    18361344   83  Linux
/dev/sda6       482125824   488396799     3135488   82  Linux swap / Solaris

I used to have another VISTA recovery partition, which was accidentally deleted.
Now I am not able to login to Win 7.

I tried to fixboot and MBR, but still I get "BootMGR not found" error.
Windows recovery console shows a valid Win 7 installation.

Any help is appreciated. 

Ashish

---

### Post by jlh68 on 2013-08-23
Try Rescutux.  Download .iso file and use Brasero to burn an image.  Set bios to boot from optical drive and stqrt computer with CD in drive.I suggest using Super Grub2 to boot.  Once in you should be able to reconstruct MBR.

[http://www.supergrubdisk.org/rescatux/](http://www.supergrubdisk.org/rescatux/)

---

### Post by oldfred on 2013-08-24
Were boot files in another NTFS partition (sda1) and you since moved boot flag to sda2? You may be missing bootmgr & BCD?

       Vista/7 (with 7 the first two files are usually in a separate 100MB boot partition)
/bootmgr /Boot/BCD /Windows/System32/winload.exe 

If you have a Windows 7 repairCD that is the same 32 bit or 64 bit version as your install you can copy the bootmgr to your install and use bdcEdit or EasyBCD to repair BCD.

---

