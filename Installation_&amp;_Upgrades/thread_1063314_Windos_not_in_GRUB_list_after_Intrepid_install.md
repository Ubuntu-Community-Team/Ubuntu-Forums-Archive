---
title: "Windos not in GRUB list after Intrepid install"
date: 2009-02-07
forum: Installation &amp; Upgrades
---

### Post by ibbers on 2009-02-07
Hi folks,

I recently dead a fresh install of Windows and then Intrepid on my laptop (needed Windows for a uni subject, unfortunately), but unlike on previous occasions, after the Ubuntu install, my Windows wasn't in the GRUB menu.

I've read a few posts elsewhere, but am hesitant to try things without checking with someone more knowledgeable on here than me...

I had run a boot_info_script024.sh on my laptop, giving me the results below:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #8 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No known boot loader is installed in the MBR of /dev/sdb

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0f800000

Partition  Boot         Start           End          Size  Id System

/dev/sda2                  63   488,392,064   488,392,002   f W95 Ext d (LBA)
/dev/sda5         389,113,263   430,073,279    40,960,017   7 HPFS/NTFS
/dev/sda6         430,073,343   488,391,119    58,317,777   7 HPFS/NTFS
/dev/sda7                 189     7,807,589     7,807,401  82 Linux swap / Solaris
/dev/sda8           7,807,653   389,110,364   381,302,712  83 Linux


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 255 MB, 255066112 bytes
8 heads, 61 sectors/track, 1020 cylinders, total 498176 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System



blkid -c /dev/null: ____________________________________________________________

/dev/sda5: UUID="38F4E9D6F4E99702" TYPE="ntfs" 
/dev/sda6: UUID="00904468904465EE" LABEL="WinSrv2003" TYPE="ntfs" 
/dev/sda7: UUID="e58d8069-1786-4fd2-9195-972efe1dc4bb" TYPE="swap" 
/dev/sda8: UUID="9b32acf3-5d3d-4cd5-bf98-05a525174c30" TYPE="ext3" 
/dev/sdb: SEC_TYPE="msdos" UUID="1234-5678" TYPE="vfat" 

=============================== "mount" output: ===============================

/dev/sda8 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/tuirreanarthri/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=tuirreanarthri)
/dev/scd1 on /media/cdrom1 type iso9660 (ro,nosuid,nodev,utf8,user=tuirreanarthri)
/dev/sdb on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
/dev/sda6 on /media/WINSRV03 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda5 on /media/WINXP type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

=========================== sda8/boot/grub/menu.lst: ===========================

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=9b32acf3-5d3d-4cd5-bf98-05a525174c30 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=9b32acf3-5d3d-4cd5-bf98-05a525174c30

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
uuid		9b32acf3-5d3d-4cd5-bf98-05a525174c30
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=9b32acf3-5d3d-4cd5-bf98-05a525174c30 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		9b32acf3-5d3d-4cd5-bf98-05a525174c30
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=9b32acf3-5d3d-4cd5-bf98-05a525174c30 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		9b32acf3-5d3d-4cd5-bf98-05a525174c30
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda8/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	defaults	0	0
#Entry for /dev/sda8 :
UUID=9b32acf3-5d3d-4cd5-bf98-05a525174c30	/	ext3	relatime,errors=remount-ro	0	1
#Entry for /dev/sda6 :
UUID=00904468904465EE	/media/WINSRV03	ntfs-3g	defaults,locale=en_AU.UTF-8	0	0
#Entry for /dev/sda5 :
UUID=38F4E9D6F4E99702	/media/WINXP	ntfs-3g	defaults,locale=en_AU.UTF-8	0	0
#Entry for /dev/sda7 :
UUID=e58d8069-1786-4fd2-9195-972efe1dc4bb	none	swap	sw	0	0
/dev/scd0	/media/cdrom0	udf,iso9660	user,noauto,exec,utf8	0	0
/dev/scd1	/media/cdrom1	udf,iso9660	user,noauto,exec,utf8	0	0



=================== sda8: Location of files loaded by Grub: ===================


  78.8GB: boot/grub/menu.lst
  78.8GB: boot/grub/stage2
  79.0GB: boot/initrd.img-2.6.27-7-generic
  78.9GB: boot/vmlinuz-2.6.27-7-generic
  79.0GB: initrd.img
  78.9GB: vmlinuz

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdb

00000000  eb fe 90 20 20 20 20 20  20 20 20 00 02 08 01 00  |...        .....|
00000010  02 00 02 00 00 f8 ea 00  20 00 02 00 00 00 00 00  |........ .......|
00000020  00 50 07 00 00 00 29 78  56 34 12 20 20 20 20 20  |.P....)xV4.     |
00000030  20 20 20 20 20 20 46 41  54 31 36 20 20 20 00 00  |      FAT16   ..|
00000040  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000050  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000060  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000070  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000080  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000090  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000100  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000110  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000120  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000130  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000140  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000150  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000160  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

What do I need to do to my menu.lst to get the WinXp install showing up as an option?  

I don't particularly want to stuff anything up, and WinXp installs are such a time consuming pain in the rear that I don't want to have to go through that again.... I was unimpressed enough with uni that i needed it in the first place! :(

many thanks in advance for any help!

cheers,

ibbers

p.s.

I'll also be later doing a WinSrv2003 install on a spare partition as I need it as a test environment for uni later on as well - will i just need to reinstall Ubuntu after that and restore the menu.lst that i'm trying to get working *again* so that it will work after that too?

---

### Post by caljohnsmith on 2009-02-07
Your Windows is installed to sda5 it looks like, and that is a logical partition. That means Windows would have put its boot files in some primary NTFS/FAT partition when you installed it, but you don't have any primary NTFS/FAT partitions (at least not any more). So the bottom line is your sda5 Windows partition is currently missing its boot files. I would recommend following [Meierfra's tutorial]("http://ubuntuforums.org/showthread.php?t=813628") of how to restore Windows boot files to the partition, and also how to configure Windows to boot from a logical partition. Be sure to do the "testdisk" procedure in step 5, because your sda5 boot sector needs fixing in order to be able to boot Windows from that partition. If you have any questions, feel free to post to Meierfra's tutorial thread, or you can post back here and I'll do my best to help you out. Good luck and let me know how it goes.

---

### Post by ibbers on 2009-02-07
thanks caljohnsmith!

the missing boot information would explain, i guess, why this dual boot failed for me as opposed to previous ones.

i'll give it a go, fingers crossed :)

cheers,

ib

---

