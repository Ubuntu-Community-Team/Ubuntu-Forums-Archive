---
title: "Dual Boot-Xp pro &amp; Ubuntu 9.04"
date: 2009-08-05
forum: Installation &amp; Upgrades
---

### Post by CoolPro on 2009-08-05
I just finished building my new PC. I installed XP Pro on it and it booted fine. Then i installed Ubuntu 9.04. I have a 160GB hd, and let XP create one partition the size of the drive, so when i installed linux, i resized it and made it half-and-half. I restarted it and selected Ubuntu from the GRUB bootloader, and it booted perfecly(and fast). But when i select XP it simply displays "Starting Up..". I checked the menu.lst file, and the XP entry looks like
```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Home Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1

```I already have a bunch of stuff installed on both XP and on Ubuntu, so i would hate to have to reinstall one or both OSes. Please help.

SOLVED:  Thanks for the help....I got it to work; now i can boot XP or Ubuntu.

---

### Post by presence1960 on 2009-08-05
Boot into Ubuntu and download to your desktop the [Boot Info Script 0.32]("http://sourceforge.net/projects/bootinfoscript/")
Once downloaded run this command from terminal ```
sudo bash ~/Desktop/boot_info_script*.sh
```
This will create a RESULTS.txt file on your desktop. Paste the contents of that file back here. This will show us your setup including your partition table, boot process and much more info.

---

### Post by CoolPro on 2009-08-05
Ok, here is what the results file contains:
```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders, total 320173056 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x57a457a4

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   104,808,059   104,807,997   7 HPFS/NTFS
/dev/sda2         104,808,060   320,159,384   215,351,325   5 Extended
/dev/sda5         104,808,123   311,323,634   206,515,512  83 Linux
/dev/sda6         311,323,698   320,159,384     8,835,687  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="385CFC595CFC137C" TYPE="ntfs" 
/dev/sda5: UUID="61959fa2-1fae-4529-941b-16d741b0f5db" TYPE="ext3" 
/dev/sda6: UUID="3c9af56e-ff7d-4ae2-868d-402c3cc1a70a" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/daniel/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=daniel)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

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
# kopt=root=UUID=61959fa2-1fae-4529-941b-16d741b0f5db ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=61959fa2-1fae-4529-941b-16d741b0f5db

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

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        61959fa2-1fae-4529-941b-16d741b0f5db
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=61959fa2-1fae-4529-941b-16d741b0f5db ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        61959fa2-1fae-4529-941b-16d741b0f5db
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=61959fa2-1fae-4529-941b-16d741b0f5db ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        61959fa2-1fae-4529-941b-16d741b0f5db
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=61959fa2-1fae-4529-941b-16d741b0f5db /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=3c9af56e-ff7d-4ae2-868d-402c3cc1a70a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  57.8GB: boot/grub/menu.lst
  57.9GB: boot/grub/stage2
  57.8GB: boot/initrd.img-2.6.28-11-generic
  57.8GB: boot/vmlinuz-2.6.28-11-generic
  57.8GB: initrd.img
  57.8GB: vmlinuz

```
thanks

---

### Post by merlinus on 2009-08-05
How did you shrink the xp partition?  Did you defrag beforehand?

The menu.lst entry for xp is correct, so something else must be going on.

---

### Post by CoolPro on 2009-08-05
Actually i took the hard drive out of a direct tv dvr, so it had a bunch of junk on it. I just ran the xp setup, deleted the partition that the dvr had on it, and created a new partition that took up the whole disk. After that i booted xp up, and it worked great. Then i installed ubuntu and resized the windows partition. the direct tv dvr doesn't use fat,fat32 or NTFS. It uses a wierd version of fat...fat64, so when xp pro deleted that partition, it might not of done it right, since the dvr had a wierd file system. Should i run ubuntu off the live CD, erease the hard drive and create two partitions, then install xp on the first and ubuntu on the second? Or is there a way to do it without doing that.   And no...i didn't defragment it.

---

### Post by merlinus on 2009-08-05
If ubuntu is running well, leave it alone.  Use gparted to format sda1 as ntfs, and install xp into it.  Restoring grub afterwards is easy.

---

### Post by CoolPro on 2009-08-05
Well i already deleted all the partitions on the hdd. So should i use gParted to create one for windows, NTFS(ofcourse). I want three partitions- one for windows XP, one for ubuntu, and one more to store files on... So, for the first partition, do i make it the primary partition? I'll give it 50GB. Then should i create one for ubuntu? And what file system, and what type?(Primary, Logical, Extended). And then what about the third? I want it NTFS, should it be logical or extended?  And should i label any of them, and they should all have the 'round to cylinders' checked, right? Quick reply please by anyone who knows...as i'm kinda of a noob.... i want the system up and running as soon as possible. Thanks

---

### Post by merlinus on 2009-08-05
First partition primary ntfs for xp.  Then I would create an extended partition, with logicals for /, /home and /swap, and another ntfs for shared data.

10G for / is plenty, unless you will be installing all sorts of apps.  1.5G for /swap, 7G for /home, and the rest for the shared data.  I would use ext3 for linux, as ext4 is still not stable enough.

---

### Post by theozzlives on 2009-08-05
How about a primary for Windows, Primary for root (/), primary for /home and extended for swap? If you use ext3, an fs driver will let Windows access /home.

---

### Post by CoolPro on 2009-08-05
Ok thanks.  So primary for XP, logical for Linux?  And the extended logical also?

---

### Post by CoolPro on 2009-08-05
theozzlives-just read that....so how many partitions will i have total, just one for ubuntu? Sorry...i'm a noob at this kind of stuff....
 
EDIT: So first, create a partition, make it primary-type: NTFS........then create 1 primary for ubunto type:Ext3.......then create another for my files....NTFS, make it logical...then create one for linux swap-files-Make it logical type: Ext3
That sound right?  Thanks...

---

### Post by theozzlives on 2009-08-05
> **CoolPro said:**
> theozzlives-just read that....so how many partitions will i have total, just one for ubuntu?  Sorry...i'm a noob at this kind of stuff....

Your root only needs 10 GB, an fs (ie: ext2fs) driver will allow Windows share /home (ext3). You'll wind up with 3 Linux (only swap is logical) and one Windows.

---

