---
title: "grub error 17 after partition changes (boot_info_script results included)"
date: 2009-06-15
forum: Installation &amp; Upgrades
---

### Post by snacht on 2009-06-15
I get the grub menu, choose ubuntu, then I get error 17. The results of the bootinfoscript ([http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)) are included below. running ubuntu 9.04.
History (probably not relevant): 1) installed winXP 2) installed ubuntu - now dual boot with 15 gig for ubuntu. 3) liked ubuntu so moved more and more files from winXP to ubuntu. So i needed to decrease the winXP partition and increase the ubuntu partation. 4) used to gparted on ubuntu live CD 9.04 to decrease xp partition. 5) HOWEVER, growing ubuntu partition to the left did not work, appearantly you can only grow the partition to the right (left/right meaning adding in front of/behind). 6) so I copied the ext3 partition containing ubuntu to the unpartioned space between the XP partition and the source ubuntu partition. 7) deleted the extended partition containing the the original ubuntu and swap space. 8) created a new swapspace and grew the copied ubuntu partition to the right. 9) first I did not even get the boot menu, after much fiddling I got the boot menu but an error 17 when booting into my ubuntu partition.

I would be greatfull if someone can help me out with this.

RESULTS.txt:
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #4 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
$LogFile indicates unclean shutdown (0, 1)
Failed to mount '/dev/sda2': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda2 sda2 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda2 sda2 ntfs-3g defaults,force 0 0
$LogFile indicates unclean shutdown (0, 1)
Failed to mount '/dev/sda2': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda2 sda2 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda2 sda2 ntfs-3g defaults,force 0 0

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  Unknown
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda4 and 
                       looks at sector 97748596 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #4 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x41ab2316

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       273,104       273,042  de Dell Utility
/dev/sda2    *        273,105    96,454,259    96,181,155   7 HPFS/NTFS
/dev/sda3         191,237,760   195,366,464     4,128,705  82 Linux swap / Solaris
/dev/sda4          96,454,260   191,237,759    94,783,500  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D7-070A" TYPE="vfat" 
/dev/sda2: UUID="92E0ED0BE0ECF67F" TYPE="ntfs" 
/dev/sda3: TYPE="swap" UUID="5b8e5be2-5875-4dbd-9b1a-8cf5c19f3366" 
/dev/sda4: UUID="d7c7b0a5-a533-4ad5-b6d7-0b36c7a92d31" SEC_TYPE="ext2" TYPE="ext3" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
/dev/sda4 on /mnt/root type ext3 (rw)
none on /mnt/root/proc type proc (rw)


=========================== sda4/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=d7c7b0a5-a533-4ad5-b6d7-0b36c7a92d31 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=d7c7b0a5-a533-4ad5-b6d7-0b36c7a92d31

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
root	        (hd0,2)	
kernel		/boot/vmlinuz-2.6.28-11-generic root=/dev/sda4 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
root	        (hd0,2)	
kernel		/boot/vmlinuz-2.6.28-11-generic root=/dev/sda4 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
root	        (hd0,2)	
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
rootnoverify	(hd0,1)
savedefault
makeactive
chainloader	+1


=============================== sda4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
/dev/sda4	/               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
/dev/sda3 	none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda4: Location of files loaded by Grub: ===================


  50.9GB: boot/grub/menu.lst
  50.0GB: boot/grub/stage2
  49.9GB: boot/initrd.img-2.6.28-11-generic
  50.0GB: boot/vmlinuz-2.6.28-11-generic
  49.9GB: initrd.img
  50.0GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  3f fa f5 60 00 71 92 00  23 af f9 f5 f7 ae 2a 57  |?..`.q..#.....*W|
00000010  76 dc f7 63 2b 47 cc 7e  c5 38 05 80 c0 2c ac 7a  |v..c+G.~.8...,.z|
00000020  83 fe 27 d6 94 00 40 3d  00 18 cf 4c fb e7 eb 5d  |..'...@=...L...]|
00000030  d0 85 ee d8 db 7c b7 14  9e e3 90 30 46 46 71 ef  |.....|.....0FFq.|
00000040  df af a9 a7 ab 74 18 e3  1c 7c bd 41 39 eb f5 f5  |.....t...|.A9...|
00000050  a9 95 94 2c 88 57 b4 7c  c7 8c fc d9 0a c3 90 00  |...,.W.|........|
00000060  07 23 d3 27 3c d3 c0 07  04 10 30 0f 18 2b 91 fd  |.#.'<.....0..+..|
00000070  7f 1a 1f c0 bc d1 6d a6  b9 50 98 19 42 38 60 08  |......m..P..B8`.|
00000080  e8 7a 7e 7f ce 9e ce 14  85 1b 8e 76 e4 14 c2 e7  |.z~........v....|
00000090  a9 a9 97 c3 03 29 c5 ab  24 c9 32 d8 ce 7b 0f 97  |.....)..$.2..{..|
000000a0  0a 30 07 7f 73 f5 a5 dc  09 00 1e d9 e9 d7 f1 a8  |.0..s...........|
000000b0  31 e6 95 f7 77 1e 3d 01  60 31 8c 0c 1c f7 a5 04  |1...w.=.`1......|
000000c0  8e 54 91 db 3d 28 34 a6  dd af 7d 45 50 72 09 c9  |.T..=(4...}EPr..|
000000d0  c7 42 39 1f 5c fe 7f 8d  28 40 48 63 9c 80 c0 00  |.B9.\...(@Hc....|
000000e0  dc 10 79 cf b9 a1 34 fb  9a 36 dc 77 d4 93 73 23  |..y...4..6.w..s#|
000000f0  2b 06 2b 22 90 15 b3 b7  6f f7 79 f5 fa d0 0e 36  |+.+"....o.y....6|
00000100  ae 49 2e 70 4f 5e 4f 39  cf bf 7c f7 a9 6e cb d4  |.I.pO^O9..|..n..|
00000110  cd c5 b8 ab bd 45 5c 6d  20 33 0e 07 3d b0 4f 5c  |.....E\m 3..=.O\|
00000120  f7 35 37 ca 18 02 c4 91  b7 e5 c8 23 d4 1c fa e7  |.57........#....|
00000130  d6 a6 5f 0a 5d c4 e0 f9  62 39 15 10 6d 05 82 7c  |.._.]...b9..m..||
00000140  cd b0 05 03 7b 1c b1 fa  93 d6 a4 53 d3 25 d8 85  |....{......S.%..|
00000150  3f c4 a4 02 7a 1f ad 57  35 ad a3 2e 29 a8 a6 84  |?...z..W5...)...|
00000160  63 f2 f5 63 d4 10 c3 1d  3a 1c f7 e4 f7 a3 71 c7  |c..c....:.....q.|
00000170  1c 70 33 9c 0e 4f e3 cf  3f e3 43 6d 2d 13 b9 53  |.p3..O..?.Cm-..S|
00000180  52 70 ea 42 f2 94 2d b9  a3 46 40 bb f7 1e 40 27  |Rp.B..-..F@...@'|
00000190  9e 08 e4 f3 58 d7 5a a1  65 31 da bb 44 50 aa 99  |....X.Z.e1..DP..|
000001a0  9a 22 c1 91 8f ef 3b f5  23 38 3d 8f 35 54 29 b9  |."....;.#8=.5T).|
000001b0  3e 66 2a 14 1c e5 ef 23  1c cc 8c a0 34 b7 04 ab  |>f*....#....4...|
000001c0  1c 87 76 62 e1 87 50 4e  71 fe 35 4d a5 72 23 06  |..vb..PNq.5M.r#.|
000001d0  49 4a a0 db 1a 31 1f 70  7a 9f af 7a eb 72 5a 23  |IJ...1.pz..z.rZ#|
000001e0  ba ca 2a c8 69 6c f1 c9  24 67 39 07 e9 c9 3c 9a  |..*.il..$g9...<.|
000001f0  84 f3 cf af a7 b5 62 e5  a5 96 e4 b6 f9 92 43 71  |......b.......Cq|
00000200



Can anyone help me?

---

### Post by ajgreeny on 2009-06-15
In fact you can move partitions to the left, but the fact that you were using an extended partition make sthings a bit more difficult.  Anyway, have a look at the /boot/grub/menu.lst file and check that the UUID in the second line of the ubuntu stanzas is correct as I think it may have changed in your partition changing activities. It should be ```
UUID   d7c7b0a5-a533-4ad5-b6d7-0b36c7a92d31
``` according to your blkid output in the boot info summary.  Either change the incorrect UUID to this if it is wrong, or even just use the grub device name for sda4 with the line:- ```
root    (hd0,3)
```Good luck.  I hope this helps.

---

### Post by ajgreeny on 2009-06-15
I've just looked again at your boot info script summary and see that the grub menu.lst is pointing to sda3 for the ubuntu install ```
root  (hd0,2)
```and it should be pointing to sda4```
root   (hd0,3)
```If that doesn't help, come back again.

---

### Post by snacht on 2009-06-16
Thank you,
Problem solved. One could that I could have solved myself if I had been more attentive.

---

