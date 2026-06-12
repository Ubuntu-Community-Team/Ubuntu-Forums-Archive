---
title: "Grub Error 21"
date: 2009-02-09
forum: Installation &amp; Upgrades
---

### Post by Saterus on 2009-02-09
I recently bought a new 1TB hard drive for my desktop, so I decided my old hard drive could be put to use as a Linux drive. The installation of Ubuntu 8.10 seems to have gone astray somewhere and I am unable to get back into Ubuntu after reboot.

My system:

(sda/b) (hd0/1): 2x 80gb RAID 0 array with Windows Xp x64 installed using motherboard raid controller
(sdd) (hd2): 1x 320gb Linux drive with Ubuntu 8.10 64 installed
(sdc) (hd?): 1x 1tb storage drive with all my data

I am unable to reach Linux upon reboot, and have done some searching online. I burnt a disc with Super Grub Disc and am able to use that to get to Windows, but not Linux. None of SGD's functionality lets me successfully boot to Linux, but the default "Win" option on the main menu takes me straight to windows.

From what I've gathered, some combination of my boot drive as specified in the BIOS and my boot drive as specified by Grub are not matching up. My 1tb drive is not showing up at all in Grub, but from my research that isn't really a problem since I'm not booting off it.

I've seen a bash script called boot_info_script floating around these forums while I've been researching. I've run it while logged into Ubuntu off the live cd.

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #4 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No known boot loader is installed in the MBR of /dev/sdb
 => Syslinux is installed in the MBR of /dev/sdc
 => Syslinux is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Windows XP
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb3: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdd2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdd5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders, total 160836480 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x91a491a4

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   321,637,364   321,637,302   7 HPFS/NTFS

/dev/sda1 ends after the last sector of /dev/sda

Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders, total 160836480 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

Invalid MBR Signature found
/dev/sdb3       2,941,255,680 2,941,255,689            10  2d Unknown

/dev/sdb3 ends after the last sector of /dev/sdb

Drive sdc: _____________________________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xde0ec3fc

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63 1,953,520,064 1,953,520,002   7 HPFS/NTFS


Drive sdd: _____________________________________________________________________

Disk /dev/sdd: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0005b425

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *             63   601,393,274   601,393,212  83 Linux
/dev/sdd2         601,393,275   625,137,344    23,744,070   5 Extended
/dev/sdd5         601,393,338   625,137,344    23,744,007  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sdc1: UUID="B0B44B3EB44B0676" TYPE="ntfs" 
/dev/sdd1: UUID="e08eb445-1127-444d-af27-922e635b2e5b" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdd5: UUID="8dfe0669-c85e-4fd2-92a9-6169717b78a0" TYPE="swap" 
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

=========================== sdd1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=e08eb445-1127-444d-af27-922e635b2e5b ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=e08eb445-1127-444d-af27-922e635b2e5b

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
root		(hd2,0)
uuid		e08eb445-1127-444d-af27-922e635b2e5b
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=e08eb445-1127-444d-af27-922e635b2e5b ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Windows XP x64
rootnoverify	(hd0,0)
makeactive
chainloader	+1

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root		(hd2,0)
uuid		e08eb445-1127-444d-af27-922e635b2e5b
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=e08eb445-1127-444d-af27-922e635b2e5b ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
root		(hd2,0)
uuid		e08eb445-1127-444d-af27-922e635b2e5b
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sdd1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdd1
UUID=e08eb445-1127-444d-af27-922e635b2e5b /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdd5
UUID=8dfe0669-c85e-4fd2-92a9-6169717b78a0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdd1: Location of files loaded by Grub: ===================


  61.6GB: boot/grub/menu.lst
  61.6GB: boot/grub/stage2
  61.7GB: boot/initrd.img-2.6.27-7-generic
  61.7GB: boot/vmlinuz-2.6.27-7-generic
  61.7GB: initrd.img
  61.7GB: vmlinuz

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdb

00000000  30 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |0...............|
00000010  d8 ad 0a 00 00 00 00 00  40 00 00 00 2e 00 00 00  |........@.......|
00000020  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000030  00 00 00 00 ff 07 00 00  02 00 00 00 00 00 00 00  |................|
00000040  20 6e fa 7f ff 07 00 00  00 00 00 00 00 00 00 00  | n..............|
00000050  38 83 f7 7f ff 07 00 00  00 00 00 00 00 00 00 00  |8...............|
00000060  58 f2 fd ff ff 07 00 00  be 02 00 00 00 00 00 00  |X...............|
00000070  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000080  2c 00 2d 00 00 00 00 00  50 af 0a 00 00 00 00 00  |,.-.....P.......|
00000090  82 51 08 00 01 00 00 00  00 00 00 00 00 00 00 00  |.Q..............|
000000a0  00 00 00 00 00 00 00 00  01 05 00 00 00 00 00 05  |................|
000000b0  15 00 00 00 7f b7 8b 1d  35 46 bf 98 f2 bc 37 6e  |........5F....7n|
000000c0  eb 03 00 00 01 05 00 00  00 00 00 05 15 00 00 00  |................|
000000d0  7f b7 8b 1d 35 46 bf 98  f2 bc 37 6e 01 02 00 00  |....5F....7n....|
000000e0  37 a4 18 d6 49 02 00 00  e0 62 01 00 00 00 00 00  |7...I....b......|
000000f0  60 01 00 00 01 00 04 80  14 01 00 00 30 01 00 00  |`...........0...|
00000100  00 00 00 00 14 00 00 00  02 00 00 01 02 00 00 00  |................|
00000110  00 00 18 00 ff 01 1f 00  01 02 00 00 00 00 00 05  |................|
00000120  20 00 00 00 20 02 00 00  00 00 24 00 ff 01 1f 00  | ... .....$.....|
00000130  01 05 00 00 00 00 00 05  15 00 00 00 7f b7 8b 1d  |................|
00000140  35 46 bf 98 f2 bc 37 6e  eb 03 00 00 00 00 00 00  |5F....7n........|
00000150  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000160  30 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |0...............|
00000170  d8 ad 0a 00 00 00 00 00  40 00 00 00 2e 00 00 00  |........@.......|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 00 00 ff 07 00 00  02 00 00 00 00 00 00 00  |................|
000001a0  20 6e fa 7f ff 07 00 00  00 00 00 00 00 00 00 00  | n..............|
000001b0  38 83 f7 7f ff 07 00 00  00 00 00 00 00 00 00 00  |8...............|
000001c0  58 f2 fd ff ff 07 00 00  ce 00 00 00 00 00 00 00  |X...............|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  2c 00 2d 00 00 00 00 00  50 af 0a 00 00 00 00 00  |,.-.....P.......|
000001f0  82 51 08 00 01 00 00 00  00 00 00 00 00 00 00 00  |.Q..............|
00000200

Unknown BootLoader  on sdb3



=============================== StdErr Messages: ===============================

boot_info_script.txt: line 1043: [: =: unary operator expected
hexdump: /dev/sdb3: No such file or directory
hexdump: /dev/sdb3: No such file or directory
boot_info_script.txt: line 1043: [: =: unary operator expected
```

Apparently Grub is installed on one of my 80gb hard drives even though it is part of an array. At this point, I think I understand what is happening, but I'm unsure of how to fix it. I am perfectly willing to reinstall one or both Windows and Ubuntu again. Everything is backed up on my storage drive. If there is a way to get it working without reinstalling, all the better.

---

### Post by caljohnsmith on 2009-02-09
It looks like you're right, Grub is installed to the MBR of one of your RAID drives. I would first recommend correcting that, so how about booting your Live CD (the Ubuntu install CD), and do:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
That will reinstall a Windows equivalent MBR to your sda drive. Then to install Grub to the MBR of your Ubuntu sdd drive, how about doing:
```
sudo grub
grub> root (hd3,0)
grub> setup (hd3)
grub> quit

```
It also looks like you may have tried tweaking your Ubuntu Grub's menu.lst (or maybe Super Grub Disk did that), so how about next doing:
```
sudo mount /dev/sdd1 /mnt && gksudo gedit /mnt/boot/grub/menu.lst
```
And delete all the "root (hd2,0)" lines in all your Ubuntu entries as shown highlighted in red below:
```
title		Ubuntu 8.10, kernel 2.6.27-7-generic
[COLOR="Red"]root		(hd2,0)[/COLOR]
uuid		e08eb445-1127-444d-af27-922e635b2e5b
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=e08eb445-1127-444d-af27-922e635b2e5b ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet
```
Also, please delete the Windows XP entry in the middle of your Ubuntu entries, and instead add the following entries at the very end of the menu.lst (making sure they come after "### END DEBIAN AUTOMAGIC KERNELS LIST"):
```
title       Windows XP (hd1)
rootnoverify     (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

title       Windows XP (hd2)
rootnoverify     (hd2,0)
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader +1

title       Windows XP (hd3)
rootnoverify     (hd3,0)
map        (hd0) (hd3)
map        (hd3) (hd0)
chainloader +1
```
Then reboot, set your BIOS to boot the Ubuntu sdd drive, and let me know if you can boot Ubuntu and/or Windows from your Grub menu (assuming you get the Grub menu). We can work from there.

---

### Post by Saterus on 2009-02-10
Worked like a charm. Thanks a ton. Boots to both Ubuntu and Windows perfectly.

---

### Post by caljohnsmith on 2009-02-10
Glad that worked OK; cheers and enjoy Ubuntu and Windows. :)

---

