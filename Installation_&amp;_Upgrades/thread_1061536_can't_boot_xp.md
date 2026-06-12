---
title: "can't boot xp"
date: 2009-02-05
forum: Installation &amp; Upgrades
---

### Post by ray field on 2009-02-05
I installed over an old Suse setup, using a memory key formatted live to a SCSI disk.  after getting an Error 2 during Stage 1 of grub, I used Super Grub to fix things, sort of, and have booted successfully to Intrepid, updated, etc. 

however, I can't boot XP.  here is "results.txt" from the boot info script:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sdc and looks on the same drive 
    in partition #10 for /boot/grub/stage2 and /boot/grub/menu.lst.

sdc1: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdc2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdc3: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdc4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdc5 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files/dirs:   

sdc6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdc6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdc7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdc7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdc8: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdc9: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc10: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sdc10 and 
                       looks at sector 102028308 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sdc. Stage2 looks on partition #10 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdc11: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sdc: _____________________________________________________________________

Disk /dev/sdc: 73.5 GB, 73543163904 bytes
255 heads, 63 sectors/track, 8941 cylinders, total 143638992 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xdf5ee800

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63        16,064        16,002   a OS/2 Boot Manager
/dev/sdc2    *         16,065     4,225,094     4,209,030   7 HPFS/NTFS
/dev/sdc3           4,225,095     6,281,414     2,056,320  17 Hidden HPFS/NTFS
/dev/sdc4           6,281,415   143,637,164   137,355,750   5 Extended
/dev/sdc5           6,281,478    22,667,714    16,386,237   7 HPFS/NTFS
/dev/sdc6          22,667,778    43,150,589    20,482,812   7 HPFS/NTFS
/dev/sdc7          43,150,653    73,882,934    30,732,282   7 HPFS/NTFS
/dev/sdc8         139,540,653   143,637,164     4,096,512  82 Linux swap / Solaris
/dev/sdc9          73,882,998    78,091,964     4,208,967  82 Linux swap / Solaris
/dev/sdc10         78,092,028   103,137,299    25,045,272  83 Linux
/dev/sdc11        103,137,363   139,540,589    36,403,227  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sdc2: UUID="F4DC5728DC56E480" TYPE="ntfs" 
/dev/sdc5: UUID="9454131E541302A2" TYPE="ntfs" 
/dev/sdc6: UUID="9A5CEC9D5CEC7603" LABEL="XP Apps" TYPE="ntfs" 
/dev/sdc7: UUID="3A485F62485F1BC7" LABEL="STUFF" TYPE="ntfs" 
/dev/sdc9: UUID="61d71c6d-09e1-42ef-8bd6-bdfbb077054d" TYPE="swap" 
/dev/sdc10: UUID="7b2666ae-c50a-4e66-89bf-7ee746b0d57b" TYPE="ext3" 
/dev/sdc11: UUID="75872ce8-da9e-4238-af40-155696dc44cc" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/sdc10 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-11-generic/volatile type tmpfs (rw,mode=755)
/dev/sdc11 on /home type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/raphael/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=raphael)

================================ sdc2/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(4)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(4)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect /usepmtimer


========================== sdc10/boot/grub/menu.lst: ==========================

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
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

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
# kopt=root=UUID=7b2666ae-c50a-4e66-89bf-7ee746b0d57b ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=7b2666ae-c50a-4e66-89bf-7ee746b0d57b

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

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		7b2666ae-c50a-4e66-89bf-7ee746b0d57b
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=7b2666ae-c50a-4e66-89bf-7ee746b0d57b ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		7b2666ae-c50a-4e66-89bf-7ee746b0d57b
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=7b2666ae-c50a-4e66-89bf-7ee746b0d57b ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		7b2666ae-c50a-4e66-89bf-7ee746b0d57b
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=7b2666ae-c50a-4e66-89bf-7ee746b0d57b ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		7b2666ae-c50a-4e66-89bf-7ee746b0d57b
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=7b2666ae-c50a-4e66-89bf-7ee746b0d57b ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		7b2666ae-c50a-4e66-89bf-7ee746b0d57b
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdd2
title		Windows XP Media Center Edition
root		(hd1,1)
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


=============================== sdc10/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdd10
UUID=7b2666ae-c50a-4e66-89bf-7ee746b0d57b /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdd11
UUID=75872ce8-da9e-4238-af40-155696dc44cc /home           ext3    relatime        0       2
# /dev/sdd9
UUID=61d71c6d-09e1-42ef-8bd6-bdfbb077054d none            swap    sw              0       0

=================== sdc10: Location of files loaded by Grub: ===================


  52.2GB: boot/grub/menu.lst
  52.2GB: boot/grub/stage2
  51.8GB: boot/initrd.img-2.6.27-11-generic
  51.9GB: boot/initrd.img-2.6.27-7-generic
  51.8GB: boot/vmlinuz-2.6.27-11-generic
  51.8GB: boot/vmlinuz-2.6.27-7-generic
  51.8GB: initrd.img
  51.9GB: initrd.img.old
  51.8GB: vmlinuz
  51.8GB: vmlinuz.old

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdc3

00000000  f6 f6 f6 f6 f6 f6 f6 f6  f6 f6 f6 f6 f6 f6 f6 f6  |................|
*
00000200

Unknown BootLoader  on sdc8

00000000  f6 f6 f6 f6 f6 f6 f6 f6  f6 f6 f6 f6 f6 f6 f6 f6  |................|
*
00000200


=======Devices which don't seem to have a corresponding hard drive==============

 sda .
 sdb .

=============================== StdErr Messages: ===============================

boot_info_script024.sh: line 1043: [: =: unary operator expected
boot_info_script024.sh: line 1043: [: =: unary operator expected
boot_info_script024.sh: line 1043: [: =: unary operator expected
```

---

### Post by cdtech on 2009-02-05
Try changing your Windows block like below and see if you can boot into Windows:
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdd2
title		Windows XP Media Center Edition
root		(hd2,1)
chainloader	+1

```
sda = hd0
sdb = hd1
sdc = hd2
ect.....

---

### Post by caljohnsmith on 2009-02-06
Since you are booting the sdc drive, the sdc drive will be (hd0) because (hd0) is always the first boot drive on start up. Therefore, how about trying the following entry for Windows:
```
title Windows XP
root (hd0,1)
chainloader +1
```
Let me know if that works OK or not, and we can work from there if necessary.

---

### Post by ray field on 2009-02-06
> **caljohnsmith said:**
> Since you are booting the sdc drive, the sdc drive will be (hd0) because (hd0) is always the first boot drive on start up. Therefore, how about trying the following entry for Windows:
```
title Windows XP
root (hd0,1)
chainloader +1
```
Let me know if that works OK or not, and we can work from there if necessary.

well, making some kind of progress.  I should have noted that the XP boot drive is D: -- I tried this 

```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdd2
title		Windows XP Media Center Edition
root		(hd0,3)
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
```

and the screen went black and "Starting up..." came up in the top of the left-hand side of the screen -- but nothing happened.

---

### Post by ray field on 2009-02-06
... and OS/2's Boot Manager is in a very small partition at the front of the disk.  

so, I tried 

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdd2
title		Windows XP Media Center Edition
root		(hd0,4)
savedefault
chainloader	+1

``` 

which gets me to the same "Starting Up..." hanging black screen.

I've also tried Super Grub tools, with no luck -- because I thought maybe the partition wasn't activated, I tried to us SG's activate partition tool on the windoze boot partition, but this failed with an "Error 12: incorrect device name" or suchlike.

---

### Post by cdtech on 2009-02-06
This would be the correct way to boot Windows from the device (as per caljohnsmith's suggestion):
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdd2
title		Windows XP Media Center Edition
root		(hd0,1)
chainloader	+1
```
I stand corrected:
Grub boots from BIOS so it sees the boot order that BIOS uses and when using Grub within Ubuntu it works off of the kernel using the device order as it sees listed within the /dev directory.......

**UPDATE::.**
> ... and OS/2's Boot Manager is in a very small partition at the front of the disk. 
Maybe if Grub doesn't see this partition you could try to change the (hd0,1) to (hd0,0).......

---

### Post by ray field on 2009-02-06
> **cdtech said:**
> This would be the correct way to boot Windows from the device (as per caljohnsmith's suggestion):
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdd2
title		Windows XP Media Center Edition
root		(hd0,1)
chainloader	+1
```
I stand corrected:
Grub boots from BIOS so it sees the boot order that BIOS uses and when using Grub within Ubuntu it works off of the kernel using the device order as it sees listed within the /dev directory.......

**UPDATE::.**

Maybe if Grub doesn't see this partition you could try to change the (hd0,1) to (hd0,0).......

I tried changing to hd0,0, with and without the map options -- still get the "Starting Up...." blackscreen.

is there a chance a vestige of Suse's old Grub is screwing around with things?

I'm completely at a loss.  shouldn't it be possible to figure out what Grub statement would work based on the results of that script?

I even tried getting Boot Manager active, but Grub seems to overtake it.

---

### Post by tommcd on 2009-02-07
Try reinstalling grub to the MBR from the Ubuntu live CD like this:
[http://ubuntuforums.org/showthread.php?t=224351&highlight=fsck](http://ubuntuforums.org/showthread.php?t=224351&highlight=fsck)
You could also try the Super Grub disc:
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
Either of these may be an easy way to fix things if you can't manage to boot XP by manually editing the menu.lst file.
First, you can backup your menu.lst file for safety like this:
> sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak

---

### Post by ray field on 2009-02-07
Late last night I got Super Grub to do the FDSK/MBR or whatever to allow Xp to boot, and just now I successfully booted Ubuntu from the SG CD -- what a life-saver.  

I'd really like to fix Grub.  I've hand-copied the results of SG's Show Partitions

```
N IDE  SCSI FGRUB    HURD  TYPE     SIZE   OS
1 hda1 sda1 (hd0,0)  hd0s1 Uknown    7MB
2 hda2 sda2 (hd0,1)  hd0s2 HPFS.NTFS 2GB  WINDOWS
3 hda3 sda3 (hd0,2)  hdos3 Uknown   1004 MB
5 hda5 sda5 (hd0,4)  hdos5 HPFS/NTFS 7GB WINDOWS
6 hda6 sda6 (hd0,5)  hdos6 HPFS/NTFS 9GB WINDOWS
7 hda7 sda7 (hd0,6)  hdos7 HPFS/NTFS 14GB WINDOWS
8 hda8 sda8 (hd0,7)  hdos8 SWAP      1GB
9 hda9 sda9 (hd0,8)  hdos9 SWAP	  2GB
10 hda10 sda10 (hd0,9)  hdos10 ext2fs   11GB Ubuntu 8.10 \n \l
11 hda11 sda11 (hd0,10) hdos11 ext2fs  17GB 
```

I should say that the Grub which Suse installed got this all correct out of the box.  I can't help but think that it either the presence of Boot Manager or SCSI hard disk confused Ubuntu's grub installer.

I've pasted the Ubuntu menu.lst below If someone could direct me how to edit it so it'll boot Windoze and Ubuuntu both, I'd be grateful.

Also, once I get that correct, how do I give priority to Grub over the Windows bootloader?

```

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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=7b2666ae-c50a-4e66-89bf-7ee746b0d57b ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=7b2666ae-c50a-4e66-89bf-7ee746b0d57b

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

title        Ubuntu 8.10, kernel 2.6.27-11-generic
uuid        7b2666ae-c50a-4e66-89bf-7ee746b0d57b
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=7b2666ae-c50a-4e66-89bf-7ee746b0d57b ro quiet splash
initrd        /boot/initrd.img-2.6.27-11-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid        7b2666ae-c50a-4e66-89bf-7ee746b0d57b
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=7b2666ae-c50a-4e66-89bf-7ee746b0d57b ro  single
initrd        /boot/initrd.img-2.6.27-11-generic

title        Ubuntu 8.10, kernel 2.6.27-7-generic
uuid        7b2666ae-c50a-4e66-89bf-7ee746b0d57b
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=7b2666ae-c50a-4e66-89bf-7ee746b0d57b ro quiet splash
initrd        /boot/initrd.img-2.6.27-7-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid        7b2666ae-c50a-4e66-89bf-7ee746b0d57b
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=7b2666ae-c50a-4e66-89bf-7ee746b0d57b ro  single
initrd        /boot/initrd.img-2.6.27-7-generic

title        Ubuntu 8.10, memtest86+
uuid        7b2666ae-c50a-4e66-89bf-7ee746b0d57b
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdd2
title        Windows XP Media Center Edition
root        (hd0,1)
chainloader    +1
map        (hd0) (hd1)
map        (hd1) (hd0)
```

---

### Post by ray field on 2009-02-09
bump

---

### Post by tommcd on 2009-02-10
> **ray field said:**
> 
I should say that the Grub which Suse installed got this all correct out of the box. 


Try reinstalling grub from the Suse install CD if you can. Any grub will work. It does not have to be the grub from Ubuntu.

You will have to consult the Suse documentation on how to do this, as I have never used Suse.

---

### Post by ray field on 2009-02-10
I appreciate the effort, but I think I've tossed out my Suse install disks, & wouldn't know how to install just Grub, and would be apprehensive about doing so.

it seems to me this is an Ubuntu bug.  I would like to fix it by editing menu.lst, however I'm reluctant to do so without the guidance of someone who's knowledgeable about how Ubuntu's grub interacts with SCSI partitions, as well as OS/2 Boot Manager.

---

### Post by ray field on 2009-02-13
someone suggested to me that the problem might be the map statements.

```
title		Windows XP Media Center Edition
root		(hd1,1)
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```

once again please note that Ubuntu boots fine.

again also please note that Boot Manager, which is a primary partition, is the first partition on the HDD. so given that it's a SCSI drive and the partitions are like this

```
N IDE  SCSI FGRUB    HURD  TYPE     SIZE   OS
1 hda1 sda1 (hd0,0)  hd0s1 Uknown    7MB
2 hda2 sda2 (hd0,1)  hd0s2 HPFS.NTFS 2GB  WINDOWS
3 hda3 sda3 (hd0,2)  hdos3 Uknown   1004 MB
5 hda5 sda5 (hd0,4)  hdos5 HPFS/NTFS 7GB WINDOWS
6 hda6 sda6 (hd0,5)  hdos6 HPFS/NTFS 9GB WINDOWS
7 hda7 sda7 (hd0,6)  hdos7 HPFS/NTFS 14GB WINDOWS
8 hda8 sda8 (hd0,7)  hdos8 SWAP      1GB
9 hda9 sda9 (hd0,8)  hdos9 SWAP	  2GB
10 hda10 sda10 (hd0,9)  hdos10 ext2fs   11GB Ubuntu 8.10 \n \l
11 hda11 sda11 (hd0,10) hdos11 ext2fs  17GB
```

with hda7 being my Windows boot partition, what would the entry be for booting XP in menu.lst ?

and how do I reactivate Grub to start rather than XP when I powerup?

---

