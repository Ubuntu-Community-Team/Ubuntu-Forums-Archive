---
title: "Grub won't boot Jaunty - Error 15 file not found"
date: 2009-05-21
forum: Installation &amp; Upgrades
---

### Post by Endolith on 2009-05-21
I created a new partition near the end of my disk and installed Jaunty on it.  After installation, it wouldn't boot, giving me the stage1.5 error.

So then I installed grub into the MBR and selected my existing Ubuntu install sda6 as root.  It can now boot into the old Ubuntu on sda6, but when I copy the Jaunty partition options from Jaunty's menu.lst to the working menu.lst on the root partition, it still doesn't work, it gives the Error 15 file not found error and returns to the grub menu if i try.

```


title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        c78c2847-6416-4184-b714-8a37280b648b
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=c78c2847-6416-4184-b714-8a37280b648b ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        c78c2847-6416-4184-b714-8a37280b648b
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=c78c2847-6416-4184-b714-8a37280b648b ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        c78c2847-6416-4184-b714-8a37280b648b
kernel        /boot/memtest86+.bin
quiet

``````
~> sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6        3921    31455270    7  HPFS/NTFS
/dev/sda3            3922        4379     3678885   db  CP/M / CTOS / ...
/dev/sda4            4380       19457   121114035    f  W95 Ext'd (LBA)
/dev/sda5            4380        4510     1052226    b  W95 FAT32
/dev/sda6            4511       11530    56388118+  83  Linux
/dev/sda7           11531       19092    60741733+  83  Linux
/dev/sda8           19093       19457     2931831   82  Linux swap / Solaris

```sda6 is the existing Intrepid install, sda7 is the new Jaunty install.

---

### Post by Endolith on 2009-05-23
If I change it to say "root (hd0,6)" it gives error 2, though Grub can apparently see the partition fine.

---

### Post by Endolith on 2009-05-24
If I change the first entry to say root (hd6,0):

```

title        Ubuntu 9.04, kernel 2.6.28-11-generic
# uuid        c78c2847-6416-4184-b714-8a37280b648b
root        (hd0,6)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=c78c2847-6416-4184-b714-8a37280b648b ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        c78c2847-6416-4184-b714-8a37280b648b
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=c78c2847-6416-4184-b714-8a37280b648b ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

```

I get "Error 2: Bad file or directory type" if I try to run the first option, and get "Error 15: File not found" if I try to run the second option that still uses uuid.

---

### Post by Endolith on 2009-05-24
I used GParted to shrink my existing Intrepid partition upwards and set up an 8 GB partition for Jaunty in the same starting sector. After installation, I get this:
 ```

 GRUB Loading stage1.5


 GRUB loading, please wait...
 Error 18
  _

``` The Jaunty partition is on /dev/sda8 and has 2.19 GiB of files on it, so it installed.  Fdisk says:
 
```

ubuntu@ubuntu:~$ sudo fdisk -l
 Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0000000
    Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6        3921    31455270    7  HPFS/NTFS
/dev/sda3            3922        4379     3678885   db  CP/M / CTOS / ...
/dev/sda4            4380       19457   121114035    f  W95 Ext'd (LBA)
/dev/sda5            4380        4510     1052226    b  W95 FAT32
/dev/sda6            5532       19092   108928701   83  Linux
/dev/sda7           19093       19457     2931831   82  Linux swap / Solaris
/dev/sda8            4511        5531     8201151   83  Linux
 Partition table entries are not in disk order


```From the LiveCD, /media/Jaunty/boot/grub/menu.lst has:
```

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        0dd908ba-9bf9-4904-8300-a8fc425d44a8
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=0dd908ba-9bf9-4904-8300-a8fc425d44a8 ro quiet splash
initrd        /boot/initrd.img-2.6.28-11-generic
quiet
 title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        0dd908ba-9bf9-4904-8300-a8fc425d44a8
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=0dd908ba-9bf9-4904-8300-a8fc425d44a8 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic
 title        Ubuntu 9.04, memtest86+
uuid        0dd908ba-9bf9-4904-8300-a8fc425d44a8
kernel        /boot/memtest86+.bin
quiet
 ...
 # This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title        Ubuntu 8.10, kernel 2.6.27-14-generic (on /dev/sda6)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.27-14-generic root=UUID=77be7041-20fa-4e99-af8d-5489b5e6b6b7 ro quiet splash
initrd        /boot/initrd.img-2.6.27-14-generic
savedefault
boot
 # This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title        Ubuntu 8.10, kernel 2.6.27-14-generic (recovery mode) (on /dev/sda6)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.27-14-generic root=UUID=77be7041-20fa-4e99-af8d-5489b5e6b6b7 ro single
initrd        /boot/initrd.img-2.6.27-14-generic
savedefault
boot

``` The UUID for the Jaunty partition is correct according to Nautilus.

```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       80324       40131   de  Dell Utility
/dev/sda2   *       80325    62990864    31455270    7  HPFS/NTFS
/dev/sda3        62990865    70348634     3678885   db  CP/M / CTOS / ...
/dev/sda4        70348635   312576704   121114035    f  W95 Ext'd (LBA)
/dev/sda5        70348698    72453149     1052226    b  W95 FAT32
/dev/sda6        88855578   306712979   108928701   83  Linux
/dev/sda7       306713043   312576704     2931831   82  Linux swap / Solaris
/dev/sda8        72453213    88855514     8201151   83  Linux

Partition table entries are not in disk order
ubuntu@ubuntu:~$ sudo sfdisk -d
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size=    80262, Id=de
/dev/sda2 : start=    80325, size= 62910540, Id= 7, bootable
/dev/sda3 : start= 62990865, size=  7357770, Id=db
/dev/sda4 : start= 70348635, size=242228070, Id= f
/dev/sda5 : start= 70348698, size=  2104452, Id= b
/dev/sda6 : start= 88855578, size=217857402, Id=83
/dev/sda7 : start=306713043, size=  5863662, Id=82
/dev/sda8 : start= 72453213, size= 16402302, Id=83

```

---

### Post by Endolith on 2009-05-25
Thanks for nothing!

I ended up shuffling my partitions around and then creating a dedicated boot partition, which I can then boot the Jaunty install from, and it doesn't care about the BIOS translated area.

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6        3921    31455270    7  HPFS/NTFS
/dev/sda3            3922        4379     3678885   db  CP/M / CTOS / ...
/dev/sda4            4380       19457   121114035    f  W95 Ext'd (LBA)
/dev/sda5            4380        4415      289138+  83  Linux
/dev/sda6            4416        4510      763056    c  W95 FAT32 (LBA)
/dev/sda7            4511        5531     8201151   83  Linux
/dev/sda8            5532       19092   108928701   83  Linux
/dev/sda9           19093       19457     2931831   82  Linux swap / Solaris

```

---

### Post by lavinog on 2009-05-25
First you should post your whole menu.lst. The stuff that looks like it is commented out in the beginning gets read when you do a kernel update...if the root uuid isn't in sync with what you have there you can have issues later.

Second, I suspect the problem has to do with your uuid's not being correct.
can you post the output of:
```
ls -l /dev/disk/by-uuid/
```

---

### Post by Endolith on 2009-05-25
The Error message said the Jaunty boot was out of range.  I don't know how that's possible if Intrepid booted from the same sector, but a separate boot partition fixed it.

---

