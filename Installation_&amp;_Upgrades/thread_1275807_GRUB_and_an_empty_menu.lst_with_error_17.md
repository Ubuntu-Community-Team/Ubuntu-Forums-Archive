---
title: "GRUB and an empty menu.lst with error 17"
date: 2009-09-26
forum: Installation &amp; Upgrades
---

### Post by daturk on 2009-09-26
Hi there!

Im having trouble doing a fresh install of ubuntu 9.04 on a fresh 500 gig HDD. I get the somewhat infamous error 17 upon Bootup.

Here is my fdisk list

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007b3fd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1867    14996646   83  Linux
/dev/sda2            1868       60801   473387355    5  Extended
/dev/sda5            1868        2178     2498076   82  Linux swap / Solaris
/dev/sda6            2179       60801   470889216   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x734d4f52

When I try to look at the /etc/menu.lst its empty.

My motherboard is an Asus K8N4-E DELUXE with an onboard silicone image raid controller, not sure if that could cause problems like it did with my XP install a while ago. I needed third party drivers so xp could detect my drives.

Any other info that I could provide?

Thanks for listening! err..reading...

---

### Post by oldos2er on 2009-09-26
"When I try to look at the /etc/menu.lst its empty."

 The correct location is /boot/grub/menu.lst

---

### Post by stlsaint on 2009-09-26
+1 oldos2er...correct you are looking in the wrong location for menu.lst

run this in terminal:
> gksudo gedit /boot/grub/menu.lst

then post results here.

---

### Post by daturk on 2009-09-26
Cheers oldos2er. Still nothing there though. I browsed the grub folder and all there is is the device map file.

(fd0)	/dev/fd0
(hd0)	/dev/sda
(hd1)	/dev/sdb


Am I installing grub to the wrong place? I chose hd0.

Cheers

---

### Post by rreese6 on 2009-09-26
you should have chosen the install on the MBR (Boot Record)
you could just do it again. or run grub-install on /dev/sda
(of course you need to boot off of the LiveCD)
Not sure if grub-install is on livecd or not.
if not just sudo apt-get install grub-install

---

### Post by daturk on 2009-09-26
I have a feeling I dont have an MBR. I used KillDisk to wipe my drives and Im sure I only wiped the partitions and not the whole drive but Im probably wrong. Whoops... #-o:oops:

Thanks rreese6, I feel we're getting somewhere now.

---

### Post by rreese6 on 2009-09-26
Every body has an MBR....
Just to make it easy on you.
put in your LiveCD, reinstall
make the installer use the whole drive.
and install grub (Bootloader) to the MBR of hd0

when you are finished, come back, laugh, and have a cup of tea.

oh then mark the post as solved..

---

### Post by presence1960 on 2009-09-26
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

We can guess all day that it may be this or that. this script will show us exactly your setup & boot process.

---

### Post by letank on 2009-09-29
Almost an hijack, but I have the same issue, after I did a "dd" to copy  the original 40GB to a 160GB. I have both windoze XP pro and ubuntu 7.04, I know, I need to upgrade but missed the timeline, and still need M$ to run the gps.

I also had grub error 17, and had to restart twice to be able to boot the live cd which is a 8.04 which works as I installed 8.04 on my Dad's laptop.

I can see the XP partition, access it, write and copy files to it.

Running "sudo grub"
grub> find /boot/grub/stage1, or stage2 return "Error 15: file not found"

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3b6e3b6d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2823    22675716    7  HPFS/NTFS
/dev/sda2            2824        3066     1951897+  82  Linux swap / Solaris
/dev/sda3            3067        4864    14442435   83  Linux
ubuntu@ubuntu:~$ 

This is an exact copy of my 40GB

When I checked with Gparted sda2 and sda3 are listed as unknown

pict enclosed

So I ran your script:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /ubuntu/winboot/menu.lst /boot.ini /ntldr 
                       /NTDETECT.COM /wubildr.mbr /ubuntu/winboot/wubildr.mbr

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda3: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3b6e3b6d

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    45,351,494    45,351,432   7 HPFS/NTFS
/dev/sda2          45,351,495    49,255,289     3,903,795  82 Linux swap / Solaris
/dev/sda3          49,255,290    78,140,159    28,884,870  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="880049F70049ECAE" TYPE="ntfs" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.24-23-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.24-23-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda1 on /media/disk type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)


======================== sda1/ubuntu/winboot/menu.lst: ========================

debug off
hiddenmenu
default 0
timeout 0
fallback 1

title find /ubuntu/disks/boot/grub/menu.lst
	find --set-root --ignore-floppies /ubuntu/disks/boot/grub/menu.lst
	configfile /ubuntu/disks/boot/grub/menu.lst

title find /ubuntu/install/boot/grub/menu.lst
	fallback 2
	find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst
	configfile /ubuntu/install/boot/grub/menu.lst

title find /menu.lst
	fallback 3
	find --set-root --ignore-floppies /menu.lst
	configfile /menu.lst

title find /boot/grub/menu.lst
	fallback 4
	find --set-root --ignore-floppies /boot/grub/menu.lst
	configfile /boot/grub/menu.lst

title find /grub/menu.lst
	fallback 5
	find --set-root --ignore-floppies /grub/menu.lst
	configfile /grub/menu.lst

title commandline
	commandline

title reboot
	reboot

title halt
	halt

================================ sda1/boot.ini: ================================

[boot loader]

timeout=15

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

c:\wubildr.mbr="Ubuntu"

```

Thanks for the tips.

---

### Post by presence1960 on 2009-09-29
It looks like your sda2 & sda3 are unmountable. I would just do a clean install. You also had wubi installed at one time, or is it still installed? The reference to it is still in boot.ini.

---

### Post by letank on 2009-09-29
Thanks presence1960, the other question is that I am not sure why I do not get the choice of OS, is this an issue with the MBR? Should I run the XP cd first?

Also on which partition is the MBR?

---

### Post by presence1960 on 2009-09-29
> **letank said:**
> Thanks presence1960, the other question is that I am not sure why I do not get the choice of OS, is this an issue with the MBR? Should I run the XP cd first?

Also on which partition is the MBR?

MBR is not on a partition. It is on the very beginning of a hard disk.

I would restore XP to MBR first so you at least can boot into windows if need be, then reinstall Ubuntu. You will need the XP install disk. Boot from it and follow the instructions for XP [here]("http://ubuntuforums.org/showthread.php?t=1014708").

---

### Post by letank on 2009-09-29
> **presence1960 said:**
> MBR is not on a partition. It is on the very beginning of a hard disk.

I would restore XP to MBR first so you at least can boot into windows if need be, then reinstall Ubuntu. You will need the XP install disk. Boot from it and follow the instructions for XP [here]("http://ubuntuforums.org/showthread.php?t=1014708").


Cool, this is a fun search and repair day.
I installed the original disk, to find all the needed infos. I was trying to avoid slapping XP disks around using this thread

[http://ubuntuforums.org/archive/index.php/t-874643.html](http://ubuntuforums.org/archive/index.php/t-874643.html)

So now I now the all the root is in the 3rd partition(hd0,2) for Ubuntu and the first for XP, the second is the swap. This is in the 40GB disk, not the 160GB that is the subject of the topic here.

Thank you again for the link.

And I have no idea about "wubi" hummmm?

---

### Post by presence1960 on 2009-09-29
> **letank said:**
> 

And I have no idea about "wubi" hummmm?

from your boot info script output:

```
================================ sda1/boot.ini: ================================

[boot loader]

timeout=15

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

[COLOR="Red"]c:\wubildr.mbr="Ubuntu"[/COLOR]


```

for that to be there (red) in boot.ini you must have installed Ubuntu with wubi, which is a way to try Ubuntu from inside windows.

here is a link for info on wubi: [https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

---

### Post by letank on 2009-09-30
> **presence1960 said:**
> from your boot info script output:

```
================================ sda1/boot.ini: =============

[boot loader]

timeout=15

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

[COLOR="Red"]c:\wubildr.mbr="Ubuntu"[/COLOR]


```

for that to be there (red) in boot.ini you must have installed Ubuntu with wubi, which is a way to try Ubuntu from inside windows.

here is a link for info on wubi: [https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

Thanks, I am learning everyday, and I just use an installer disk, in fact it says : "NOTE: Hibernation is not supported when installing Ubuntu via Wubi" which I found out.

Time for a clean install.

---

### Post by daturk on 2009-10-04
Sorry I havn't been replying but my pld agp card decided to call it quits and I had to find an el cheapo replacement.

Thanks presence1960 for the script, here are the results. 





============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No known boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0007b3fd

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    29,993,354    29,993,292  83 Linux
/dev/sda2          29,993,355   976,768,064   946,774,710   5 Extended
/dev/sda5          29,993,418    34,989,569     4,996,152  82 Linux swap / Solaris
/dev/sda6          34,989,633   976,768,064   941,778,432  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x734d4f52

Partition  Boot         Start           End          Size  Id System



blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="e8522d07-1402-4ac8-82af-71fb4d616cbb" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="51902bf1-cade-4322-95ff-7c641906cb56" TYPE="swap" 
/dev/sda6: UUID="ac03accb-2c5a-43b6-98cc-df6dc3081505" SEC_TYPE="ext2" TYPE="ext3" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


=========================== sda1/boot/grub/menu.lst: ===========================

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
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

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
# kopt=root=UUID=e8522d07-1402-4ac8-82af-71fb4d616cbb ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=e8522d07-1402-4ac8-82af-71fb4d616cbb

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

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

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

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		e8522d07-1402-4ac8-82af-71fb4d616cbb
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=e8522d07-1402-4ac8-82af-71fb4d616cbb ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		e8522d07-1402-4ac8-82af-71fb4d616cbb
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=e8522d07-1402-4ac8-82af-71fb4d616cbb ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		e8522d07-1402-4ac8-82af-71fb4d616cbb
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=e8522d07-1402-4ac8-82af-71fb4d616cbb /               ext3    relatime,errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=ac03accb-2c5a-43b6-98cc-df6dc3081505 /home           ext3    relatime        0       2
# swap was on /dev/sda5 during installation
UUID=51902bf1-cade-4322-95ff-7c641906cb56 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .5GB: boot/grub/menu.lst
    .6GB: boot/grub/stage2
    .6GB: boot/initrd.img-2.6.28-11-generic
    .5GB: boot/vmlinuz-2.6.28-11-generic
    .6GB: initrd.img
    .5GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdb

00000000  6f 67 69 63 61 6c 20 64  72 69 76 65 20 69 6e 66  |ogical drive inf|
00000010  6f 72 6d 61 74 69 6f 6e  2c 20 73 65 61 72 63 68  |ormation, search|
00000020  20 00 66 6f 72 20 66 69  6c 65 73 2c 20 70 72 65  | .for files, pre|
00000030  76 69 65 77 20 61 6e 64  20 63 6f 70 79 20 6e 6f  |view and copy no|
00000040  6e 2d 64 65 6c 65 74 65  64 20 66 69 6c 65 73 20  |n-deleted files |
00000050  61 6e 64 20 00 64 69 72  65 63 74 6f 72 69 65 73  |and .directories|
00000060  20 66 72 6f 6d 20 4e 54  46 53 20 74 6f 20 46 41  | from NTFS to FA|
00000070  54 20 70 61 72 74 69 74  69 6f 6e 2e 00 00 00 28  |T partition....(|
00000080  62 29 20 52 45 44 49 53  54 52 49 42 55 54 49 4f  |b) REDISTRIBUTIO|
00000090  4e 20 4f 46 20 46 52 45  45 20 43 4f 50 59 2e 20  |N OF FREE COPY. |
000000a0  20 49 66 20 79 6f 75 20  61 72 65 20 75 73 69 6e  | If you are usin|
000000b0  67 20 00 46 52 45 45 20  53 4f 46 54 57 41 52 45  |g .FREE SOFTWARE|
000000c0  20 79 6f 75 20 6d 61 79  20 6d 61 6b 65 20 63 6f  | you may make co|
000000d0  70 69 65 73 20 6f 66 20  74 68 65 20 46 52 45 45  |pies of the FREE|
000000e0  20 53 4f 46 54 57 41 52  45 00 61 73 20 79 6f 75  | SOFTWARE.as you|
000000f0  20 77 69 73 68 3b 20 67  69 76 65 20 65 78 61 63  | wish; give exac|
00000100  74 20 63 6f 70 69 65 73  20 6f 66 20 74 68 65 20  |t copies of the |
00000110  6f 72 69 67 69 6e 61 6c  20 46 52 45 45 00 53 4f  |original FREE.SO|
00000120  46 54 57 41 52 45 20 74  6f 20 61 6e 79 6f 6e 65  |FTWARE to anyone|
00000130  3b 20 61 6e 64 20 64 69  73 74 72 69 62 75 74 65  |; and distribute|
00000140  20 74 68 65 20 46 52 45  45 20 53 4f 46 54 57 41  | the FREE SOFTWA|
00000150  52 45 20 00 69 6e 20 69  74 73 20 75 6e 6d 6f 64  |RE .in its unmod|
00000160  69 66 69 65 64 20 66 6f  72 6d 20 76 69 61 20 65  |ified form via e|
00000170  6c 65 63 74 72 6f 6e 69  63 20 6d 65 61 6e 73 20  |lectronic means |
00000180  28 49 6e 74 65 72 6e 65  74 2c 20 00 42 42 53 27  |(Internet, .BBS'|
00000190  73 2c 20 53 68 61 72 65  77 61 72 65 20 64 69 73  |s, Shareware dis|
000001a0  74 72 69 62 75 74 69 6f  6e 20 6c 69 62 72 61 72  |tribution librar|
000001b0  69 65 73 2c 20 43 44 2d  52 4f 4d 73 2c 20 00 00  |ies, CD-ROMs, ..|
000001c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Cheers

---

### Post by presence1960 on 2009-10-04
everything looks good from the script. I would reboot & go into BIOS and make sure sda is set to boot first in the hard disk boot order. if you have sdb booting first you will get a GRUB error. Try that & report back please.

---

### Post by daturk on 2009-10-04
the bios seems set up right. So i tried unplugging the second drive altogether and got a disk boot error... And then I remembered I had a stripped raid array set up from my old XP installation before i KilledDisked my drives. Would that effect the instalation? Should I try a fresh install with just the one drive? It wont hurt to delete that raid set either.

Cheers for the help, now I know its not a ubuntu error I can look elsewhere. These forums rock.:guitar:

---

### Post by presence1960 on 2009-10-04
> **daturk said:**
> the bios seems set up right. So i tried unplugging the second drive altogether and got a disk boot error... And then I remembered I had a stripped raid array set up from my old XP installation before i KilledDisked my drives. Would that effect the instalation? Should I try a fresh install with just the one drive? It wont hurt to delete that raid set either.

Cheers for the help, now I know its not a ubuntu error I can look elsewhere. These forums rock.:guitar:
That would be the problem. if you want to use a RAID setup for Ubuntu use the alternate text based installer. it has support for RAID unlike the Live CD. Get it [here]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate").

or just get rid of the RAID. Either way will work.

---

### Post by daturk on 2009-10-04
Ok, It's all good now!

How do I mark this as solved?

Thanks again for everyones help!:P

---

### Post by presence1960 on 2009-10-05
> **daturk said:**
> Ok, It's all good now!

How do I mark this as solved?

Thanks again for everyones help!:P

Under Thread Tools top right of page choose "Mark as "Solved".

---

