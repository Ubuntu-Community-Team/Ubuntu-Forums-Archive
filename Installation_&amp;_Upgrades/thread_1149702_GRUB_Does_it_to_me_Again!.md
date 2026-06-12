---
title: "GRUB Does it to me Again!"
date: 2009-05-05
forum: Installation &amp; Upgrades
---

### Post by the.scarecrow on 2009-05-05
I'm hopeless with GRUB but I don't think its badly broken, please help.

Its a Dell D600 Laptop with a 160GB hard drive divided into three main 50GB partitions as follows:-
Win XP on sda1
a little Swap sda5
Ubuntu 8.10 on sda6
and an unformated partition

I have been using the partitions above for months without problems till today when I installed:-
Ubuntu 9.04 on sda7, in the spare unformatted partition.

Installation of Jaunty went OK until restart was required and now I get:

GRUB loading stage 1.5

GRUB loading, please wait
Error 18

Here is the RESULTS from ```
sudo bash boot_info_script024.sh
```

This is about the limit of my ability so please help me out with what to do to fix it.

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #7 for /boot/grub/stage2 and /boot/grub/menu.lst.

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

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00023415

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   101,562,929   101,562,867   7 HPFS/NTFS
/dev/sda2         101,562,930   312,576,704   211,013,775   5 Extended
/dev/sda5         101,562,993   104,486,759     2,923,767  82 Linux swap / Solaris
/dev/sda6         104,486,823   208,523,699   104,036,877  83 Linux
/dev/sda7         208,523,763   312,576,704   104,052,942  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="B01C32061C31C85C" TYPE="ntfs" 
/dev/sda5: TYPE="swap" UUID="a1d4659b-6d99-4cb5-a048-835ec5ab079f" 
/dev/sda6: UUID="c87e29cc-eb1d-4daa-a142-804c2333f39a" TYPE="ext3" 
/dev/sda7: UUID="a3326b78-7f1a-4cf5-8b38-cebbc6c0f7c5" TYPE="ext3" 

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
/dev/sda7 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sda1 on /media/disk-1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda6 on /media/disk-2 type ext3 (rw,nosuid,nodev,uhelper=hal)

================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


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
# kopt=root=UUID=c87e29cc-eb1d-4daa-a142-804c2333f39a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=c87e29cc-eb1d-4daa-a142-804c2333f39a

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
uuid		c87e29cc-eb1d-4daa-a142-804c2333f39a
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=c87e29cc-eb1d-4daa-a142-804c2333f39a ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		c87e29cc-eb1d-4daa-a142-804c2333f39a
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=c87e29cc-eb1d-4daa-a142-804c2333f39a ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		c87e29cc-eb1d-4daa-a142-804c2333f39a
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=c87e29cc-eb1d-4daa-a142-804c2333f39a ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		c87e29cc-eb1d-4daa-a142-804c2333f39a
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=c87e29cc-eb1d-4daa-a142-804c2333f39a ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		c87e29cc-eb1d-4daa-a142-804c2333f39a
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
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=c87e29cc-eb1d-4daa-a142-804c2333f39a /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda1
UUID=B01C32061C31C85C /windows        ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=a1d4659b-6d99-4cb5-a048-835ec5ab079f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


  88.9GB: boot/grub/menu.lst
  88.9GB: boot/grub/stage2
  88.9GB: boot/initrd.img-2.6.27-11-generic
  88.9GB: boot/initrd.img-2.6.27-7-generic
  88.9GB: boot/vmlinuz-2.6.27-11-generic
  88.9GB: boot/vmlinuz-2.6.27-7-generic
  88.9GB: initrd.img
  88.9GB: initrd.img.old
  88.9GB: vmlinuz
  88.9GB: vmlinuz.old

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
# kopt=root=UUID=a3326b78-7f1a-4cf5-8b38-cebbc6c0f7c5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=a3326b78-7f1a-4cf5-8b38-cebbc6c0f7c5

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
uuid		a3326b78-7f1a-4cf5-8b38-cebbc6c0f7c5
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=a3326b78-7f1a-4cf5-8b38-cebbc6c0f7c5 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		a3326b78-7f1a-4cf5-8b38-cebbc6c0f7c5
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=a3326b78-7f1a-4cf5-8b38-cebbc6c0f7c5 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		a3326b78-7f1a-4cf5-8b38-cebbc6c0f7c5
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
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu 8.10, kernel 2.6.27-11-generic (on /dev/sda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=c87e29cc-eb1d-4daa-a142-804c2333f39a ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode) (on /dev/sda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=c87e29cc-eb1d-4daa-a142-804c2333f39a ro single 
initrd		/boot/initrd.img-2.6.27-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (on /dev/sda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=c87e29cc-eb1d-4daa-a142-804c2333f39a ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode) (on /dev/sda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=c87e29cc-eb1d-4daa-a142-804c2333f39a ro single 
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


=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=a3326b78-7f1a-4cf5-8b38-cebbc6c0f7c5 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=a1d4659b-6d99-4cb5-a048-835ec5ab079f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda7: Location of files loaded by Grub: ===================


 150.0GB: boot/grub/menu.lst
 150.0GB: boot/grub/stage2
 150.0GB: boot/initrd.img-2.6.28-11-generic
 150.1GB: boot/vmlinuz-2.6.28-11-generic
 150.0GB: initrd.img
 150.1GB: vmlinuz

```

---

### Post by caljohnsmith on 2009-05-05
> **the.scarecrow said:**
> ```

=================== sda6: Location of files loaded by Grub: ===================


  88.9GB: boot/grub/menu.lst
  88.9GB: boot/grub/stage2
  88.9GB: boot/initrd.img-2.6.27-11-generic
  88.9GB: boot/initrd.img-2.6.27-7-generic
  88.9GB: boot/vmlinuz-2.6.27-11-generic
  88.9GB: boot/vmlinuz-2.6.27-7-generic
  88.9GB: initrd.img
  88.9GB: initrd.img.old
  88.9GB: vmlinuz
  88.9GB: vmlinuz.old

=================== sda7: Location of files loaded by Grub: ===================


 150.0GB: boot/grub/menu.lst
 150.0GB: boot/grub/stage2
 150.0GB: boot/initrd.img-2.6.28-11-generic
 150.1GB: boot/vmlinuz-2.6.28-11-generic
 150.0GB: initrd.img
 150.1GB: vmlinuz

```
A Grub error 18 typically occurs when you have a BIOS that can't access anything on a HDD past either 8.4 GB or 137 GB, depending on how old the BIOS is. In your case it looks pretty clear that your BIOS must have the 137 GB limit, because your Ubuntu 8.10 boot files in the sda6 partition are all located ~89 GB from the beginning of your drive, but your Jaunty install boot files in sda7 are all located ~150 GB from the start of the drive (see above). Since all your 8.10 boot files are within the 137 GB limit, that would explain why you were previously able to boot 8.10 with no problems, but now your Jaunty boot files are all outside that limit, leading to your Grub problems. 

So to fix a Grub error 18 like you are experiencing, you need to somehow relocate Grub's/Jaunty's boot files within your 137 GB BIOS limit. Fortunately your sda6 Ubuntu 8.10 partition ends at about ~107 GB from the start of the HDD, so what you could do is set up a ~200 MB boot partition right after sda6 for your Jaunty and Grub boot files, and then reinstall Jaunty. You can create the boot partition manually with gparted (System > Admin > Partition Editor), or you can do it using the "manual" partition option in the installer. Once you have the boot partition created, just go through the Ubuntu installer like you did before, but this time set the mount point on your newly created ~200 MB boot partition as "/boot". Good luck and let me know how it goes or if you run into problems.

John

---

### Post by the.scarecrow on 2009-05-05
Hi John

Thanks for your reply, it was you that rescued me last time I had GRUB problems.

I'm going to re-read your post, several times then try to do what you suggest. I'll be back with more questions or some results because I have a couple of hours to fiddle with it now.

Thanks again

---

### Post by the.scarecrow on 2009-05-05
> **caljohnsmith said:**
> A Grub error 18 typically occurs when you have a BIOS that can't access anything on a HDD past either 8.4 GB or 137 GB, depending on how old the BIOS is. In your case it looks pretty clear that your BIOS must have the 137 GB limit, because your Ubuntu 8.10 boot files in the sda6 partition are all located ~89 GB from the beginning of your drive, but your Jaunty install boot files in sda7 are all located ~150 GB from the start of the drive (see above). Since all your 8.10 boot files are within the 137 GB limit, that would explain why you were previously able to boot 8.10 with no problems, but now your Jaunty boot files are all outside that limit, leading to your Grub problems. 

So to fix a Grub error 18 like you are experiencing, you need to somehow relocate Grub's/Jaunty's boot files within your 137 GB BIOS limit. Fortunately your sda6 Ubuntu 8.10 partition ends at about ~107 GB from the start of the HDD, so what you could do is set up a ~200 MB boot partition right after sda6 for your Jaunty and Grub boot files, and then reinstall Jaunty. You can create the boot partition manually with gparted (System > Admin > Partition Editor), or you can do it using the "manual" partition option in the installer. Once you have the boot partition created, just go through the Ubuntu installer like you did before, but this time set the mount point on your newly created ~200 MB boot partition as "/boot". Good luck and let me know how it goes or if you run into problems.

John

So I re-run the Jaunty installer till I get to the Partitioner
select "manual" and make sda7 spare
create a 200MB boot partition (is that a / partition SW3?)
then use the remaining disk space for Jaunty (is that also / partition SW3)
Will Jaunty use the existing Swap partition? I just assumed it would.

I'm on line with a spare PC at the moment.

---

### Post by caljohnsmith on 2009-05-05
I personally would set up your partitions beforehand with gparted rather than using the installer to do it, but it's up to you. I don't understand what you mean with the notation "SW3"--what does that refer to? The bottom line is I would delete sda7, create a ~200 MB logical ext3 partition right after sda6 (that will become sda7), and then create another logical partition with the remaining space for Jaunty (that will become sda8 ). Then when you go through the installer, set the mount point on sda7 as "/boot", and set the mount point on sda8 as "/". Let me know how that goes or if you run into problems.

John

---

### Post by the.scarecrow on 2009-05-05
> **caljohnsmith said:**
> I personally would set up your partitions beforehand with gparted rather than using the installer to do it, but it's up to you. I don't understand what you mean with the notation "SW3"--what does that refer to? The bottom line is I would delete sda7, create a ~200 MB logical ext3 partition right after sda6 (that will become sda7), and then create another logical partition with the remaining space for Jaunty (that will become sda8). Then when you go through the installer, set the mount point on sda7 as "/boot", and set the mount point on sda8 as "/". Let me know how that goes or if you run into problems.

John

When I say SW3, I mean ext3 cos I'm an idiot.

I have done what you suggested with lots of results. GRUB now works Yeh! and I get the choice of 9.04, Windows and 8.10. The smallest /boot sector it let me create was 8MB.

I selected 9.04 and got lots of messages including Kernal panic just before the laptop locked up.

Then I selected 8.10 and this works but at login it said something about two users of the same home file. However, 8.10 seems to work normally and I am testing it at the moment.

Windows works OK.

I need to copy out the error messages from 9.04 and 8.10 and then I will post them here.

Thanks John, already a big step forward, I can use my laptop again.

---

### Post by caljohnsmith on 2009-05-05
> **the.scarecrow said:**
>  The smallest /boot sector it let me create was 8MB.

Did you make the boot partition just 8 MB? If so, that's going to be too small--it should be ~200 MB or so like I previously mentioned. Were you able to actually install Jaunty while setting the mount point on that partition as "/boot"? At least it sounds like you're making some good progress. :)

John

---

### Post by the.scarecrow on 2009-05-05
> **caljohnsmith said:**
> Did you make the boot partition just 8 MB? If so, that's going to be too small--it should be ~200 MB or so like I previously mentioned. Were you able to actually install Jaunty while setting the mount point on that partition as "/boot"? At least it sounds like you're making some good progress. :)

John

Yes I made /boot ext3 8MB as sda7 (I suppose I got that a bit wrong then)
then the remaining space into / ext3 as sda8
Jaunty seemed to install OK but when I select it from GRUB
GRUB entry "9.04 kernel 2.6.28-11-generic"

```
Boot from (hd0,6) ext3 e298e52c-8d4f-4698-ba8b-5fafd329e692

Starting up...
[ 1.489767] IO APIC resources could not be allocated.
[ 1.592303] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block (0,0)

```

Just after logging into 8.10 it pops up thi message.
```
Users $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. Users $HOME directory must be owned by user and not writable by other users.
```

Apart from that message 8.10 appears to work OK.

I'm gonna have to leave it to tomorrow now as I have to make an early start in the morning.

Thanks a bunch John, speak to you again tomorrow evening.

---

### Post by the.scarecrow on 2009-05-06
OK, I will re-instal Jaunty again later this evening with 200MB /boot sector and I will use a different user name in case its clashing with the existing Intrepid user name.

I will let you know how I get on.

---

### Post by the.scarecrow on 2009-05-06
Hi John

You truly are a STAR :KS, what would I and Ubuntu do without you? I am posting this to you from a nice fresh Jaunty installation and I can boot into Intrepid or WindowsXP so that's perfect. 

I can access all three file systems and Jaunty looks great and seems to boot fast. No video problems with my ATI graphics card but I use Open Source drivers so I thought it would work OK.

Seems I was too quick to blame GRUB as your diagnosis that it was my BIOS and suggested fix were spot on. Pity I can't follow instructions very well and get it right 1st time.

I still get this error message just after booting into Intrepid.

"Users $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. Users $HOME directory must be owned by user and not writable by other users."

I don't know what it means but everything seems to work OK and I am migrating away from Intrepid to Jaunty so I wont need to use it much. Eventually I will delete the 8.10 partition and replace it with 9.10. Lets hope I don't break GRUB when I come to do that.

---

### Post by caljohnsmith on 2009-05-06
That's great news, I'm glad to hear you have Jaunty booting now with no more Grub error 18. About the error you are getting with the ".dmrc" file in your Intrepid install, I think I can help you fix that if you want help with it, but how about first posting the following while you are booted into your Intrepid install:
```
ls -l /home
ls -al /home/*/.dmrc
```
And we can work from there. :)

John

---

### Post by the.scarecrow on 2009-05-07
Hi John

Here is the output I get in 8.10

```
roger@roger-DellD600:~$ ls -l /home
total 4
drwxrwxrwx 59 roger roger 4096 2009-05-07 21:45 roger
roger@roger-DellD600:~$ 

```
and
```
roger@roger-DellD600:~$ ls -al /home/*/.dmrc
-rw------- 1 roger roger 28 2009-05-04 21:03 /home/roger/.dmrc
roger@roger-DellD600:~$ 

```

That's it

p.s Jaunty looks F A N T A S T I C.

---

### Post by caljohnsmith on 2009-05-07
> **the.scarecrow said:**
> 
```
roger@roger-DellD600:~$ ls -l /home
total 4
[COLOR="Red"]drwxrwxrwx[/COLOR] 59 roger roger 4096 2009-05-07 21:45 roger
roger@roger-DellD600:~$ 

```

I think the problem is your home directory is writable by everyone, when the permissions should be set so only you can write to it. How about doing the following while you are booted into Intrepid:
```
chmod 755 /home/roger
```
Then reboot back into Intrepid, and let me know if you still get the same .dmrc error.

John

---

