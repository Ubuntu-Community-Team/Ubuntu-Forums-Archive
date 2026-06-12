---
title: "Please, help with non-MBR GRUB"
date: 2009-10-04
forum: Installation &amp; Upgrades
---

### Post by Telegram Sam on 2009-10-04
Hello, Forum!

Would you, please, help me with GRUB which is located in the same partition, where Ubuntu 9.04 was installed.

GRUB (and everything, lonely "/") is on /dev/sda9. Right after install, system was booted up successfully and "dist-upgraded" via clean CLI apt. After that, rebooted, I see only "grub>" when I tried to boot the Ubuntu 9.04

Here is a backgrund:

System is boot up via MS ntldr (standard procedure, dd of first sector of the linux partition with GRUB into *.bin file).

Some exerptions from "boot_info_script032.sh":

sda9: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda9 and 
                       looks at sector 134353635 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #9 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0f550f54

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    81,931,499    81,931,437   7 HPFS/NTFS
/dev/sda2          81,931,500   106,510,949    24,579,450   7 HPFS/NTFS
/dev/sda3         106,510,950   106,639,469       128,520  83 Linux
/dev/sda4         106,639,470   156,296,384    49,656,915   5 Extended
/dev/sda5         106,639,533   122,270,714    15,631,182  83 Linux
/dev/sda6         122,270,778   124,230,644     1,959,867  83 Linux
/dev/sda7         124,230,708   128,134,439     3,903,732  83 Linux
/dev/sda8         128,134,503   130,126,499     1,991,997  82 Linux swap / Solaris
/dev/sda9         130,126,563   143,219,474    13,092,912  83 Linux
/dev/sda10        143,219,538   156,296,384    13,076,847  83 Linux

Current GRUB menu.lst on /dev/sda9:

title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		a977ab40-1520-4d8a-83bf-29a3df9694f3
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=a977ab40-1520-4d8a-83bf-29a3df9694f3 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		a977ab40-1520-4d8a-83bf-29a3df9694f3
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=a977ab40-1520-4d8a-83bf-29a3df9694f3 ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, memtest86+
uuid		a977ab40-1520-4d8a-83bf-29a3df9694f3
kernel		/boot/memtest86+.bin
quiet

At the same time, if I boot with Ubuntu LiveCD and:

grub> find /boot/grub/stage1
 (hd0,2)
 (hd0,9)

How /dev/sda9 may be (hd0,9)? (hd0,2) is correct, where Debian loader is located, but where is my GRUB at (hd0,8 )?

Please, help me to reinstall GRUB into first sector of /dev/sda9 (hd0,8 ) and boot up Ubuntu 9.04

Thanks n advance!

---

### Post by rreese6 on 2009-10-04
Many people have had success using a program called Super Grub.
Here is the link;

[http://www.supergrubdisk.org/]("http://www.supergrubdisk.org/")

---

### Post by Telegram Sam on 2009-10-04
Thanks!
It was possible to boot Ubuntu via SGD, but anyway, there is a mess: SGD shows /dev/sda10 as Ubuntu GRUB location, but it is /dev/sda9, where I put it actually.

And, it is a failure to reinstall grub from Ubuntu itself:

$ sudo grub-install /dev/sda9
Searching for GRUB installation directory ... found: /boot/grub
The file /boot/grub/stage1 not read correctly.

I have also checked UUID (GRUB uses UUID) and that correct in GRUB.
No boot, anyway.

---

