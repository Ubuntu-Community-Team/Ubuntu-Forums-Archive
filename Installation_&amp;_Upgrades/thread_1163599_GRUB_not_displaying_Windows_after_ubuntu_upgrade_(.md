---
title: "GRUB not displaying Windows after ubuntu upgrade (and hibernation of Windows)"
date: 2009-05-18
forum: Installation &amp; Upgrades
---

### Post by mchiz on 2009-05-18
I have a dual boot laptop and after a system upgrade to kernal 2.6.27-14 (8.10) GRUB no longer displays Windows XP as an option to boot to.  I downloaded and install the Boot Info Script after coming across one thread ([http://ubuntuforums.org/showpost.php?p=6740172&postcount=5](http://ubuntuforums.org/showpost.php?p=6740172&postcount=5)), the results are here:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
Windows is hibernated, refused to mount.
Failed to mount '/dev/sda1': Operation not permitted
The NTFS partition is hibernated. Please resume and shutdown Windows
properly, or mount the volume read-only with the 'ro' mount option, or
mount the volume read-write with the 'remove_hiberfile' mount option.
For example type on the command line:

            mount -t ntfs-3g /dev/sda1 sda1 -o remove_hiberfile

Windows is hibernated, refused to mount.
Failed to mount '/dev/sda1': Operation not permitted
The NTFS partition is hibernated. Please resume and shutdown Windows
properly, or mount the volume read-only with the 'ro' mount option, or
mount the volume read-write with the 'remove_hiberfile' mount option.
For example type on the command line:

            mount -t ntfs-3g /dev/sda1 sda1 -o remove_hiberfile


sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00067dd8

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    41,736,869    41,736,807   7 HPFS/NTFS
/dev/sda2          41,736,870   196,667,729   154,930,860  83 Linux
/dev/sda3         196,667,730   228,251,519    31,583,790  83 Linux
/dev/sda4         228,251,520   234,436,544     6,185,025  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="0B41B4631702BC6E" LABEL="Redmond" TYPE="ntfs" 
/dev/sda2: UUID="c1d9af49-8463-400b-88d6-d0cd3d5314e8" TYPE="ext3" 
/dev/sda3: UUID="6d18f913-3067-49c1-bb33-08fd120fd187" TYPE="ext3" 
/dev/sda4: UUID="f6793cc8-de9d-4678-bd06-26d191104fc8" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda3 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-14-generic/volatile type tmpfs (rw,mode=755)
/dev/sda2 on /home type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/matt/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=matt)
/dev/scd0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,utf8,user=matt)


=========================== sda3/boot/grub/menu.lst: ===========================

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
default		1

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		4

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
# kopt=root=UUID=6d18f913-3067-49c1-bb33-08fd120fd187 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=6d18f913-3067-49c1-bb33-08fd120fd187

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

title		Ubuntu 8.10, kernel 2.6.27-14-generic
uuid		6d18f913-3067-49c1-bb33-08fd120fd187
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=6d18f913-3067-49c1-bb33-08fd120fd187 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-14-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-14-generic (recovery mode)
uuid		6d18f913-3067-49c1-bb33-08fd120fd187
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=6d18f913-3067-49c1-bb33-08fd120fd187 ro  single
initrd		/boot/initrd.img-2.6.27-14-generic

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		6d18f913-3067-49c1-bb33-08fd120fd187
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=6d18f913-3067-49c1-bb33-08fd120fd187 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		6d18f913-3067-49c1-bb33-08fd120fd187
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=6d18f913-3067-49c1-bb33-08fd120fd187 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		6d18f913-3067-49c1-bb33-08fd120fd187
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=6d18f913-3067-49c1-bb33-08fd120fd187 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		6d18f913-3067-49c1-bb33-08fd120fd187
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=6d18f913-3067-49c1-bb33-08fd120fd187 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		6d18f913-3067-49c1-bb33-08fd120fd187
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=6d18f913-3067-49c1-bb33-08fd120fd187 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		6d18f913-3067-49c1-bb33-08fd120fd187
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=6d18f913-3067-49c1-bb33-08fd120fd187 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		6d18f913-3067-49c1-bb33-08fd120fd187
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=6d18f913-3067-49c1-bb33-08fd120fd187 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=c1d9af49-8463-400b-88d6-d0cd3d5314e8 /home           ext3    relatime        0       2
# /dev/sda4
UUID=f6793cc8-de9d-4678-bd06-26d191104fc8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda3: Location of files loaded by Grub: ===================


 107.4GB: boot/grub/menu.lst
 107.4GB: boot/grub/stage2
 107.4GB: boot/initrd.img-2.6.27-11-generic
 107.4GB: boot/initrd.img-2.6.27-14-generic
 107.5GB: boot/initrd.img-2.6.27-7-generic
 107.5GB: boot/initrd.img-2.6.27-9-generic
 107.4GB: boot/vmlinuz-2.6.27-11-generic
 107.5GB: boot/vmlinuz-2.6.27-14-generic
 107.4GB: boot/vmlinuz-2.6.27-7-generic
 107.4GB: boot/vmlinuz-2.6.27-9-generic
 107.4GB: initrd.img
 107.4GB: initrd.img.old
 107.5GB: vmlinuz
 107.4GB: vmlinuz.old
```

my menu.lst is:
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
default		1

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		4

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
# kopt=root=UUID=6d18f913-3067-49c1-bb33-08fd120fd187 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=6d18f913-3067-49c1-bb33-08fd120fd187

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

title		Ubuntu 8.10, kernel 2.6.27-14-generic
uuid		6d18f913-3067-49c1-bb33-08fd120fd187
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=6d18f913-3067-49c1-bb33-08fd120fd187 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-14-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-14-generic (recovery mode)
uuid		6d18f913-3067-49c1-bb33-08fd120fd187
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=6d18f913-3067-49c1-bb33-08fd120fd187 ro  single
initrd		/boot/initrd.img-2.6.27-14-generic

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		6d18f913-3067-49c1-bb33-08fd120fd187
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=6d18f913-3067-49c1-bb33-08fd120fd187 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		6d18f913-3067-49c1-bb33-08fd120fd187
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=6d18f913-3067-49c1-bb33-08fd120fd187 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		6d18f913-3067-49c1-bb33-08fd120fd187
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=6d18f913-3067-49c1-bb33-08fd120fd187 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		6d18f913-3067-49c1-bb33-08fd120fd187
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=6d18f913-3067-49c1-bb33-08fd120fd187 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		6d18f913-3067-49c1-bb33-08fd120fd187
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=6d18f913-3067-49c1-bb33-08fd120fd187 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		6d18f913-3067-49c1-bb33-08fd120fd187
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=6d18f913-3067-49c1-bb33-08fd120fd187 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		6d18f913-3067-49c1-bb33-08fd120fd187
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

thanks in advance for any help!

---

### Post by mchiz on 2009-05-18
I guess I should specify: I tried the advised ```
mount -t ntfs-3g /dev/sda1 sda1 -o remove_hiberfile
```
to no avail and because windows doesn't show in grub, I can't resume to shutdown as also suggested.

---

### Post by lindsay7 on 2009-05-18
One thing you need to do is add this at the end of your grub menu file.

title		Windows 95/98/NT/2000
root		(hd0,0)
makeactive
chainloader	+1


type "sudo gedit /boot/grub/menu.lst" add the lines above and save the file.  This will make windows a boot option and you should be able to start windows if your mbr and windows loader in order.  If you are booting XP or Vista you can change that title in the above.  Make sure you add the above four lines below ### END DEBIAN AUTOMAGIC KERNELS LIST,

---

### Post by mchiz on 2009-05-18
wow, simple enough.
That was my feeling but wasnt sure on specifics.  Thanks for the help!

---

