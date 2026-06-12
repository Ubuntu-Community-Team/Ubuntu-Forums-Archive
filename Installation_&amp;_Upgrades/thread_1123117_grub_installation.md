---
title: "grub installation"
date: 2009-04-11
forum: Installation &amp; Upgrades
---

### Post by newsman on 2009-04-11
I am having a bit of a problem trying to figure out where to put grup boot loader (or rather which drive or where is the mbr so that I can put the boot loader there)..

how do i go about solving this problem ?

My bios is set to a maxtor drive as secondary (after CD-Rom)

the maxtor drive contains three partitions,, ntfs, ext3 and swap... and i tried putting grub there but for some reason i don't think it is installing properly.

All i get at the end of the install is a dos line "Grub" with nothing else.. any clues as to what happened?  This has happened with ubuntu and xubuntu thus i assume it would happen with all variants.

---

### Post by meierfra. on 2009-04-11
In order to get a clearer picture of your setup, I suggest to boot from the Ubuntu LiveCD and  download the Boot Info Script to  your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post,  highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by neu2buntu on 2009-04-11
are you using the live cd?  do you have ubuntu installed to your pc and want to make a seperate bootable maxtor drive?,...try to give more info please

---

### Post by newsman on 2009-04-12
this will seam like a long post..

I am using the ubuntu live cd 

> 
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #3 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
 => Grub0.97 is installed in the MBR of /dev/sdd and looks on boot drive #3 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       reiserfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd1: _________________________________________________________________________

    File system:       
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sdd1 and 
                       looks at sector 248795503 on boot drive #3 for the 
                       stage2 file. A stage2 file is at this location on 
                       /dev/sdc. Stage2 looks on the same partition for 
                       /boot/grub/menu.lst.
    Mounting failed:
mount: unknown filesystem type ''

sdd2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdd5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x680cf14f

Partition  Boot         Start           End          Size  Id System

/dev/sda2    *      6,040,440   714,747,914   708,707,475   f W95 Ext d (LBA)
/dev/sda5           6,056,505   703,566,674   697,510,170   b W95 FAT32
/dev/sda6         703,566,738   714,747,914    11,181,177  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x28c48805

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   735,953,714   735,953,652   c W95 FAT32 (LBA)
/dev/sdb2         966,888,090   976,768,064     9,879,975   5 Extended
/dev/sdb5         966,888,153   976,768,064     9,879,912  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcc92cc92

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   359,229,464   359,229,402  83 Linux
/dev/sdc2         359,229,465   398,283,479    39,054,015   5 Extended
/dev/sdc5         359,229,528   398,283,479    39,053,952  82 Linux swap / Solaris


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders, total 240121728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x04b39df1

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *             63   234,838,169   234,838,107   7 HPFS/NTFS
/dev/sdd2         234,838,170   240,107,489     5,269,320   5 Extended
/dev/sdd5         234,838,233   240,107,489     5,269,257  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda5: LABEL="back2" UUID="09E2-09E4" TYPE="vfat" 
/dev/sda6: UUID="2f229353-c7ad-4079-9ce3-0945f76c5273" TYPE="swap" 
/dev/sdb1: LABEL="Backup" UUID="B22E-83AF" TYPE="vfat" 
/dev/sdb5: UUID="59f7e2b2-b9a9-40ee-a587-59c5c2c58078" TYPE="swap" 
/dev/sdc1: UUID="e3ff2d67-3e0a-4987-b235-bdc40a731ee7" TYPE="reiserfs" 
/dev/sdc5: UUID="6869e4ad-29bb-44c1-8dd7-1024adbddfe2" TYPE="swap" 
/dev/sdd5: UUID="4bce3dca-d0d1-453e-86c5-11cfb6ae2fd9" TYPE="swap" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

/proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/scd0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


=========================== sdc1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=e3ff2d67-3e0a-4987-b235-bdc40a731ee7 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=e3ff2d67-3e0a-4987-b235-bdc40a731ee7

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

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		e3ff2d67-3e0a-4987-b235-bdc40a731ee7
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=e3ff2d67-3e0a-4987-b235-bdc40a731ee7 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		e3ff2d67-3e0a-4987-b235-bdc40a731ee7
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=e3ff2d67-3e0a-4987-b235-bdc40a731ee7 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		e3ff2d67-3e0a-4987-b235-bdc40a731ee7
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc1
UUID=e3ff2d67-3e0a-4987-b235-bdc40a731ee7 /               reiserfs notail,relatime 0       1
# /dev/sda6
UUID=2f229353-c7ad-4079-9ce3-0945f76c5273 none            swap    sw              0       0
# /dev/sdb5
UUID=59f7e2b2-b9a9-40ee-a587-59c5c2c58078 none            swap    sw              0       0
# /dev/sdc5
UUID=6869e4ad-29bb-44c1-8dd7-1024adbddfe2 none            swap    sw              0       0
# /dev/sdd5
UUID=4bce3dca-d0d1-453e-86c5-11cfb6ae2fd9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdc1: Location of files loaded by Grub: ===================


 127.3GB: boot/grub/menu.lst
 127.3GB: boot/grub/stage2
    .2GB: boot/initrd.img-2.6.27-7-generic
 127.3GB: boot/vmlinuz-2.6.27-7-generic
    .2GB: initrd.img
 127.3GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda5

00000000  eb 58 90 4d 53 57 49 4e  34 2e 31 00 02 40 6f 00  |.X.MSWIN4.1..@o.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 39 6a 5c 00  |........?...9j\.|
00000020  1a 29 93 29 8f 4c 01 00  00 00 00 00 03 00 00 00  |.).).L..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 e4 09 e2 09 4e  4f 20 4e 41 4d 45 20 20  |..)....NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 8c c8 8e d0 bc ff  |  FAT32   ......|
00000060  7b fb 8e d8 8e c0 fc bf  20 00 33 c0 b9 15 00 af  |{....... .3.....|
00000070  75 05 af 75 04 e2 f8 47  47 81 7d fe 00 c0 72 0a  |u..u...GG.}...r.|
00000080  e2 ed 81 3e 02 01 00 c0  73 0f be 88 7d e8 3f 00  |...>....s...}.?.|
00000090  33 c0 cd 16 3d 00 3b 75  f7 be a7 7c bf a7 7e b9  |3...=.;u...|..~.|
000000a0  71 00 f3 a5 e9 00 02 bb  00 7c b9 01 00 be e1 7e  |q........|.....~|
000000b0  e8 1c 00 33 c0 cd 16 b8  01 02 33 d2 50 cd 13 58  |...3......3.P..X|
000000c0  cd 13 72 e3 81 3e fe 7d  55 aa 75 db e9 31 fd 50  |..r..>.}U.u..1.P|
000000d0  53 51 ac 3c 00 75 04 59  5b 58 c3 b4 0e cd 10 eb  |SQ.<.u.Y[X......|
000000e0  f1 0a 0d 4e 6f 6e 2d 73  79 73 74 65 6d 20 64 69  |...Non-system di|
000000f0  73 6b 20 6f 72 20 64 69  73 6b 20 65 72 72 6f 72  |sk or disk error|
00000100  0a 0d 49 6e 73 65 72 74  20 44 4f 53 20 64 69 73  |..Insert DOS dis|
00000110  6b 65 74 74 65 20 61 6e  64 20 70 72 65 73 73 20  |kette and press |
00000120  61 6e 79 20 6b 65 79 20  2e 2e 2e 0a 0d 00 00 00  |any key ........|
00000130  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000180  00 00 00 00 00 00 00 00  0a 0d 50 6f 73 73 69 62  |..........Possib|
00000190  6c 65 20 62 6f 6f 74 20  56 49 52 55 53 20 64 65  |le boot VIRUS de|
000001a0  74 65 63 74 65 64 21 0a  0d 50 72 65 73 73 20 3c  |tected!..Press <|
000001b0  46 31 3e 20 74 6f 20 63  6f 6e 74 69 6e 75 65 00  |F1> to continue.|
000001c0  0d 0a 50 57 2f 44 42 20  62 79 20 4b 49 52 20 56  |..PW/DB by KIR V|
000001d0  2e 20 28 43 29 20 50 61  72 61 67 6f 6e 20 31 39  |. (C) Paragon 19|
000001e0  39 37 2d 31 39 39 39 00  00 00 00 00 00 00 00 00  |97-1999.........|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



---

### Post by newsman on 2009-04-12
i have managed to get it working.

my first post sdd was split betweeen ubuntu installation swap and ntfs..

now my sdd is split only only on ntfs  (if you read the text file posted before) and grub on sdd and /boot on sdd as well.

my ubuntu installation is on sdc

i have edit grub to load sdd1 or sdd2 (ntfs)

what do i put in my menu.lst file?


Thanks....

> 
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #3 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
 => Grub0.97 is installed in the MBR of /dev/sdd and looks on the same drive 
    in partition #5 for /grub/stage2 and /grub/menu.lst.

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       reiserfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd1: _________________________________________________________________________

    File system:       
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sdd1 and 
                       looks at sector 248795503 on boot drive #3 for the 
                       stage2 file. A stage2 file is at this location on 
                       /dev/sdc. Stage2 looks on partition #1 for 
                       /boot/grub/menu.lst.
    Mounting failed:
mount: unknown filesystem type ''

sdd2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdd5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x680cf14f

Partition  Boot         Start           End          Size  Id System

/dev/sda2    *      6,040,440   714,747,914   708,707,475   f W95 Ext d (LBA)
/dev/sda5           6,056,505   703,566,674   697,510,170   b W95 FAT32
/dev/sda6         703,566,738   714,747,914    11,181,177  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x28c48805

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   735,953,714   735,953,652   c W95 FAT32 (LBA)
/dev/sdb2         966,888,090   976,768,064     9,879,975   5 Extended
/dev/sdb5         966,888,153   976,768,064     9,879,912  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcc92cc92

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   359,229,464   359,229,402  83 Linux
/dev/sdc2         359,229,465   398,283,479    39,054,015   5 Extended
/dev/sdc5         359,229,528   398,283,479    39,053,952  82 Linux swap / Solaris


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders, total 240121728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x04b39df1

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *             63   234,838,169   234,838,107   7 HPFS/NTFS
/dev/sdd2         234,838,170   240,107,489     5,269,320   5 Extended
/dev/sdd5         234,838,233   240,107,489     5,269,257  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda5: LABEL="back2" UUID="09E2-09E4" TYPE="vfat" 
/dev/sda6: UUID="2f229353-c7ad-4079-9ce3-0945f76c5273" TYPE="swap" 
/dev/sdb1: LABEL="Backup" UUID="B22E-83AF" TYPE="vfat" 
/dev/sdb5: UUID="59f7e2b2-b9a9-40ee-a587-59c5c2c58078" TYPE="swap" 
/dev/sdc1: UUID="30bb1ff1-25a4-4cb5-8386-2e133fcca7a8" TYPE="reiserfs" 
/dev/sdc5: UUID="6869e4ad-29bb-44c1-8dd7-1024adbddfe2" TYPE="swap" 
/dev/sdd5: UUID="66ed4997-900f-494c-8309-9bbf88c151d8" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/sdc1 on / type reiserfs (rw,relatime)
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
/dev/sdd5 on /boot type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)


=========================== sdc1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=30bb1ff1-25a4-4cb5-8386-2e133fcca7a8 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=66ed4997-900f-494c-8309-9bbf88c151d8

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
uuid		66ed4997-900f-494c-8309-9bbf88c151d8
kernel		/vmlinuz-2.6.27-11-generic root=UUID=30bb1ff1-25a4-4cb5-8386-2e133fcca7a8 ro quiet splash 
initrd		/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		66ed4997-900f-494c-8309-9bbf88c151d8
kernel		/vmlinuz-2.6.27-11-generic root=UUID=30bb1ff1-25a4-4cb5-8386-2e133fcca7a8 ro  single
initrd		/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		66ed4997-900f-494c-8309-9bbf88c151d8
kernel		/vmlinuz-2.6.27-7-generic root=UUID=30bb1ff1-25a4-4cb5-8386-2e133fcca7a8 ro quiet splash 
initrd		/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		66ed4997-900f-494c-8309-9bbf88c151d8
kernel		/vmlinuz-2.6.27-7-generic root=UUID=30bb1ff1-25a4-4cb5-8386-2e133fcca7a8 ro  single
initrd		/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		66ed4997-900f-494c-8309-9bbf88c151d8
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc1
UUID=30bb1ff1-25a4-4cb5-8386-2e133fcca7a8 /               reiserfs relatime        0       1
# /dev/sdd5
UUID=66ed4997-900f-494c-8309-9bbf88c151d8 /boot           ext3    relatime        0       2
# /dev/sda6
UUID=2f229353-c7ad-4079-9ce3-0945f76c5273 none            swap    sw              0       0
# /dev/sdb5
UUID=59f7e2b2-b9a9-40ee-a587-59c5c2c58078 none            swap    sw              0       0
# /dev/sdc5
UUID=6869e4ad-29bb-44c1-8dd7-1024adbddfe2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdc1: Location of files loaded by Grub: ===================


    .9GB: boot/grub/menu.lst
    .9GB: boot/grub/stage2
    .0GB: boot/initrd.img-2.6.27-11-generic
    .0GB: boot/initrd.img-2.6.27-7-generic
    .0GB: boot/vmlinuz-2.6.27-11-generic
    .0GB: boot/vmlinuz-2.6.27-7-generic
    .0GB: initrd.img
    .0GB: initrd.img.old
    .0GB: vmlinuz
    .0GB: vmlinuz.old

============================= sdd5/grub/menu.lst: =============================

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
# kopt=root=UUID=30bb1ff1-25a4-4cb5-8386-2e133fcca7a8 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=66ed4997-900f-494c-8309-9bbf88c151d8

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
uuid		66ed4997-900f-494c-8309-9bbf88c151d8
kernel		/vmlinuz-2.6.27-11-generic root=UUID=30bb1ff1-25a4-4cb5-8386-2e133fcca7a8 ro quiet splash 
initrd		/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		66ed4997-900f-494c-8309-9bbf88c151d8
kernel		/vmlinuz-2.6.27-11-generic root=UUID=30bb1ff1-25a4-4cb5-8386-2e133fcca7a8 ro  single
initrd		/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		66ed4997-900f-494c-8309-9bbf88c151d8
kernel		/vmlinuz-2.6.27-7-generic root=UUID=30bb1ff1-25a4-4cb5-8386-2e133fcca7a8 ro quiet splash 
initrd		/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		66ed4997-900f-494c-8309-9bbf88c151d8
kernel		/vmlinuz-2.6.27-7-generic root=UUID=30bb1ff1-25a4-4cb5-8386-2e133fcca7a8 ro  single
initrd		/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		66ed4997-900f-494c-8309-9bbf88c151d8
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=================== sdd5: Location of files loaded by Grub: ===================


 121.2GB: grub/menu.lst
 121.2GB: grub/stage2
 120.2GB: initrd.img-2.6.27-11-generic
 120.3GB: initrd.img-2.6.27-7-generic
 120.2GB: vmlinuz-2.6.27-11-generic
 120.3GB: vmlinuz-2.6.27-7-generic
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda5

00000000  eb 58 90 4d 53 57 49 4e  34 2e 31 00 02 40 6f 00  |.X.MSWIN4.1..@o.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 39 6a 5c 00  |........?...9j\.|
00000020  1a 29 93 29 8f 4c 01 00  00 00 00 00 03 00 00 00  |.).).L..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 e4 09 e2 09 4e  4f 20 4e 41 4d 45 20 20  |..)....NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 8c c8 8e d0 bc ff  |  FAT32   ......|
00000060  7b fb 8e d8 8e c0 fc bf  20 00 33 c0 b9 15 00 af  |{....... .3.....|
00000070  75 05 af 75 04 e2 f8 47  47 81 7d fe 00 c0 72 0a  |u..u...GG.}...r.|
00000080  e2 ed 81 3e 02 01 00 c0  73 0f be 88 7d e8 3f 00  |...>....s...}.?.|
00000090  33 c0 cd 16 3d 00 3b 75  f7 be a7 7c bf a7 7e b9  |3...=.;u...|..~.|
000000a0  71 00 f3 a5 e9 00 02 bb  00 7c b9 01 00 be e1 7e  |q........|.....~|
000000b0  e8 1c 00 33 c0 cd 16 b8  01 02 33 d2 50 cd 13 58  |...3......3.P..X|
000000c0  cd 13 72 e3 81 3e fe 7d  55 aa 75 db e9 31 fd 50  |..r..>.}U.u..1.P|
000000d0  53 51 ac 3c 00 75 04 59  5b 58 c3 b4 0e cd 10 eb  |SQ.<.u.Y[X......|
000000e0  f1 0a 0d 4e 6f 6e 2d 73  79 73 74 65 6d 20 64 69  |...Non-system di|
000000f0  73 6b 20 6f 72 20 64 69  73 6b 20 65 72 72 6f 72  |sk or disk error|
00000100  0a 0d 49 6e 73 65 72 74  20 44 4f 53 20 64 69 73  |..Insert DOS dis|
00000110  6b 65 74 74 65 20 61 6e  64 20 70 72 65 73 73 20  |kette and press |
00000120  61 6e 79 20 6b 65 79 20  2e 2e 2e 0a 0d 00 00 00  |any key ........|
00000130  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000180  00 00 00 00 00 00 00 00  0a 0d 50 6f 73 73 69 62  |..........Possib|
00000190  6c 65 20 62 6f 6f 74 20  56 49 52 55 53 20 64 65  |le boot VIRUS de|
000001a0  74 65 63 74 65 64 21 0a  0d 50 72 65 73 73 20 3c  |tected!..Press <|
000001b0  46 31 3e 20 74 6f 20 63  6f 6e 74 69 6e 75 65 00  |F1> to continue.|
000001c0  0d 0a 50 57 2f 44 42 20  62 79 20 4b 49 52 20 56  |..PW/DB by KIR V|
000001d0  2e 20 28 43 29 20 50 61  72 61 67 6f 6e 20 31 39  |. (C) Paragon 19|
000001e0  39 37 2d 31 39 39 39 00  00 00 00 00 00 00 00 00  |97-1999.........|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



---

### Post by meierfra. on 2009-04-12
Your Ubuntu partition is on the 204GB drive /dev/sdc. (and not on the 123 GB drive  /dev/sdd containing the ntfs partition)

To be able to  boot into Ubuntu, I suggest  to install Grub to the MBR of 204GB drive and set the bios to boot from that drive:

Boot from the LiveCD, open a terminal and reinstall grub via

```
sudo grub
root (hd2,0)
setup (hd2)
quit
```

Reboot, but set your bios to boot from the 204GB drive


Then you tried to install grub  to the 123GB drive, you overwrote the boot sector of  ntfs partition /dev/sdd1.  You will have to fix the boot sector:


 Download the [testdisk-6.10.linux26.tar.bz2 package](http://www.cgsecurity.org/testdisk-6.10.linux26.tar.bz2) to your desktop, and then do:

```


cd ~/Desktop
tar xvf testdisk-6.10.linux26.tar.bz2
sudo testdisk-6.10/linux/testdisk_static /dev/sdd

```


Choose "proceed" on the first screen, then
"intel"
"advanced",
Select the ntfs partition (although it should be selected already) and choose
"boot"
"BackupBS"
Type "Y" to confirm.


Also  you have a swap partition on each of your hard drives, including a 20GB swap partition on /dev/sdc.  You really only need one swap partition of size say 2GB. So you might think about shrinking the swap partition on /dev/sdc and delete all the others.

---

### Post by newsman on 2009-04-12
yep............. all done and dusted....... phew.... what a way to spend the holiday weekend... ..

---

### Post by meierfra. on 2009-04-12
> all done and dusted.
Great. Have fun with Ubuntu

---

