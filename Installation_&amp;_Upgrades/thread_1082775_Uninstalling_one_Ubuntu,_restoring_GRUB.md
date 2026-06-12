---
title: "Uninstalling one Ubuntu, restoring GRUB"
date: 2009-02-28
forum: Installation &amp; Upgrades
---

### Post by The Beanjamin on 2009-02-28
I have 4 operating systems installed now on my 640GB harddisk: Vista, 2x Ubuntu 8.10 because I messed one up partly, and Ubuntu 8.04 to see if it was any better than 8.10 (it wasn't). 

I would like to remove the 8.04, but that was the last OS I have installed, so my computer uses this one's GRUB to boot. I think I might break everything if I just remove the 8.04 partition. Is it safe to just remove it, and will the 8.10's GRUB take over, or will the 8.04's remain and crash because it can't find 8.04? If so, how can I make 8.10's GRUB the main one?

I saw an option in the bootmanager to create a repair diskette, but my computer doesn't have a floppy drive. I don't know if it's relevant, but thought I'd mention it anyway.

So to make things clear: I only want to remove the 8.04, the rest has to remain on the drive.

Any help is appreciated.

---

### Post by caljohnsmith on 2009-02-28
You're right, if 8.04 is currently in charge of Grub on start up, you will temporarily break your booting process if you simply delete that partition. Before you do that, it would help to get a clearer picture of your setup to know what might be the best way of changing your boot setup so that everything boots OK after deleting 8.04; how about downloading the **Boot Info Script** to your Ubuntu desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup.

---

### Post by The Beanjamin on 2009-02-28
Ok here it is:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #9 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda9: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.2
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda10: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Schijf /dev/sda: 640.1 GB, 640135028736 bytes
255 koppen, 63 sectoren/spoor, 77825 cilinders, totaal 1250263728 sectoren
Eenheid = sectoren van 1 * 512 = 512 bytes
Schijf-ID: 0xc40104e7

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   944,862,974   944,860,927   7 HPFS/NTFS
/dev/sda2         944,862,975 1,250,258,624   305,395,650   5 Extended
/dev/sda5       1,049,156,955 1,090,122,704    40,965,750  83 Linux
/dev/sda6       1,241,985,213 1,250,258,624     8,273,412  82 Linux swap / Solaris
/dev/sda7         944,863,101 1,044,803,339    99,940,239  83 Linux
/dev/sda8       1,044,803,403 1,049,156,954     4,353,552  82 Linux swap / Solaris
/dev/sda9       1,090,122,768 1,235,703,734   145,580,967  83 Linux
/dev/sda10      1,235,703,798 1,241,985,149     6,281,352  82 Linux swap / Solaris

/dev/sda1 ends after the last cylinder of /dev/sda
/dev/sda2 ends after the last cylinder of /dev/sda
/dev/sda5 ends after the last cylinder of /dev/sda
/dev/sda6 ends after the last cylinder of /dev/sda
/dev/sda7 ends after the last cylinder of /dev/sda
/dev/sda8 ends after the last cylinder of /dev/sda
/dev/sda9 ends after the last cylinder of /dev/sda
/dev/sda10 ends after the last cylinder of /dev/sda

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="D2FE8504FE84E259" TYPE="ntfs" 
/dev/sda5: UUID="6f56e316-1153-40ca-adb6-edab9791351c" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="aa3c7b68-8122-48f2-a69c-a2b0f8037ba4" TYPE="swap" 
/dev/sda7: UUID="a602ecc4-946d-4d4a-a1ac-5947b61e1452" TYPE="ext3" 
/dev/sda8: UUID="40cefc7e-4f9b-4869-9164-09bbc374cf10" TYPE="swap" 
/dev/sda9: UUID="372943e1-4f03-41a1-b06b-d031a8c44118" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda10: UUID="f7e3dd72-ae9e-4c54-92f0-18d588abcce1" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda7 on / type ext3 (rw,relatime,errors=remount-ro)
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
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/benjamin/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=benjamin)


=========================== sda5/boot/grub/menu.lst: ===========================

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
default		8

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
#timeout		10

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
# kopt=root=UUID=6f56e316-1153-40ca-adb6-edab9791351c ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=6f56e316-1153-40ca-adb6-edab9791351c

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
# defoptions=quiet splash vga=795

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
# howmany=1

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=false

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		6f56e316-1153-40ca-adb6-edab9791351c
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=6f56e316-1153-40ca-adb6-edab9791351c ro quiet splash vga=795 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		6f56e316-1153-40ca-adb6-edab9791351c
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=6f56e316-1153-40ca-adb6-edab9791351c ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=6f56e316-1153-40ca-adb6-edab9791351c /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=aa3c7b68-8122-48f2-a69c-a2b0f8037ba4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 554.7GB: boot/grub/menu.lst
 554.7GB: boot/grub/stage2
 554.7GB: boot/initrd.img-2.6.27-11-generic
 554.7GB: boot/initrd.img-2.6.27-7-generic
 554.7GB: boot/initrd.img-2.6.27-9-generic
 554.7GB: boot/vmlinuz-2.6.27-11-generic
 554.7GB: boot/vmlinuz-2.6.27-7-generic
 554.7GB: boot/vmlinuz-2.6.27-9-generic
 554.7GB: initrd.img
 554.7GB: initrd.img.old
 554.7GB: vmlinuz
 554.7GB: vmlinuz.old

=========================== sda7/boot/grub/menu.lst: ===========================

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
#timeout		10

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
# kopt=root=UUID=a602ecc4-946d-4d4a-a1ac-5947b61e1452 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=a602ecc4-946d-4d4a-a1ac-5947b61e1452

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
# howmany=1

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=false

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		a602ecc4-946d-4d4a-a1ac-5947b61e1452
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=a602ecc4-946d-4d4a-a1ac-5947b61e1452 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		a602ecc4-946d-4d4a-a1ac-5947b61e1452
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=a602ecc4-946d-4d4a-a1ac-5947b61e1452 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.10, kernel 2.6.27-11-generic (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=6f56e316-1153-40ca-adb6-edab9791351c ro quiet splash vga=795 
initrd		/boot/initrd.img-2.6.27-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode) (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=6f56e316-1153-40ca-adb6-edab9791351c ro single 
initrd		/boot/initrd.img-2.6.27-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.10, kernel 2.6.27-9-generic (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=6f56e316-1153-40ca-adb6-edab9791351c ro quiet splash vga=795 
initrd		/boot/initrd.img-2.6.27-9-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode) (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=6f56e316-1153-40ca-adb6-edab9791351c ro single 
initrd		/boot/initrd.img-2.6.27-9-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=6f56e316-1153-40ca-adb6-edab9791351c ro quiet splash vga=795 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode) (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=6f56e316-1153-40ca-adb6-edab9791351c ro single 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.10, memtest86+ (on /dev/sda5)
root		(hd0,4)
kernel		/boot/memtest86+.bin  
savedefault
boot


=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=a602ecc4-946d-4d4a-a1ac-5947b61e1452 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda8
UUID=40cefc7e-4f9b-4869-9164-09bbc374cf10 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda7: Location of files loaded by Grub: ===================


 496.2GB: boot/grub/menu.lst
 493.3GB: boot/grub/stage2
 490.2GB: boot/initrd.img-2.6.27-11-generic
 490.3GB: boot/initrd.img-2.6.27-7-generic
 490.2GB: boot/vmlinuz-2.6.27-11-generic
 490.2GB: boot/vmlinuz-2.6.27-7-generic
 490.2GB: initrd.img
 490.3GB: initrd.img.old
 490.2GB: vmlinuz
 490.2GB: vmlinuz.old

=========================== sda9/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=372943e1-4f03-41a1-b06b-d031a8c44118 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,8)

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

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=372943e1-4f03-41a1-b06b-d031a8c44118 ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=372943e1-4f03-41a1-b06b-d031a8c44118 ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.2, memtest86+
root		(hd0,8)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.10, kernel 2.6.27-11-generic (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=6f56e316-1153-40ca-adb6-edab9791351c ro quiet splash vga=795 
initrd		/boot/initrd.img-2.6.27-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode) (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=6f56e316-1153-40ca-adb6-edab9791351c ro single 
initrd		/boot/initrd.img-2.6.27-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda7.
title		Ubuntu 8.10, kernel 2.6.27-11-generic (on /dev/sda7)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=a602ecc4-946d-4d4a-a1ac-5947b61e1452 ro quiet splash vga=795 
initrd		/boot/initrd.img-2.6.27-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda7.
title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode) (on /dev/sda7)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=a602ecc4-946d-4d4a-a1ac-5947b61e1452 ro single 
initrd		/boot/initrd.img-2.6.27-11-generic
savedefault
boot


=============================== sda9/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda9
UUID=372943e1-4f03-41a1-b06b-d031a8c44118 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda10
UUID=f7e3dd72-ae9e-4c54-92f0-18d588abcce1 none            swap    sw              0       0
/dev/sdf1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda9: Location of files loaded by Grub: ===================


 623.7GB: boot/grub/menu.lst
 623.8GB: boot/grub/stage2
 623.8GB: boot/initrd.img-2.6.24-23-generic
 623.8GB: boot/vmlinuz-2.6.24-23-generic
 623.8GB: initrd.img
 623.8GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 
```

---

### Post by caljohnsmith on 2009-02-28
OK, so your two 8.10 installs are on sda5 and sda7, so which one do you want to control Grub on start up? How about doing the following:
```
sudo grub
```
If you want sda5 to control Grub, use (hd0,4) in the following commands, or if you want sda7 to control Grub, use (hd0,6) as shown:
```
grub> root [COLOR="Blue"](hd0,6)[/COLOR]
grub> setup (hd0)
grub> quit
```
Then reboot, see if you can boot into Ubuntu and Vista OK, and if so, it is safe to delete your 8.04 sda9 partition and the sda10 swap partition. Also, I just wanted to mention that your different distros can share the same swap partition, so you don't need a separate swap partition for both your remaining 8.10 partitions. Anyway, let me know how it goes or if you run into problems.

---

### Post by The Beanjamin on 2009-02-28
That worked like a charm. Thanks for your help :smile:

---

### Post by caljohnsmith on 2009-02-28
Glad that worked OK; cheers and enjoy your dual-boot 8.10/Vista setup. :)

---

