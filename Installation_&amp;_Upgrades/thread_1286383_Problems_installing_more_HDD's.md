---
title: "Problems installing more HDD's"
date: 2009-10-08
forum: Installation &amp; Upgrades
---

### Post by ckmccoy on 2009-10-08
I had an old 80GB IDE hard drive sitting around and i wanted to copy things off of it.  When ever install it into my system (which already has a 160 GB ubuntu, and a 500GB vista) my computer won't boot. i get the "Grub loading..." then on the next line i get "error 17" any ideas? i should probably add that i've tried adding a new hard drive before and it never booted then either.

---

### Post by bhaverkamp on 2009-10-08
The two drives you mention are real drives (as opposed to partitions on a single drive)? Are the two drives on the same cable? Is the new disk on it's own cable? If so is it setup to be master? if the two drives were on seperate cables then make sure the new drive is slave.

---

### Post by ckmccoy on 2009-10-09
my vista and ubuntu os's are on separate drives. now i'm having more problems. i managed to set my new drive into slave. but when i reinstalled it i got a new error. i am still getting the same message but a new error. "error 22" then it sits and sits until i press the power button........... so i removed the ide hard drive, set my system back to how i had it, in its working form factor, and it wont' boot. i'm baffled. my computer has now been returned to its old working order and it will not boot. thanks to "error 22" any new ideass?????

---

### Post by presence1960 on 2009-10-09
plug in that 80 GB disk and do this:

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by andy16666 on 2009-10-09
Generally when you put a new drive in, it's best to use a separate cable. If you absolutely have to do a master/slave setup make sure the master drive is configured to "master with slave" and not simply "master" or "single". There is a distinction...master with slave must be used if you want two drives on the same IDE channel.

---

### Post by ckmccoy on 2009-10-09
Here is everything that was inside of the RESULTS.txt file on the desktop.

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on boot drive #2 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

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

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00018b29

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   299,805,029   299,804,967  83 Linux
/dev/sda2         299,805,030   312,576,704    12,771,675   5 Extended
/dev/sda5         299,805,093   312,576,704    12,771,612  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1a4709f3

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   976,770,370   976,768,323   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="78445008-daeb-4212-86bf-83934d5db510" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="6dd3d7a3-5c47-44f8-9bba-eb6051e4b21e" TYPE="swap" 
/dev/sdb1: UUID="386EC9D46EC98B58" TYPE="ntfs" 

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
# kopt=root=UUID=78445008-daeb-4212-86bf-83934d5db510 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=78445008-daeb-4212-86bf-83934d5db510

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

title        Ubuntu 9.04, kernel 2.6.28-15-generic
uuid        78445008-daeb-4212-86bf-83934d5db510
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=78445008-daeb-4212-86bf-83934d5db510 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid        78445008-daeb-4212-86bf-83934d5db510
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=78445008-daeb-4212-86bf-83934d5db510 ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        78445008-daeb-4212-86bf-83934d5db510
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=78445008-daeb-4212-86bf-83934d5db510 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        78445008-daeb-4212-86bf-83934d5db510
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=78445008-daeb-4212-86bf-83934d5db510 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        78445008-daeb-4212-86bf-83934d5db510
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista (loader)
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1


=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=78445008-daeb-4212-86bf-83934d5db510 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=6dd3d7a3-5c47-44f8-9bba-eb6051e4b21e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  57.0GB: boot/grub/menu.lst
  57.1GB: boot/grub/stage2
  57.1GB: boot/initrd.img-2.6.28-11-generic
  57.0GB: boot/initrd.img-2.6.28-15-generic
  57.0GB: boot/vmlinuz-2.6.28-11-generic
  57.0GB: boot/vmlinuz-2.6.28-15-generic
  57.0GB: initrd.img
  57.1GB: initrd.img.old
  57.0GB: vmlinuz
  57.0GB: vmlinuz.old
```

---

### Post by ckmccoy on 2009-10-09
Problem solved. Simply just reinstalled Grub while booting up from one of my live CD's.
The steps i followed are from the following: 

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

this worked perfectly as far as i can tell and only took about 2 minutes of my time.

---

### Post by bhaverkamp on 2009-10-10
Glad to hear it.

---

### Post by presence1960 on 2009-10-10
> **ckmccoy said:**
> Problem solved. Simply just reinstalled Grub while booting up from one of my live CD's.
The steps i followed are from the following: 

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

this worked perfectly as far as i can tell and only took about 2 minutes of my time.

Excellent! Enjoy ubuntu

---

