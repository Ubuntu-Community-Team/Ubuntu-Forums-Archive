---
title: "Ubuntu 8.10 dual boot with XP sp2"
date: 2009-05-08
forum: Installation &amp; Upgrades
---

### Post by Aglow,_Phoenix on 2009-05-08
**How do I use the NT bootloader to dual boot Windows XP and Ubuntu 8.10?**  Thank you for your help.

I am attempting to install Ubuntu 8.10 on an exterior second HD.  I get a dual boot window where I selected Ubuntu from, then I get a black screen with only a flashing underline in the upper left hand corner.  I believe there were no other notices, including no "Please wait, loading . . . "

I ran bootinfoscript.sh and received the following RESULTS.txt:

```
======== Boot Info Summary: ============

 => HP/Gateway is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
 => Grub0.97 is installed in the MBR of /dev/sdc and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     Grub0.97 in the file /bootsect.lnx looks at sector 1 
                       of the same hard drive for the stage2 file. A stage2 
                       file is at this location on /dev/sdc. Stage2 looks on 
                       the same partition for /boot/grub/stage2.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  HP Recovery
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ntldr /NTLDR /NTDETECT.COM /ntdetect.com

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdc2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     Grub in the file /bootsect.lnx looks at sector on boot 
                       drive #-127 for the stage2 file, but no stage2 files 
                       can be found at this location.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2aea2aea

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *      9,333,765   390,700,799   381,367,035   7 HPFS/NTFS
/dev/sda2                  63     9,333,764     9,333,702   b W95 FAT32


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9a03910a

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   160,071,659   160,071,597   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000098ec

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   122,881,184   122,881,122  83 Linux
/dev/sdc2         122,881,185   126,977,759     4,096,575  82 Linux swap / Solaris
/dev/sdc3         126,977,760   976,768,064   849,790,305  17 Hidden HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="B634A80934A7CB27" LABEL="1st HD" TYPE="ntfs" 
/dev/sda2: LABEL="WINDOWS XP" UUID="423B-2BDF" TYPE="vfat" 
/dev/sdb1: UUID="FA082A9F082A5B41" LABEL="Shawn's Documents" TYPE="ntfs" 
/dev/sdc1: UUID="b2d1d860-943b-4ba0-8ac8-a0971e54bca1" TYPE="ext3" 
/dev/sdc2: UUID="20feffd9-1f3b-4f29-b72d-6bb3763fd20e" TYPE="swap" 
/dev/sdc3: UUID="CA4C4A5E4C4A4603" LABEL="Backup HD" TYPE="ntfs" 
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
/dev/scd1 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdc3 on /media/Backup HD type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdc1 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect
C:\bootsect.lnx="Ubuntu 8.10"
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
# kopt=root=UUID=b2d1d860-943b-4ba0-8ac8-a0971e54bca1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=b2d1d860-943b-4ba0-8ac8-a0971e54bca1

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

title        Ubuntu 8.10, kernel 2.6.27-7-generic
uuid        b2d1d860-943b-4ba0-8ac8-a0971e54bca1
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=b2d1d860-943b-4ba0-8ac8-a0971e54bca1 ro quiet 
initrd        /boot/initrd.img-2.6.27-7-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid        b2d1d860-943b-4ba0-8ac8-a0971e54bca1
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=b2d1d860-943b-4ba0-8ac8-a0971e54bca1 ro  single
initrd        /boot/initrd.img-2.6.27-7-generic

title        Ubuntu 8.10, memtest86+
uuid        b2d1d860-943b-4ba0-8ac8-a0971e54bca1
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Home Edition
root        (hd0,0)
savedefault
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows NT/2000/XP
root        (hd0,1)
savedefault
chainloader    +1


=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc1
UUID=b2d1d860-943b-4ba0-8ac8-a0971e54bca1 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdc2
UUID=20feffd9-1f3b-4f29-b72d-6bb3763fd20e none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdc1: Location of files loaded by Grub: ===================


  23.2GB: boot/grub/menu.lst
  23.2GB: boot/grub/stage2
  23.2GB: boot/initrd.img-2.6.27-7-generic
  23.2GB: boot/vmlinuz-2.6.27-7-generic
  23.2GB: initrd.img
  23.2GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdd sde sdf sdg 
=============================== StdErr Messages: ===============================

hexdump: /media/Backup: No such file or directory
hexdump: HD/bootsect.lnx: No such file or directory
./boot_info_script032.sh: line 590: [: -lt: unary operator expected
./boot_info_script032.sh: line 590: [: -lt: unary operator expected
./boot_info_script032.sh: line 590: [: -lt: unary operator expected
```

---

### Post by caljohnsmith on 2009-05-08
If Windows and Ubuntu are on different drives, you have to install Grub to the boot sector of your Ubuntu partition in a special way if you want to copy that boot sector to use with the Windows boot loader. How about trying the following from your Live CD:
```
sudo grub
grub> device (hd0) /dev/sdc
grub> device (hd2) /dev/sdc
grub> root (hd2,0)
grub> setup (hd0,0)
grub> quit
```
Then copy the boot sector as you did before ("bootsect.lnx"), and see if that works. The above Grub commands assume that your Ubuntu sdc drive is the third boot drive in your BIOS boot order. If it doesn't work, probably the sdc drive is the second boot drive, so the Grub commands would instead be:
```
sudo grub
grub> device (hd0) /dev/sdc
grub> device (hd1) /dev/sdc
grub> root (hd1,0)
grub> setup (hd0,0)
grub> quit
```
Let me know how that goes or if you run into problems still.

John

---

### Post by Aglow,_Phoenix on 2009-05-09
I thought I could delete this post.

---

### Post by Aglow,_Phoenix on 2009-05-09
I need to replace the new DVD burner.  I'll get back to you.  Thanks.

---

### Post by Aglow,_Phoenix on 2009-05-15
We tried both of those and it still didn't work.

After trying each of the code sequences, I received a black screen with only the following in the upper left corner:

Grub _

During the second code sequence, when I entered the setup command, I received the following:

```
grub> setup (hd0,0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,0)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd1,0)"... failed (this is not fatal)
 Running "install /boot/grub/stage1 d (hd0,0) /boot/grub/stage2 p /boot/grub/me
nu.lst "... succeeded
Done.
```We hope someone can still help.


Thanks,
Phoenix Aglow

---

### Post by Aglow,_Phoenix on 2009-05-21
Does anyone have any further suggestions?

Thank you.

---

