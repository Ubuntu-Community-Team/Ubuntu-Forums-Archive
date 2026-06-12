---
title: "Coping Extened Partition to Primary and Removing Extended"
date: 2009-02-10
forum: Installation &amp; Upgrades
---

### Post by NeoZiggy on 2009-02-10
I've seamed to have made a really mess here. I'll try to provide all the info I the best I can:
After installing Ubuntu Hardy (months ago) and the GRUB bootloader I was no longer able to boot into Windows (actually a blessing). Unfortunately, I only allotted Ubuntu 10GB of space. I have recently used GParted to resize the Linux partition.

However, I would like to do away with the remaining NTFS partition, but it is the first partition on the drive and for some reason **the Linux partition and it's swap are in an "Extended Partition"**. There is no reason for this, I have a fairly new computer and it is only an 80GB drive.

I had read that a computer will not boot if there is only an extended partition, and no primary. The other boggle here is the operating system is on SDB and not SDA (I may have my master/slave cables mixed), but thats besides the point.

Can I, using GParted LiveCD, copy the Linux partition and Swap to the unallocated space, outside of the extended partition, after deleting the primary partition, as long as it is flagged as boot?

_Here is some info:_
 => Grub is installed in the MBR of /dev/sda and looks on boot drive #105 in 
    partition #225 for /e8del.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

Disk /dev/sda: 45.0 GB, 45020602368 bytes
255 heads, 63 sectors/track, 5473 cylinders, total 87930864 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x435919c8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63     2056319     1028128+   7  HPFS/NTFS
/dev/sda3         2056320    87923744    42933712+   7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xed00ed00

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    89963999    44981968+   7  HPFS/NTFS
/dev/sdb2        89964000   156296384    33166192+   5  Extended
/dev/sdb5        89964063   155236094    32636016   83  Linux
/dev/sdb6       155236158   156296384      530113+  82  Linux swap / Solaris

As you can see, the first drive, SDA, is not the drive with the OS. The drive only has mp3s on it. When GRUB boots into Ubuntu this is the setting from the boot menu: *root (hd0,4)*. I'm guessing the GRUB on SDA is from an old installation (I changed BIOS settings to boot from that drive and it prints GRUB over and over on an endless loop).

I just want to, with out reformatting, get rid of that partition and let Ubuntu have the whole drive. Since the GRUB that boots is on SDB's MBR if I remove that leading partition I'm assuming it won't boot. So would I have to burn a copy of Ubuntu, remove that partition, then reinstall GRUB? I really don't want to touch anything with out some input on this. Thanks.

---

### Post by caljohnsmith on 2009-02-10
> **NeoZiggy said:**
> 
I had read that a computer will not boot if there is only an extended partition, and no primary. 
That is only true if you are using an OS like Windows that requires a primary partition for its boot files, and that's solely because of the limitations of the Windows boot loader, i.e. the Windows boot loader can only boot a primary partition. But since you are using Grub, you don't need any primary partitions; you could delete your Windows sdb1 primary partition and have just one extended partition on the HDD with your linux partitions, and you should be fine. The only small thing to watch out for is that some BIOSes won't boot a drive unless one of the partitions listed in the MBR is marked as bootable, so if you have a BIOS like that, you can simply mark your extended partition as bootable and your BIOS should be happy. Or if you really want to make your sdb5 Linux partition a primary partition, we can do that by simply changing your partition table; fortunately there's no need to copy or move your partitions around in order to turn your sdb5 linux partition into a primary partition. Let me know if you really want to make sdb5 a primary partition, because if you do, please post:
```
sudo sfdisk -d
```
And we can work from there.

---

### Post by NeoZiggy on 2009-02-10
I started downloading the Ubuntu CD anyway, always good to have. GParted makes it apear that there is still around 40gb of data on that partition, however when I "gksudo nautilus" there is nothing but under 1MB in a Windows recycling folder that I can not delete: "There was an error deleting 2.0.0.0__b03f5f7f11d50a3a. Error removing file: Operation not supported".

```

# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size=  2056257, Id= 7, bootable
/dev/sda2 : start=        0, size=        0, Id= 0
/dev/sda3 : start=  2056320, size= 85867425, Id= 7
/dev/sda4 : start=        0, size=        0, Id= 0
# partition table of /dev/sdb
unit: sectors

/dev/sdb1 : start=       63, size= 89963937, Id= 7, bootable
/dev/sdb2 : start= 89964000, size= 66332385, Id= 5
/dev/sdb3 : start=        0, size=        0, Id= 0
/dev/sdb4 : start=        0, size=        0, Id= 0
/dev/sdb5 : start= 89964063, size= 65272032, Id=83
/dev/sdb6 : start=155236158, size=  1060227, Id=82

```
Thanks for replying, and let me know what to do next. :)

---

### Post by caljohnsmith on 2009-02-10
OK, since you posted that output, does that mean you definitely want to turn your sdb5 logical partition into a primary partition? If so, do you also want to delete the sdb1 NTFS partition I assume? If that is true, how about downloading the attached "partition_table.txt" file to your Ubuntu desktop, and then do:
```
sudo sfdisk --no-reread -f /dev/sdb -O ~/Desktop/sdb_sectors_modified.save < ~/Desktop/partition_table.txt
```
And please post the output. The above command will create a backup of the few sectors being modified as a small "sdb_sectors_modified.save" file on your desktop, so if for some reason anything were to go wrong, we can easily restore your original partition table with that file. Therefore, please copy that file to a different drive, or you could for instance save it to your email account or something like that. Next boot your Live CD, and please post the output of:
```
sudo fdisk -lu
sudo sfdisk -d
sudo parted /dev/sdb print
sudo mount /dev/sdb1 /mnt && cat /mnt/boot/grub/menu.lst
```
And then to reinstall Grub to the MBR of the sdb drive so that it points to the new sdb1 Ubuntu partition:
```
sudo grub
grub> root (hd1,0)
grub> setup (hd1)
grub> quit
```
And please post the output before you type "quit". We can work from there.

---

### Post by NeoZiggy on 2009-02-10
Yes, I want to remove all leftover window scum. I'll keep that on my gmail account and on my other HD.

```

Disk /dev/sdb: 9729 cylinders, 255 heads, 63 sectors/track
Old situation:
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sdb1   *      0+   5599    5600-  44981968+   7  HPFS/NTFS
/dev/sdb2       5600    9728    4129   33166192+   5  Extended
/dev/sdb3          0       -       0          0    0  Empty
/dev/sdb4          0       -       0          0    0  Empty
/dev/sdb5       5600+   9662    4063-  32636016   83  Linux
/dev/sdb6       9663+   9728      66-    530113+  82  Linux swap / Solaris
New situation:
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sdb1   *  89964063 155236094   65272032  83  Linux
/dev/sdb2     155236095 156296384    1060290   5  Extended
/dev/sdb3             0         -          0   0  Empty
/dev/sdb4             0         -          0   0  Empty
/dev/sdb5     155236158 156296384    1060227  82  Linux swap / Solaris
Warning: partition 1 does not start at a cylinder boundary
Successfully wrote the new partition table

Re-reading the partition table ...
BLKRRPART: Device or resource busy
The command to re-read the partition table failed
Reboot your system now, before using mkfs

If you created or changed a DOS partition, /dev/foo7, say, then use dd(1)
to zero the first 512 bytes:  dd if=/dev/zero of=/dev/foo7 bs=512 count=1
(See fdisk(8).)

```

Just to confirm: I am running Ubuntu from my HD right now. So I'll need to to burn the liveCD, boot up with it, and then run those commands and post the outputs?

---

### Post by caljohnsmith on 2009-02-10
Yes, most likely you will need to boot the Live CD to finish the process. But while you are burning the Live CD, how about trying those Grub commands while you are still in your Ubuntu install and let me know if they complete successfully. Also please post:
```
cat /boot/grub/menu.lst
```

---

### Post by NeoZiggy on 2009-02-10
All ready on the live CD ;)

```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 45.0 GB, 45020602368 bytes
255 heads, 63 sectors/track, 5473 cylinders, total 87930864 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x435919c8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63     2056319     1028128+   7  HPFS/NTFS
/dev/sda3         2056320    87923744    42933712+   7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xed00ed00

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *    89964063   155236094    32636016   83  Linux
/dev/sdb2       155236095   156296384      530145    5  Extended
/dev/sdb5       155236158   156296384      530113+  82  Linux swap / Solaris

```
```
ubuntu@ubuntu:~$ sudo sfdisk -d
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size=  2056257, Id= 7, bootable
/dev/sda2 : start=        0, size=        0, Id= 0
/dev/sda3 : start=  2056320, size= 85867425, Id= 7
/dev/sda4 : start=        0, size=        0, Id= 0
# partition table of /dev/sdb
unit: sectors

/dev/sdb1 : start= 89964063, size= 65272032, Id=83, bootable
/dev/sdb2 : start=155236095, size=  1060290, Id= 5
/dev/sdb3 : start=        0, size=        0, Id= 0
/dev/sdb4 : start=        0, size=        0, Id= 0
/dev/sdb5 : start=155236158, size=  1060227, Id=82

```
```
ubuntu@ubuntu:~$ sudo sfdisk -d
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size=  2056257, Id= 7, bootable
/dev/sda2 : start=        0, size=        0, Id= 0
/dev/sda3 : start=  2056320, size= 85867425, Id= 7
/dev/sda4 : start=        0, size=        0, Id= 0
# partition table of /dev/sdb
unit: sectors

/dev/sdb1 : start= 89964063, size= 65272032, Id=83, bootable
/dev/sdb2 : start=155236095, size=  1060290, Id= 5
/dev/sdb3 : start=        0, size=        0, Id= 0
/dev/sdb4 : start=        0, size=        0, Id= 0
/dev/sdb5 : start=155236158, size=  1060227, Id=82
ubuntu@ubuntu:~$ sudo parted /dev/sdb print

Disk /dev/sdb: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      46.1GB  79.5GB  33.4GB  primary   ext3         boot 
 2      79.5GB  80.0GB  543MB   extended                    
 5      79.5GB  80.0GB  543MB   logical   linux-swap        

Information: Don't forget to update /etc/fstab, if necessary.

```
```
ubuntu@ubuntu:~$ sudo cat /mnt/boot/grub/menu.lst
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color light-gray/black white/black

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=a9c0101d-22eb-4a7f-93eb-b1244cd45026 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,4)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-23-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=a9c0101d-22eb-4a7f-93eb-b1244cd45026 ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=a9c0101d-22eb-4a7f-93eb-b1244cd45026 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=a9c0101d-22eb-4a7f-93eb-b1244cd45026 ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=a9c0101d-22eb-4a7f-93eb-b1244cd45026 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
##title		Other operating systems:
##root

```
Yea, I edited the menu.lst before. I also closed the terminal before copying, so it was mounted already. I redid the 2nd part for the output.
Shall I do GRUB now?

---

### Post by caljohnsmith on 2009-02-10
Yes, run the Grub commands now, and also you'll need to modify your menu.lst. If you still have sdb1 mounted on /mnt, just do:
```
gksudo gedit /mnt/boot/grub/menu.lst
```
And change all your Ubuntu entries to use (hd0,0) rather than (hd0,4). Also be sure to change the "# groot=(hd0,4)" line to use (hd0,0) too. Let me know how the Grub commands go.

---

### Post by NeoZiggy on 2009-02-10
```
grub> root (hd1,0)

grub> setup (hd1)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd1)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd1) (hd1)1+16 p (hd1,0)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

```
And I made the changes in menu.lst. Has the extra space already been added to the Ubuntu partition, or is that the next step?

BTW, is it supposed to be hd(1,0) (like above), and then hd(0,0) in menu.lst like you said? I don't mean to question you, I just don't understand it :p

---

### Post by caljohnsmith on 2009-02-10
That's good, it looks like Grub installed just fine. How about booting into your Ubuntu install just to confirm everything is OK, and if so, you can boot your Live CD again, run gparted (System > Admin > Partition Editor), and you can use that to enlarge the Ubuntu sdb1 partition from the beginning to use all that space that Windows had. Let me know how that goes.

P.S. Yes, the menu.lst should use (hd0,0), because when you boot the sdb drive, it is then (hd0) on start up.

---

### Post by NeoZiggy on 2009-02-10
Ok, I'll give it a go!

---

### Post by NeoZiggy on 2009-02-10
Everything worked perfectly. Thank you so much for your help! I would have never figured that out on my own. :KS

---

### Post by caljohnsmith on 2009-02-10
Great, glad to hear everything is working OK. Cheers and enjoy Ubuntu. :)

---

### Post by cr0atian on 2009-03-03
Mr. caljohnsmith, I would like to ask for some help getting the same thing done on my computer. Some time ago I virtualized my Windows XP Pro partition using VMWare tools and since then I'm running Windows on my Linux VMWare 2.0 server host when I need it. I'm now left with a small primary bootable NTFS partition of only 3.5 GB in size that I'd like to get rid of in favor of the Linux partition, which I'd like to also make bootable. Please look at the output I prepared for you and tell me what you think?

```
sudo sfdisk -d
```

# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size=    80262, Id=de
/dev/sda2 : start=    80325, size=  7181055, Id= 7, bootable
/dev/sda3 : start=  7261380, size=146400345, Id=83
/dev/sda4 : start=153661725, size=  2586465, Id= 5
/dev/sda5 : start=153661788, size=  2586402, Id=82

```
sudo fdisk -lu
```

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       80324       40131   de  Dell Utility
/dev/sda2   *       80325     7261379     3590527+   7  HPFS/NTFS
/dev/sda3         7261380   153661724    73200172+  83  Linux
/dev/sda4       153661725   156248189     1293232+   5  Extended
/dev/sda5       153661788   156248189     1293201   82  Linux swap / Solaris

```
sudo parted /dev/sda print
```
Model: ATA SAMSUNG HD080HJ/ (scsi)
Disk /dev/sda: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      32.3kB  41.1MB  41.1MB  primary   fat16             
 2      41.1MB  3718MB  3677MB  primary   ntfs         boot 
 3      3718MB  78.7GB  75.0GB  primary   ext3              
 4      78.7GB  80.0GB  1324MB  extended                    
 5      78.7GB  80.0GB  1324MB  logical   linux-swap        

**The relevant portion of my menu.lst looks like this:**

[INDENT]## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-12-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.27-12-generic root=UUID=5586fb58-ae76-4006-94fa-8d1408296457 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-12-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-12-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.27-12-generic root=UUID=5586fb58-ae76-4006-94fa-8d1408296457 ro  single
initrd		/boot/initrd.img-2.6.27-12-generic

title		Ubuntu 8.10, kernel 2.6.27-11-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=5586fb58-ae76-4006-94fa-8d1408296457 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=5586fb58-ae76-4006-94fa-8d1408296457 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Dell Utility Partition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
makeactive
chainloader	+1[/INDENT]

---

### Post by NeoZiggy on 2009-03-05
I was checking over my old posts and bumped into this one. I am happy to see some one else is looking to get rid of windows. I did a quick search on google, maybe this will help you:
[http://www.chutneytech.com/modifying-a-vmware-server-virtual-disk-configuration/]("http://www.chutneytech.com/modifying-a-vmware-server-virtual-disk-configuration/")

I would hope that some one else could give you better advice. I'm not sure if that is what you were looking for or not.

---

### Post by cr0atian on 2009-03-05
NeoZiggy,

Thank you for your time and your support, but that page doesn't explain how to get rid of a Windows partition. It only explains (to a certain degree) how to manipulate a VMWare virtual disk size. I am familiar with GParted and VMWare, but what I'm not sure about is how to get rid of a no longer needed Windows XP (NTFS) partition without harming my Ubuntu installation and bootability (Grub) on the same hard disk drive. I need some better instructions on how to do it similar to those that caljohnsmith gave you. I hope that he still monitors this thread from time to time.

---

### Post by NeoZiggy on 2009-03-06
This is what I did, I'm not telling you to do it, just sharing my experience:
I'd burned a copy of the gParted CD. And the Ubuntu CD just in case.

1) Copied everything I wanted from Windows (my doc, ect), then deleted any remaining junk, including hidden files/folders like Recycle. This took me a bit because I had to shrink Windows in order to fit things to the Ubuntu partition.
2) Edited GRUB's menu.lst.
3) Booted into the gParted CD. Deleted the windows partition, and grow Ubuntu to fill the drive. Or maybe I had to create a new partition in the space and merged the two... I forget now. I made sure that Linux was now the bootable partition, although it already was.

I knew I could always edit the boot settings from the GRUB menu by pressing E. Also from the live CD you can skip the install process and reinstall GRUB (search for reinstalling GRUB on the forum, it will tell you how to do this without reinstalling Ubuntu).

---

### Post by NeoZiggy on 2009-03-06
> **cr0atian said:**
> Mr. caljohnsmith
Have you send him a PM?

---

### Post by cr0atian on 2009-03-06
Thank you, I just did.

---

