---
title: "GRUB Error 17: Linux only drive (/ swap /home)"
date: 2009-03-25
forum: Installation &amp; Upgrades
---

### Post by David Brant on 2009-03-25
Hello

I get GRUB Loading Stage 1.5 ... Error 17 on my Linux only hard drive backup copy (Ubuntu 8.10 Desktop).:(

The backup was made using the System Rescue CD, and went faultlessly from start to finish!:)

On the drive I have an extended partition inside which are the /, swap and /home partitions. The 2 backups were correctly applied to the sda5 and sda7 devices.

I have inspected the contents of the partitions with the working drive, and they each look identical to the last detail.

Having followed advice detailed for such an error (Herman's Super Grub Disk Documentation) including fault checking, etc, I have had to stop at GRUB stage as I'm getting out of my depth. I am now in need some kind expert advice and feedback to progress further.

My first impression was has to be a relatively simple scenario to sort ... but ...doh!

I can provide the following details as perhaps a starting point.

sudo fdisk -l produces
-------------------------------------------------------------------------
Disk /dev/sda: 10.1 GB, 10110320640 bytes
255 heads, 63 sectors/track, 1229 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1637cc5a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1229     9871911    5  Extended
/dev/sda5               1         587     4715014+  83  Linux
/dev/sda6             588         652      522081   82  Linux swap / Solaris
/dev/sda7             653        1229     4634721   83  Linux
-------------------------------------------------------------------------

/etc/fstab
-------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=243d1c9f-d7e8-4c32-8560-557d0bb98b97 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=b67e2f73-9f31-4e1d-b37c-258e505e98df /home           ext3    relatime        0       2
# /dev/sda6
UUID=95187bcc-822a-4592-9182-9682ccc0dd37 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
-------------------------------------------------------------------------

/boot/grub/menu.lst
-------------------------------------------------------------------------
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

etc, etc

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		(hd0,1)
uuid		243d1c9f-d7e8-4c32-8560-557d0bb98b97
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=243d1c9f-d7e8-4c32-8560-557d0bb98b97 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root		(hd0,1)
uuid		243d1c9f-d7e8-4c32-8560-557d0bb98b97
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=243d1c9f-d7e8-4c32-8560-557d0bb98b97 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,1)
uuid		243d1c9f-d7e8-4c32-8560-557d0bb98b97
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
-------------------------------------------------------------------------

[COLOR="Red"]The root (hd0,1) lines were added as part of my diagnostics, but had no effect[/COLOR]


/boot/grub/device.map
-------------------------------------------------------------------------
(hd0)	/dev/sda
-------------------------------------------------------------------------

Finally running grub gives
-------------------------------------------------------------------------
grub> find /boot/grub/stage1
 (hd0,4)

grub> find /boot/grub/stage2
 (hd0,4)
-------------------------------------------------------------------------

I am really stumped and desperately need to get this matter sorted somehow without re-installation every time.

Any feedback would be very much appreciated.

Thank you

---

### Post by David Brant on 2009-03-25
I forgot to mention the / and /home partition backups were made with PartImage, not GParted with copy and paste, to avoid possible UUID numbering problems.

---

### Post by unutbu on 2009-03-25
Hello David,
Perhaps try booting from an Ubuntu 8.10 LiveCD, open a terminal and type
```

sudo mount /dev/sda5 /mnt
gksu gedit /mnt/boot/grub/menu.lst
```

Remove the "root (hd0,1)" lines.
Instead, try adding
```

title Ubuntu 8.10, **Test #1**
**uuid 243d1c9f-d7e8-4c32-8560-557d0bb98b97**
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=243d1c9f-d7e8-4c32-8560-557d0bb98b97 ro quiet splash
initrd /boot/initrd.img-2.6.27-7-generic
quiet

title Ubuntu 8.10, **Test #2**
**root (hd0,4)**
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=243d1c9f-d7e8-4c32-8560-557d0bb98b97 ro quiet splash
initrd /boot/initrd.img-2.6.27-7-generic
quiet
```

Save and exit gedit. Reboot, get to the GRUB menu and try booting using the Test #1 and Test #2 stanzas. Do either of them work? If they both fail, please post back with what you see, and what GRUB Error number you encounter for each.

---

### Post by David Brant on 2009-03-26
Hello unutbu,

I followed your kind instructions, but unfortunately the final reboot got me back to GRUB Error 17. I guess both tests failed.

I have included the latest menu.lst for reference.

Just to add a little to the matter. Each drive (working and backup) and their respective partitions are of different capacities and sizes.

But that shouldn't matter should it!, well...

With my particular BIOS i have to set all IDE drives to auto-detect, otherwise they are not recognised. I have noticed that if i boot with my working drive as master and backup drive as slave, the backup drive does not appear under the Places dropwown, nor is it displayed in System Monitor/File Systems. It just doesn't appear to be there. Is this to be expected?

Connecting up working drive with the intermediate backup media drive presents no such problems (1).

Booting Live with working and backup drives, System Monitor reveals all (2) and via Partition Editor i get (3) & (4).

It is here i begin to get lost.

The drive and partition sizes appear to be correct in (3) & (4), but why are the root and home partitions of different used capacities? Root from 2.1 GB to 2.6GB and home from 400MB to 3.8GB. All differences apparently residing in the lost+found!

Also the root and home partition sizes reported in (2) for the backup drive (dev/sdb5 & 6) are clearly wrong!, but the used amounts are very similar to the working drive.

Each partition backup file are uncompressed single files of 2.1GB(root) and 402.9MB(home) which is also consistently reflected on the working drive.

I'm getting very confused. Maybe i need to step back and just concentrate on getting a boot first. That would be a REAL plus.

Regards, Dave

---

### Post by unutbu on 2009-03-26
Hi David,
When you boot the LiveCD, do you have a working internet connection? If so, please boot from the LiveCD with both the working and backup drives connected. Follow [these instructions ]("http://ubuntuforums.org/showpost.php?p=6725571&postcount=3") to run the boot_info_script.
Posting the RESULTS.txt file will give us a clearer picture of what's going on. 

If you don't have a working connection while booted from the LiveCD, you can download the boot_info_script onto your working drive first, then reboot from the LiveCD (so both drives are recognized) and then run the boot_info_script.

Regarding the backup being invisible to the master drive:
> 
I have noticed that if i boot with my working drive as master and backup drive as slave, the backup drive does not appear under the Places dropwown, nor is it displayed in System Monitor/File Systems. It just doesn't appear to be there. Is this to be expected?

I am guessing that the UUIDs for the master and backup drives are identical. 
I am also guessing that your /etc/fstab specifies where to mount partitions based on their UUIDs. For example:
```

UUID=e8c543ef-c9c3-47f6-82bc-d35b5ff8f615 / ext3 relatime,errors=remount-ro 0 1  
```

If you have two partitions (one on the master and one on the backup) with the same UUID,
then /etc/fstab will only mount one of those partitions. 

If my guesses are correct, then this would explain why you do not see the backup drive while booted from the master drive. You do see both drives when booted from the LiveCD, because the LiveCD is probably mounting the partitions based on their device names /dev/sda5 and /dev/sdb5 rather than by their identical UUIDs.

> Connecting up working drive with the intermediate backup media drive presents no such problems (1).

What is the intermediate backup media drive? Sorry, I'm a bit confused by what you are saying here.

Finally, let's work on the filesystem size issues after we get the backup drive to boot.

---

### Post by David Brant on 2009-03-26
Hi unutbu

When booting the LiveCD, i have a live internet connection.

So booting from the LiveCD with both the working and backup drives connected, as per your instructions to run the boot_info_script, i enclose the RESULTS.txt file for diagnosis.  

```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

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
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 6448 MB, 6448619520 bytes
255 heads, 63 sectors/track, 784 cylinders, total 12594960 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xac454c41

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    12,594,959    12,594,897   5 Extended
/dev/sda5                 126     8,385,929     8,385,804  83 Linux
/dev/sda6           8,385,993    10,490,444     2,104,452  82 Linux swap / Solaris
/dev/sda7          10,490,508    12,594,959     2,104,452  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 10.1 GB, 10110320640 bytes
255 heads, 63 sectors/track, 1229 cylinders, total 19746720 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1637cc5a

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    19,743,884    19,743,822   5 Extended
/dev/sdb5                 126     9,430,154     9,430,029  83 Linux
/dev/sdb6           9,430,218    10,474,379     1,044,162  82 Linux swap / Solaris
/dev/sdb7          10,474,443    19,743,884     9,269,442  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda5: UUID="243d1c9f-d7e8-4c32-8560-557d0bb98b97" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="95187bcc-822a-4592-9182-9682ccc0dd37" TYPE="swap" 
/dev/sda7: UUID="b67e2f73-9f31-4e1d-b37c-258e505e98df" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: UUID="243d1c9f-d7e8-4c32-8560-557d0bb98b97" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb6: UUID="b05737a8-d725-4f2d-92c1-a1e7abb9e8ad" TYPE="swap" 
/dev/sdb7: UUID="b67e2f73-9f31-4e1d-b37c-258e505e98df" SEC_TYPE="ext2" TYPE="ext3" 
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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

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
# kopt=root=UUID=243d1c9f-d7e8-4c32-8560-557d0bb98b97 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=243d1c9f-d7e8-4c32-8560-557d0bb98b97

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
uuid		243d1c9f-d7e8-4c32-8560-557d0bb98b97
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=243d1c9f-d7e8-4c32-8560-557d0bb98b97 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		243d1c9f-d7e8-4c32-8560-557d0bb98b97
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=243d1c9f-d7e8-4c32-8560-557d0bb98b97 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		243d1c9f-d7e8-4c32-8560-557d0bb98b97
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=243d1c9f-d7e8-4c32-8560-557d0bb98b97 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=b67e2f73-9f31-4e1d-b37c-258e505e98df /home           ext3    relatime        0       2
# /dev/sda6
UUID=95187bcc-822a-4592-9182-9682ccc0dd37 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


   1.0GB: boot/grub/menu.lst
    .9GB: boot/grub/stage2
    .9GB: boot/initrd.img-2.6.27-7-generic
   1.0GB: boot/vmlinuz-2.6.27-7-generic
    .9GB: initrd.img
   1.0GB: vmlinuz

=========================== sdb5/boot/grub/menu.lst: ===========================

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
hiddenmenu

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
# kopt=root=UUID=243d1c9f-d7e8-4c32-8560-557d0bb98b97 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=243d1c9f-d7e8-4c32-8560-557d0bb98b97

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

title Ubuntu 8.10, Test #1
uuid 243d1c9f-d7e8-4c32-8560-557d0bb98b97
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=243d1c9f-d7e8-4c32-8560-557d0bb98b97 ro quiet splash
initrd /boot/initrd.img-2.6.27-7-generic
quiet

title Ubuntu 8.10, Test #2
root (hd0,4)
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=243d1c9f-d7e8-4c32-8560-557d0bb98b97 ro quiet splash
initrd /boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, memtest86+
uuid		243d1c9f-d7e8-4c32-8560-557d0bb98b97
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=243d1c9f-d7e8-4c32-8560-557d0bb98b97 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=b67e2f73-9f31-4e1d-b37c-258e505e98df /home           ext3    relatime        0       2
# /dev/sda6
UUID=95187bcc-822a-4592-9182-9682ccc0dd37 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


   1.0GB: boot/grub/menu.lst
    .9GB: boot/grub/stage2
    .9GB: boot/initrd.img-2.6.27-7-generic
   1.0GB: boot/vmlinuz-2.6.27-7-generic
    .9GB: initrd.img
   1.0GB: vmlinuz

```

Regarding my invisible backup drive from the UUIDs. I checked each drive while under live boot. Both menu.lst files display the same identifiers. These are also identical to those displayed in each /etc/fstab file. Home and swap partitions are both different, but identical for each drive. Your suggestion sounds very convincing to me! 

To answer your penultimate point:

The 'intermediate backup media drive' is an old IDE slave drive, with a suitable empty partition formatted ext3, i had to hand. It was purely for intremediate storage for the backup data files, prior to their restoration. Now I have my ntfs USB stick handy, i have copied the backup files to that for convenience. It was a needless reference which confuses things and i will drop reference to it.

and your final point:

I agree, lets get the thing booting first for the big plus.

Best regards

---

### Post by unutbu on 2009-03-26
Note these lines at the top of the RESULTS.txt file:
```

 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
```

This indicates that when booting sdb, the backup drive, GRUB is looking in /dev/sdb1 for the stage2 and menu.lst boot files. GRUB is looking in the wrong partition, since these files are in /dev/sdb5. 

Here is how you can correct that:

Option #1:
With only the backup drive connected, boot from the LiveCD.
Open a terminal and type
```

sudo grub
root (hd0,4)
setup (hd0)
quit
```

Option #2:
With both the working and backup drives connected, boot from the LiveCD.
Open a terminal and type
```

sudo grub
root (hd1,4)
setup (hd1)
quit

```

Both options try to do the same thing: they install GRUB to the MBR on sdb and tell it to look in /dev/sdb5 for the stage2 and menu.lst files.

I think that this is all that was preventing you from booting.
Let us know how it goes.

---

### Post by rishg on 2009-03-27
I had a similar problem when I re-installed Windows XP and lost the GRUB. 

Here are the sequence of events as they unfolded. 

1. To reinstall grub, I booted via LiveCD 

2.Got to the grub shell set the root to point Grub to the appropriate partition.  

These were the commands I entered : 
sudo grub
root **(hd0,5)**
setup (hd0)
quit

3. So far so good. On restarting the laptop and selecting Ubuntu on the grub menu, I got the dreaded Error 17 message.

4. On the grub menu, I hit 'e' on the Ubuntu option and looked up which partition Ubuntu was pointing to. I noticed that it was pointing to (hd0,8) although I had set it root to (hd0,5) via LiveCD!!  I manually changed it to (hd0,5) and voila, ubuntu booted. Note that this change is not permanent. 

5. To make this change permanent, once you are booted up, open a terminal and type 

gksudo gedit /boot/grub/menu.lst 

6. Change the root partition to your actual partition. In my case, I changed it to (hd0,5).  The changes were permanent now. 
Hope this works for you too. 

Its a simple fix actually. The chances that yor grub menu is pointing to a different file system are pretty high. So first check the partition towards which Ubuntu on your Grub menu is pointing. It may be just the fix you need. 

Hope this helps.

---

### Post by David Brant on 2009-03-27
Hi unutbu

It works. It really works!!!
What an incredible relief that is.
I'm actually up and running on the backup drive. :)

Re-booted a few times since and the changes seam to have been remembered.

Just one little point though. I notice during each new boot sequence, several scripts run beforehand beginning with 'reading files needed to boot'. I guess this is to get things as they should be according to the new boot partition specifications. Is there a way to make things 'more permenant' and less visible (for want of a better term)? ie, not requiring to run the additional scripts as in the case of the original working drive, Perhaps as 'rishg' suggests. If so, could you recommend the necessary edits to my now re-instated original menu.lst included below.

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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

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
# kopt=root=UUID=243d1c9f-d7e8-4c32-8560-557d0bb98b97 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=243d1c9f-d7e8-4c32-8560-557d0bb98b97

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
uuid		243d1c9f-d7e8-4c32-8560-557d0bb98b97
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=243d1c9f-d7e8-4c32-8560-557d0bb98b97 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		243d1c9f-d7e8-4c32-8560-557d0bb98b97
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=243d1c9f-d7e8-4c32-8560-557d0bb98b97 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		243d1c9f-d7e8-4c32-8560-557d0bb98b97
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

This now only leaves file system size discrepancy issues reported between System Monitor/File Systems and Patrtion Manager/GParted to be resolved and i am home and dry.

Should i start another thread on this aspect?

---

### Post by unutbu on 2009-03-27
Hi David, so glad to hear the backup drive is now bootable!

I'm not 100% sure I know why you are not getting the splash screen, but I have a guess. 
I recall a thread where a person's boot lacked the "cylon" bar because the
UUID in /etc/initramfs-tools/conf.d/resume didn't match his swap partition's UUID.

If I'm right, it's easy to fix:

While booted from the backup drive, open a terminal. Type
```

sudo vol_id /dev/sdb6
```

You will see a line that says something like
```

ID_FS_UUID=**b05737a8-d725-4f2d-92c1-a1e7abb9e8ad**
```

Next type
```

gksu gedit /etc/initramfs-tools/conf.d/resume
```

You should see
```

RESUME=UUID=**b05737a8-d725-4f2d-92c1-a1e7abb9e8ad**
```

Whatever UUID you see after the "sudo vol_id /dev/sdb6" command should match
the UUID you see in /etc/initramfs-tools/conf.d/resume.

I hope this works for you, if not, I'm afraid I don't have the answer.

---

### Post by David Brant on 2009-03-27
Hi unutbu

The UUIDs were different, so i changed them, but no effect. It's no big deal though, the scripts only temporarily pop up towards the end of the oscillating ubuntu progress bar before the final splash screen.

The boot is the thing :)

Finally, any ideas about the file system size discrepancy? My only real concern is what do i use for future reference. I'm happy with the quality of the backup, it's just the reported quantities which appear so ambiguous between System Monitor/File Systems and Partition Manager/GParted.

---

### Post by unutbu on 2009-03-27
```
             System Monitor                    GParted
          ---------------------------    ---------------------
	  total	  free  avail  used   	 total  unused 	 used   
sda5	  3.9	  1.9   1.7    2.0    	 4.0	1.9    	 2.1    
sdb5	  3.9	  1.9	1.7    2.0       4.5	1.9    	 2.6    
sda7	  1011.4  624.8 573.4  386.6	 1.0	624.79 	 402.78 
sdb7	  1011.4  624.9 573.6  386.5	 4.42	624.93 	 3.81   

```

**Regarding why there is a apparent discrepancy between System Monitor numbers and GParted numbers:**

System Monitor>File Systems reports the size of your filesystems.
GParted reports the sizes of your partitions.

The filesystem sits inside the partition, sort of like a filing cabinet inside of a room, except that the filing cabinet practically fills the room.

Every filesystem (such as ext3) has a scheme for remembering its directory structure and where files are physically located in the partition. That scheme requires some hard drive space to store, but is not counted as part of the filesystem itself. This accounts for the discrepancy between "used" sizes reported by GParted versus System Monitor. The amount of "used" space as reported by GParted will always be greater than the amount of "used" space reported by System Monitor.[B]

Regarding the "clearly wrong" filesystem sizes on sdb5 and sdb7:
[/B]
Notice that your sdb5 has a filesystem with total size 3.9 GiB, but GParted says
the total partitions size is 4.5. The reason why this happened is because 
your backup program, PartImage, literally made a backup of your sda5 filesystem which was then placed in sdb5. sda5 has a filesystem of size 3.9 GiB, so you get a filesystem of size 3.9 GiB in sdb5 too. Its like having a small filing cabinet in a large room.

To fix this problem, open a terminal and type
```

sudo resize2fs /dev/sdb5
sudo resize2fs /dev/sdb7

```
After doing this, System Monitor should report the total filesystem size of sdb5 has increased to around 4.4 GiB, and the total filesystem size of sdb7 should increase to around 4.3 GiB.

---

### Post by David Brant on 2009-03-28
Even though i am still very much a novice, i have to say that is the most focussed and understandable explanation of a complex subject i have come across in a very long time. My hearty congratulations go to you.

I was having a real problem, perhaps not so much so with partitions but definitely with the concept of filesystems. If my limited understanding is now correct, there is little direct correlation between the practical data size held within an oversized filesystem (after a backup in this case).

My initial concern was that the filesystem appeared to have increased disproportionately in relation to the data size i had actually backed up. But in reality i am only backing up several books within a resized filing cabinet, and there is plenty of room left within the cabinet before it begins to increase it's size to the limit of the room size.

Having done your recommended resizing i have to say that the 400MB of data that now resides in a 4GB filesystem in a similarly sized home partition now looks much more pleasing to my eye. :)

Many thanks for your patience, diligence and kindness. You are a real asset and credit to the forums and i am very much indebted to you.

---

### Post by unutbu on 2009-03-28
David, I'm very happy I could help.
I agree with you that ubuntuforums is a wonderful resource -- I learn a lot from others here too. 
> 
there is little direct correlation between the practical data size held within an oversized filesystem

Yes. The total filesystem size is a measure of the maximum capacity of the "filing cabinet", not the amount used by files so far.

By the way, if I understand your setup correctly, the backup drive is invisible to the working drive and vice versa (due to the matching UUIDs). Would you like to make them visible to each other?

---

### Post by David Brant on 2009-03-28
Yes indeed, you understand my setup correctly. It was achieved through a skillful combination of default, luck and accident :)

Mutual drive visibility would be a very useful feature to have for verification checking purposes following future backups.

---

### Post by unutbu on 2009-03-28
First a little warning: If you plan on using Partimage to clone sda5 onto sdb5 again, then 
the "resize2fs" commands would have to be redone. That's not so hard. But the changes below would have to be redone as well. You may not want to go through the steps below if you plan on cloning frequently.

On the other hand, if you are okay with letting sda5 and sdb5 diverge, then the instructions below may worth doing so you can mount the backup drive's partitions while booted from the working drive.

Boot the backup drive.

First, change the UUID on sdb5 and sdb7:
```

sudo tune2fs -U random /dev/sdb5
sudo tune2fs -U random /dev/sdb7
```

To find out the new UUIDs assigned to sdb5 and sdb7, run
```

blkid -c /dev/null
```

Now edit /boot/grub/menu.lst

```
gksu gedit /boot/grub/menu.lst
```

Do a find-and-replace, changing 
```

243d1c9f-d7e8-4c32-8560-557d0bb98b97 --> the new UUID for sdb5
b67e2f73-9f31-4e1d-b37c-258e505e98df --> the new UUID for sdb7

```
If you select text in the terminal with your mouse, you can paste the text into gedit by clicking your middle mouse button. If you have a 2-button mouse, try clicking the two buttons simultaneously.

Save menu.lst. Next open /etc/fstab

Again do the same find-and-replace. Also, replace

```
95187bcc-822a-4592-9182-9682ccc0dd37 --> b05737a8-d725-4f2d-92c1-a1e7abb9e8ad
```
The UUID on the left is the UUID for sda6 (the working drive's swap). The UUID on the right is the UUID for sdb6 (the backup drive's swap).

Your backup drive was using your working drive's swap partition. There is nothing wrong with that when you have both drives plugged in -- in fact it could help performance to have swap on a different drive since two (drive) heads are better than one. But if you don't have the working drive plugged in while running off the backup, you would have no swap at all.

Save and exit.

Shutdown. Plug both the working and backup drives in and try to boot the backup drive.

If the above instructions are successful, the working drive's / and /home dirs will automatically get mounted in /media and with icons on your desktop.

Conversely, booting the working drive should result in the backup drive's / and /home getting mounted in /media and with icons on your desktop.

---

### Post by David Brant on 2009-04-06
My apologies for the delay in getting back to thank you for your valued help. I will keep the contents of this posting for future reference. Time will tell how often i need to backup, or indeed come up against related boot problems, but it is reassuring to have good set of working options to fall back on. Speaking as a newbie, i am already finding Ubuntu a very good OS, and have been inspired by your efforts.

Best regards, Dave   :)

---

### Post by unutbu on 2009-04-06
No problem; Enjoy Ubuntu!

---

