---
title: "Uninstall second ubuntu install"
date: 2009-03-18
forum: Installation &amp; Upgrades
---

### Post by Amber_Man on 2009-03-18
I am completely new to Linux so be gentle.  I recently became confident with Ubuntu 8.10 and decided was finally ready to dump windows forever, so I deleted my win xp partition.  After that I got error 17 in grub.  I tried in vain to reinstall grub.  I decided to install a second copy of ubuntu, this reinstalled grub and I can now boot my original install of ubuntu. It is listed as other operating systems at start up.

How can I un-install the second copy of ubuntu and not mess up grub?

---

### Post by lindsay7 on 2009-03-18
type sudo fdisk -lu  in the terminal (applications/accessories/terminal)

and they type you password and post your results. This will show what is on your drives and if you do indeed have two copies.

---

### Post by Amber_Man on 2009-03-18
Disk /dev/sda: 118.5 GB, 118526284800 bytes
255 heads, 63 sectors/track, 14410 cylinders, total 231496650 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2              63   231496649   115748293+   f  W95 Ext'd (LBA)
/dev/sda5        22201830    24242084     1020127+  83  Linux
/dev/sda6   *    24242148   177919874    76838863+  83  Linux
/dev/sda7       177919938   179815544      947803+  82  Linux swap / Solaris
/dev/sda8       179815608   184024574     2104483+  82  Linux swap / Solaris
/dev/sda9       184024638   231496649    23736006    7  HPFS/NTFS
/dev/sda10            189     1959929      979870+  83  Linux
/dev/sda11        1959993    22185764    10112886   83  Linux
/dev/sda12       22185828    22201829        8001   82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by upchucky on 2009-03-18
hmm lots of linux partitions there, gonna need more info to sort out which to keep and which partitions to redo.


download this

[http://sourceforge.net/project/platformdownload.php?group_id=250055](http://sourceforge.net/project/platformdownload.php?group_id=250055) 

then do this

```
sudo bash ~/Desktop/boot_info_script*.sh

```

post the results to this forum and indicate which version of ubuntu you were expecting to keep.

---

### Post by Amber_Man on 2009-03-18
The version of Ubuntu I want to keep is in partition sda6

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #11 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda9: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda10: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda11: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda12: _________________________________________________________________________

    File system:       swap
    Boot sector type:  Unknown
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 118.5 GB, 118526284800 bytes
255 heads, 63 sectors/track, 14410 cylinders, total 231496650 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x41ab2316

Partition  Boot         Start           End          Size  Id System

/dev/sda2                  63   231,496,649   231,496,587   f W95 Ext d (LBA)
/dev/sda5          22,201,830    24,242,084     2,040,255  83 Linux
/dev/sda6    *     24,242,148   177,919,874   153,677,727  83 Linux
/dev/sda7         177,919,938   179,815,544     1,895,607  82 Linux swap / Solaris
/dev/sda8         179,815,608   184,024,574     4,208,967  82 Linux swap / Solaris
/dev/sda9         184,024,638   231,496,649    47,472,012   7 HPFS/NTFS
/dev/sda10                189     1,959,929     1,959,741  83 Linux
/dev/sda11          1,959,993    22,185,764    20,225,772  83 Linux
/dev/sda12         22,185,828    22,201,829        16,002  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda5: UUID="117128ad-3b0d-474e-a82c-b8edca1e1a26" TYPE="ext2" 
/dev/sda6: UUID="37740c55-0703-4b99-8ba3-c1c4d2b43638" TYPE="ext3" 
/dev/sda7: TYPE="swap" UUID="fcb78bd1-f2ec-4cb9-90c9-f255f7cc17ef" 
/dev/sda8: TYPE="swap" UUID="ad0ed6e5-ba69-4fb4-be08-6cb90499f5dd" 
/dev/sda9: UUID="5A574E87544F12F5" TYPE="ntfs" 
/dev/sda10: UUID="dfc8793d-3d7e-40c3-9ac6-01ca24b4d23d" TYPE="ext2" 
/dev/sda11: UUID="df00acf3-3599-44b0-877e-8c03b6910866" TYPE="ext3" 
/dev/sda12: TYPE="swap" UUID="d233806d-48a6-46b7-a333-0da6e52ee8db" 

=============================== "mount" output: ===============================

/dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
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
/dev/sda10 on /media/sda10 type ext2 (rw)
/dev/sda11 on /media/sda11 type ext3 (rw)
/dev/sda5 on /media/sda7 type ext2 (rw)
/dev/sda9 on /media/sda9 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/justin/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=justin)
/dev/scd0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,utf8,user=justin)


=========================== sda6/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=37740c55-0703-4b99-8ba3-c1c4d2b43638 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=37740c55-0703-4b99-8ba3-c1c4d2b43638

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
uuid		37740c55-0703-4b99-8ba3-c1c4d2b43638
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=37740c55-0703-4b99-8ba3-c1c4d2b43638 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		37740c55-0703-4b99-8ba3-c1c4d2b43638
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=37740c55-0703-4b99-8ba3-c1c4d2b43638 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		37740c55-0703-4b99-8ba3-c1c4d2b43638
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=37740c55-0703-4b99-8ba3-c1c4d2b43638 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		37740c55-0703-4b99-8ba3-c1c4d2b43638
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=37740c55-0703-4b99-8ba3-c1c4d2b43638 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		37740c55-0703-4b99-8ba3-c1c4d2b43638
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=37740c55-0703-4b99-8ba3-c1c4d2b43638 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		37740c55-0703-4b99-8ba3-c1c4d2b43638
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=37740c55-0703-4b99-8ba3-c1c4d2b43638 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		37740c55-0703-4b99-8ba3-c1c4d2b43638
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	defaults	0	0
#Entry for /dev/sda6 :
UUID=37740c55-0703-4b99-8ba3-c1c4d2b43638	/	ext3	relatime,errors=remount-ro	0	1
#Entry for /dev/sda10 :
UUID=dfc8793d-3d7e-40c3-9ac6-01ca24b4d23d	/media/sda10	ext2	defaults	0	2
#Entry for /dev/sda11 :
UUID=df00acf3-3599-44b0-877e-8c03b6910866	/media/sda11	ext3	defaults	0	2
#Entry for /dev/sda5 :
UUID=117128ad-3b0d-474e-a82c-b8edca1e1a26	/media/sda7	ext2	defaults	0	2
#Entry for /dev/sda9 :
UUID=5A574E87544F12F5	/media/sda9	ntfs-3g	defaults,locale=en_AU.UTF-8	0	0
UUID=578d1125-6297-4cf8-9b17-bfddedfc7393	/media/sda1	ext3	defaults	0	2
UUID=f8a42a8a-9709-40ca-a410-04c9b0177095	/media/sda9	ext3	defaults	0	2
UUID=ae8bafe0-f2cb-41bb-9236-a83c4e586cde	none	swap	sw	0	0
/dev/scd0	/media/cdrom0	udf,iso9660	user,noauto,exec,utf8	0	0
/tmp/app/1/image	/tmp/app/1	cramfs,iso9660	user,noauto,ro,loop,exec	0	0
/tmp/app/2/image	/tmp/app/2	cramfs,iso9660	user,noauto,ro,loop,exec	0	0
/tmp/app/3/image	/tmp/app/3	cramfs,iso9660	user,noauto,ro,loop,exec	0	0
/tmp/app/4/image	/tmp/app/4	cramfs,iso9660	user,noauto,ro,loop,exec	0	0
/tmp/app/5/image	/tmp/app/5	cramfs,iso9660	user,noauto,ro,loop,exec	0	0
/tmp/app/6/image	/tmp/app/6	cramfs,iso9660	user,noauto,ro,loop,exec	0	0
/tmp/app/7/image	/tmp/app/7	cramfs,iso9660	user,noauto,ro,loop,exec	0	0



=================== sda6: Location of files loaded by Grub: ===================


  28.2GB: boot/grub/menu.lst
  28.1GB: boot/grub/stage2
  28.1GB: boot/initrd.img-2.6.27-11-generic
  28.1GB: boot/initrd.img-2.6.27-7-generic
  28.1GB: boot/initrd.img-2.6.27-9-generic
  28.2GB: boot/vmlinuz-2.6.27-11-generic
  28.1GB: boot/vmlinuz-2.6.27-7-generic
  28.1GB: boot/vmlinuz-2.6.27-9-generic
  28.1GB: initrd.img
  28.1GB: initrd.img.old
  28.2GB: vmlinuz
  28.1GB: vmlinuz.old

========================== sda11/boot/grub/menu.lst: ==========================

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
# kopt=root=UUID=df00acf3-3599-44b0-877e-8c03b6910866 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=df00acf3-3599-44b0-877e-8c03b6910866

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
uuid		df00acf3-3599-44b0-877e-8c03b6910866
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=df00acf3-3599-44b0-877e-8c03b6910866 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		df00acf3-3599-44b0-877e-8c03b6910866
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=df00acf3-3599-44b0-877e-8c03b6910866 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		df00acf3-3599-44b0-877e-8c03b6910866
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu 8.10, kernel 2.6.27-11-generic (on /dev/sda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=37740c55-0703-4b99-8ba3-c1c4d2b43638 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode) (on /dev/sda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=37740c55-0703-4b99-8ba3-c1c4d2b43638 ro single 
initrd		/boot/initrd.img-2.6.27-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu 8.10, kernel 2.6.27-9-generic (on /dev/sda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=37740c55-0703-4b99-8ba3-c1c4d2b43638 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode) (on /dev/sda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=37740c55-0703-4b99-8ba3-c1c4d2b43638 ro single 
initrd		/boot/initrd.img-2.6.27-9-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (on /dev/sda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=37740c55-0703-4b99-8ba3-c1c4d2b43638 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode) (on /dev/sda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=37740c55-0703-4b99-8ba3-c1c4d2b43638 ro single 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu 8.10, memtest86+ (on /dev/sda6)
root		(hd0,5)
kernel		/boot/memtest86+.bin  
savedefault
boot


=============================== sda11/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda11
UUID=df00acf3-3599-44b0-877e-8c03b6910866 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda10
UUID=dfc8793d-3d7e-40c3-9ac6-01ca24b4d23d /home           ext2    relatime        0       2
# /dev/sda7
UUID=fcb78bd1-f2ec-4cb9-90c9-f255f7cc17ef none            swap    sw              0       0
# /dev/sda8
UUID=ad0ed6e5-ba69-4fb4-be08-6cb90499f5dd none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda11: Location of files loaded by Grub: ===================


   4.2GB: boot/grub/menu.lst
   4.3GB: boot/grub/stage2
   4.2GB: boot/initrd.img-2.6.27-7-generic
   4.3GB: boot/vmlinuz-2.6.27-7-generic
   4.2GB: initrd.img
   4.3GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda5

00000000  f6 f6 f6 f6 f6 f6 f6 f6  f6 f6 f6 f6 f6 f6 f6 f6  |................|
*
00000200

Unknown BootLoader  on sda12

00000000  62 4b 2b 58 55 72 4c 54  74 63 73 56 75 49 34 62  |bK+XUrLTtcsVuI4b|
00000010  67 4b 79 65 63 46 63 45  42 67 72 73 4d 6e 73 54  |gKyecFcEBgrsMnsT|
00000020  30 7a 0d 0a 58 78 6a 72  6e 2f 42 4e 4c 39 6a 72  |0z..Xxjrn/BNL9jr|
00000030  57 70 5a 5a 4a 50 68 61  62 46 70 62 6c 72 70 6d  |WpZZJPhabFpblrpm|
00000040  73 64 5a 76 6f 63 46 2b  71 67 71 77 2b 58 6a 70  |sdZvocF+qgqw+Xjp|
00000050  6a 41 7a 78 57 79 78 64  57 43 74 47 54 74 32 4a  |jAzxWyxdWCtGTt2J|
00000060  6c 42 62 6e 38 2f 50 2f  41 41 55 32 2f 5a 31 2b  |lBbn8/P/AAU2/Z1+|
00000070  0d 0a 48 33 37 4f 2f 77  41 63 74 45 38 49 2f 44  |..H37O/wActE8I/D|
00000080  4c 52 70 39 45 38 4c 61  70 38 4f 37 50 58 31 74  |LRp9E8Lap8O7PX1t|
00000090  62 6d 39 6d 75 43 39 77  31 78 64 52 53 4e 76 6b  |bm9muC9w1xdRSNvk|
000000a0  4a 50 2f 4c 4a 65 4f 32  50 65 76 7a 47 75 37 58  |JP/LJeO2PevzGu7X|
000000b0  35 6d 34 43 2f 4a 6a 67  56 36 75 49 68 79 0d 0a  |5m4C/JjgV6uIhy..|
000000c0  4b 4e 74 33 46 4f 2f 79  4f 47 4d 72 74 72 73 39  |KNt3FO/yOGMrtrs9|
000000d0  44 6d 74 52 68 45 61 74  39 7a 4a 50 4a 32 39 66  |DmtRhEat9zJPJ29f|
000000e0  65 76 4d 66 45 58 45 44  68 63 41 48 4f 64 76 2b  |evMfEXEDhcAHOdv+|
000000f0  66 72 58 4d 6f 33 31 37  46 7a 6e 30 5a 35 4a 4c  |frXMo317Fzn0Z5JL|
00000100  46 76 75 6c 58 42 4f 5a  75 2f 72 58 0d 0a 61 33  |FvulXBOZu/rX..a3|
00000110  6c 37 39 6a 73 34 49 6b  2b 5a 69 6e 7a 45 6a 72  |l79js4Ik+ZinzEjr|
00000120  2f 39 62 72 57 6a 70 38  37 52 7a 7a 71 63 71 39  |/9brWjp87Rzzqcq9|
00000130  54 34 37 2b 4a 64 39 4a  71 50 69 71 64 44 4a 75  |T47+Jd9JqPiqdDJu|
00000140  2b 78 77 70 46 67 48 37  70 49 33 48 36 63 6e 39  |+xwpFgH7pI3H6cn9|
00000150  4b 35 53 33 74 39 34 77  2f 59 0d 0a 64 54 69 76  |K5S3t94w/Y..dTiv|
00000160  4e 78 47 74 52 2b 52 33  30 6b 31 46 65 5a 59 61  |NxGtR+R30k1FeZYa|
00000170  77 2b 70 4f 42 6a 49 71  71 62 48 42 2b 58 47 4d  |w+pOBjIqqbHB+XGM|
00000180  35 50 76 57 62 67 79 72  39 79 49 32 68 42 36 63  |5PvWbgyr9yI2hB6c|
00000190  6a 67 4e 55 69 57 7a 44  35 74 6f 39 44 6b 56 50  |jgNUiWzD5to9DkVP|
000001a0  4a 5a 6c 58 4c 71 57 79  0d 0a 75 4d 6c 65 57 48  |JZlXLqWy..uMleWH|
000001b0  50 76 55 76 38 41 5a 32  54 6b 6a 47 4d 41 34 48  |PvUv8AZ2TkjGMA4H|
000001c0  51 56 6f 34 57 52 4c 6c  59 2f 30 75 4c 66 58 79  |QVo4WRLlY/0uLfXy|
000001d0  56 42 4c 6e 71 4d 6a 4a  72 55 54 78 42 7a 6a 64  |VBLnqMjJrUTxBzjd|
000001e0  77 54 2f 65 36 56 46 79  58 42 73 75 52 65 49 46  |wT/e6VFyXBsuReIF|
000001f0  47 41 58 39 75 44 0d 0a  6d 72 59 38 52 6f 75 44  |GAX9uD..mrY8RouD|
00000200

---

### Post by upchucky on 2009-03-18
all info is here to correct your install, I must apologize though, fixing this is a bit beyond my abilities however there are plenty other that will know exactly how to redo this. the fix is rather simple, but i do not feel comfortable enough to advise. a little patience and i'm sure that more better brains than mine can get you going again.

---

### Post by lindsay7 on 2009-03-18
I agree. Being that you wanted to get rid of your windows installation anyway and by the looks of you disk as it is (a mess). If it were me I would format the hard drive and start with a nice clean and fresh drive and install Ubuntu from scratch. But, I would wait a little and see if someone has a better idea on how to clean up you partitions and get you going.

---

### Post by Amber_Man on 2009-03-18
Thanks guys.  Reinstalling with a clean drive was my next option.  I did want to avoid that if possible though as I had spent a long time setting up Ubuntu just the way I wanted it.

---

### Post by lindsay7 on 2009-03-18
Take a look at Super Ubuntu (look for on the web). It has a lot of the extra software and drivers that you would normally install already on it. It might same you some time.

---

