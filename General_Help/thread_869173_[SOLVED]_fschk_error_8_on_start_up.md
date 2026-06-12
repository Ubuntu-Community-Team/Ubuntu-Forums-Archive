---
title: "[SOLVED] fschk error 8 on start up"
date: 2008-07-24
forum: General Help
---

### Post by lighthouseca on 2008-07-24
Problem

 when i restart and system does it's checks i get an error 8 and told to run fschk manually? then the only way to boot up is through a control D
any suggestions

appreciate

---

### Post by plucky on 2008-07-24
> **lighthouseca said:**
> Problem

 when i restart and system does it's checks i get an error 8 and told to run fschk manually? then the only way to boot up is through a control D
any suggestions

appreciate

Post output of ```
cat /etc/fstab ; sudo blkid
```

There is a possibility the UUID of one of your partitions is incorrect.

---

### Post by gerry mcgowan on 2008-07-24
I had similar problem on laptop and desktop today. When system fails to launch and you get error message type *fschk*. answer y to all prompts. Make sure to wait until system is finished as it takes a little time to complete some parts, and you are back at root command. Then control D to reboot. When system reboots it should be ok. It worked for me anyway....

---

### Post by lighthouseca on 2008-07-25
> **plucky said:**
> Post output of ```
cat /etc/fstab ; sudo blkid
```

There is a possibility the UUID of one of your partitions is incorrect.
here it is :KS
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
#/dev/sdb2
UUID=e2ce6ddb-8453-4090-a93a-3525a55336e2 /media/sdb2               ext3    defa                                                           ults,errors=remount-ro 0       1
#/dev/sdb1
UUID=855eada0-9711-45c7-96b4-ecc7425b6776 /media/sdb1               ext3    defa                                                           ults,errors=remount-rw 0       1
# /dev/sdb5
UUID=2307c873-a9ea-4ccc-86a2-2aa9c04ab34e none            swap    sw                                                                         0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
[sudo] password for john:
/dev/sda1: LABEL="HP_RECOVERY" UUID="22D1-40E3" TYPE="vfat"
/dev/sda2: UUID="AA04D8FC04D8CD07" LABEL="HP_PAVILION" TYPE="ntfs"
/dev/sda3: UUID="a5581b8a-ff2a-4ca4-adcf-57402a4a061c" SEC_TYPE="ext2" TYPE="ext3"
/dev/sda5: TYPE="swap" UUID="3fd37586-5c8d-44b5-acfc-215c851964e7"
/dev/sda6: UUID="4d760132-01f1-4e63-b653-ff538d252dde" SEC_TYPE="ext2" TYPE="ext3"
/dev/sdb1: UUID="855eada0-9711-45c7-96b4-ecc7425b6776" SEC_TYPE="ext2" TYPE="ext3"
/dev/sdb2: UUID="e2ce6ddb-8453-4090-a93a-3525a55336e2" SEC_TYPE="ext2" TYPE="ext3"
/dev/sdb5: TYPE="swap" UUID="2307c873-a9ea-4ccc-86a2-2aa9c04ab34e"

---

### Post by Ender305 on 2008-07-25
try just doing an fsck, if its the root filesystem, you may need a live cd to do a safe fsck(doing an fsck on a mounted partition isn't always safe)

---

### Post by lighthouseca on 2008-07-25
what parameters would i use

---

### Post by geirha on 2008-07-25
```

#/dev/sdb2
UUID=e2ce6ddb-8453-4090-a93a-3525a55336e2 /media/sdb2 ext3 [color=blue]defa ults[/color],errors=remount-ro 0 [color=red]1[/color]
#/dev/sdb1
UUID=855eada0-9711-45c7-96b4-ecc7425b6776 /media/sdb1 ext3 [color=blue]defa ults[/color],errors=remount-rw 0 [color=red]1[/color]
```

Is there really a space in the middle of the default keyword (marked in blue) ? There shouldn't be a space there, and I beleive it may be the cause of your error.

Also, only / and /boot should have 1 as the fs_passno (marked in red) field. All other ext2/ext3 filesystems should have 2. Read ```
man fstab
``` for more info.

---

### Post by plucky on 2008-07-25
```
/dev/sda3: UUID="a5581b8a-ff2a-4ca4-adcf-57402a4a061c" SEC_TYPE="ext2" TYPE="ext3"
/dev/sda5: TYPE="swap" UUID="3fd37586-5c8d-44b5-acfc-215c851964e7"
```


What are these partitions?
Where is your / partition? 
Why is it not in fstab?
Are you dual booting?

---

### Post by lighthouseca on 2008-07-25
no there is no space in default
should i replace o with 2 in fstab for sdb1 as per yur hilite?

---

### Post by lighthouseca on 2008-07-25
leftovers from my windows disk and initial experiments with linux
thanks

---

### Post by plucky on 2008-07-25
Can you post output from a terminal of```
cat /var/log/fsck/checkfs
sudo fdisk -l
cat /boot/grub/menu.lst
```

---

### Post by lighthouseca on 2008-07-25
here you go it's starting to make sense

cat /var/log/fsck/checkfs
Log of fsck -C -R -A -a
Thu Jul 24 16:51:50 2008

fsck 1.40.8 (13-Mar-2008)
/dev/sdb2 is mounted.  e2fsck: Cannot continue, aborting.


/dev/sdb1: clean, 14/424320 files, 55400/1690833 blocks
fsck died with exit status 8

fdisk -l
Disk /dev/sda: 40 GB, 40015503360 bytes
240 heads, 63 sectors/track, 5169 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         697     5269288    b  FAT32
/dev/sda2   *         772        4369    27193320    7  HPFS/NTFS
/dev/sda3            4370        4396      196560   83  Linux
/dev/sda4            4397        5169     5836320    5  Extended
/dev/sda6            4397        5110     5390280   83  Linux
/dev/sda5            5111        5169      438480   82  Linux swap

Disk /dev/sdb: 40 GB, 40015987200 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         842     6763333   83  Linux
/dev/sdb2   *         843        4674    30772507   83  Linux
/dev/sdb3            4675        4865     1526175    5  Extended
/dev/sdb5            4683        4857     1397655   82  Linux swap
Error: Unable to open /dev/fd0 - unrecognised disk label.
Warning: Unable to open /dev/scd0 read-write (Read-only file system).  /dev/scd0 has been opened read-only.
Error: Unable to open /dev/scd0 - unrecognised disk label.     

 title           Ubuntu 8.04.1, kernel 2.6.24-19-generic
root            (hd1,1)
kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=e2ce6ddb-8453-4090-a93a-3525a55336e2 ro quiet splash
initrd          /boot/initrd.img-2.6.24-19-generic
quiet

title           Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root            (hd1,1)
kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=e2ce6ddb-8453-4090-a93a-3525a55336e2 ro single
initrd          /boot/initrd.img-2.6.24-19-generic

title           Ubuntu 8.04.1, kernel 2.6.22-14-generic
root            (hd1,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=e2ce6ddb-8453-4090-a93a-3525a55336e2 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 8.04.1, kernel 2.6.22-14-generic (recovery mode)
root            (hd1,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=e2ce6ddb-8453-4090-a93a-3525a55336e2 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 8.04.1, memtest86+
root            (hd1,1)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windows NT/2000/XP
root            (hd0,0)
savedefault
makeactive
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Microsoft Windows XP Home Edition
root            (hd0,1)
savedefault
makeactive
chainloader     +1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title           Ubuntu 8.04, kernel 2.6.24-19-generic (on /dev/sda6)
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=4d760132-01f1-4e63-b653-ff538d252dde ro quiet splash
initrd          /boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title           Ubuntu 8.04, kernel 2.6.24-19-generic (recovery mode) (on /dev/sda6)
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=4d760132-01f1-4e63-b653-ff538d252dde ro single
initrd          /boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title           Ubuntu 8.04, kernel 2.6.24-18-generic (on /dev/sda6)
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.24-18-generic root=UUID=4d760132-01f1-4e63-b653-ff538d252dde ro quiet splash
initrd          /boot/initrd.img-2.6.24-18-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title           Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode) (on /dev/sda6)
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.24-18-generic root=UUID=4d760132-01f1-4e63-b653-ff538d252dde ro single
initrd          /boot/initrd.img-2.6.24-18-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title           Ubuntu 8.04, kernel 2.6.24-17-generic (on /dev/sda6)
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.24-17-generic root=UUID=4d760132-01f1-4e63-b653-ff538d252dde ro quiet splash
initrd          /boot/initrd.img-2.6.24-17-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title           Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode) (on /dev/sda6)
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.24-17-generic root=UUID=4d760132-01f1-4e63-b653-ff538d252dde ro single
initrd          /boot/initrd.img-2.6.24-17-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title           Ubuntu 8.04, kernel 2.6.24-16-generic (on /dev/sda6)
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.24-16-generic root=UUID=4d760132-01f1-4e63-b653-ff538d252dde ro quiet splash
initrd          /boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title           Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode) (on /dev/sda6)
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.24-16-generic root=UUID=4d760132-01f1-4e63-b653-ff538d252dde ro single
initrd          /boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title           Ubuntu 8.04, memtest86+ (on /dev/sda6)
root            (hd0,5)
kernel          /boot/memtest86+.bin
savedefault
boot

---

### Post by plucky on 2008-07-25
> cat /var/log/fsck/checkfs
Log of fsck -C -R -A -a
Thu Jul 24 16:51:50 2008

fsck 1.40.8 (13-Mar-200
[color=red]/dev/sdb2 is mounted. e2fsck: Cannot continue, aborting.[/color]


/dev/sdb1: clean, 14/424320 files, 55400/1690833 blocks
fsck died with exit status 8


I think that is your problem,it is trying to run fsck on a mounted partition which I think is your root partition,as that is what is booting to.
I am not sure what to suggest as your system is totally non standard.Your fstab file doesn't specify a root partition,and what is the /dev/sdb1 partition?


> Error: Unable to open /dev/fd0 - unrecognised disk label.
Warning: Unable to open /dev/scd0 read-write (Read-only file system). /dev/scd0 has been opened read-only.
Error: Unable to open /dev/scd0 - unrecognised disk label.


What is that all about? fdisk should not produce this output.

If I were you I would seriously consider a reinstall of your system to tidy up your partitions and files and get rid of the unused installs.

Can you still boot into windows?
can you post output of ```
cat /etc/mtab
```

Thanks.

---

### Post by lighthouseca on 2008-07-25
yes i can still boot windows. I changed fstab to change boot order of devices and changed last parameter for sdb1 from a 1 to 2 and that solved the boot error. if this file has problems i would appreciate any advice other wise i think its fixed
 the only problem I am running into now has to do with ownership  with apt-get install as below
Reading package lists... Done
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root
 
here is output etc/mtab
cat /etc/mtab
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.24-19-generic/volatile tmpfs rw 0 0
/dev/sdb2 /media/sdb2 ext3 rw,0 0 0
securityfs /sys/kernel/security securityfs rw 0 0


Obviously I'm feeling my way around and am thankfull for any advice you may have to offer
 thanks to all

---

### Post by geirha on 2008-07-28
> **lighthouseca said:**
> yes i can still boot windows. I changed fstab to change boot order of devices and changed last parameter for sdb1 from a 1 to 2 and that solved the boot error. if this file has problems i would appreciate any advice other wise i think its fixed
 the only problem I am running into now has to do with ownership  with apt-get install as below
Reading package lists... Done
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root


Did you forget to put sudo infront of that command? ```
sudo apt-get install pkg
```

---

