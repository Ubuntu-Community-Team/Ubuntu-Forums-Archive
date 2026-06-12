---
title: "Another Dual Boot Problem"
date: 2009-05-17
forum: Installation &amp; Upgrades
---

### Post by cignus on 2009-05-17
Sorry If this is a little long-winded, I'm trying to be as detailed as possible.

After trying with limited success to get wine to work with the few games I have, I finally broke down and decided to dual boot with XP.  I read through all the options for dual booting on the Ubuntu community pages, to see what the different options were, and since I was still using 8.10 I decided to just backup all my data, then install XP first followed by Ubuntu 9.04 so I wouldn't have to worry about XP overwritting grub.  

Here is the whole process I followed:

First, my original 8.10 installation looked like this:
100MB /boot
4GB swap
100GB /
400GB /home

When I tried to install XP, I couldn't get the installer to work.  A quick search revealed that sometimes the installer will crash if the first partition on a drive is anything but FAT32.  So I reformatted my 100MB boot partition as FAT32, and was able to successfully install XP after that, and boot up with no problems.

Here's the catch (And I think the source of the problem I'm having now) - when I installed XP, I made a new 100GB partition at the end of my drive, so XP would be forced to use the slowest drive cylinders.

After installing XP my drive looked like this:
100MB FAT32 boot partition
300GB empty
100GB FAT32 Windows XP

I then reformatted the 100MB FAT32 partion back to ext2 /boot, and installed Ubuntu 9.04, and was able to boot into it.

When I rebooted though, the I noticed that GRUB did not list XP as one of my OS choices even though I thought it was supposed to detect it automatically.  I copied the example from menu.lst and got XP to show up, but when I try to boot I get a message that the partition is not bootable and I should insert a boot floppy.  That's when I came here and started looking through all the dual boot threads, but to no avail.

I've included my results of boot_info_script032.sh below.

A few Issues I've noticed about it are:
- sda3 is marked as my boot partition, when I formatted sda1 as /boot
- sda 1 is listed as XP FAT32 boot sector, but the file system is ext2.  There are also no other details for it
- if I fdisk -l I get a message that "Partition table entries are not in disk order."

```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /grub/stage2 and /grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda3 starts 
                       at sector 63. But according to the info from fdisk, 
                       sda3 starts at sector 771971445.
    Operating System:  Windows XP
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000da27f

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       192,779       192,717  83 Linux
/dev/sda2             192,780     8,193,149     8,000,370  82 Linux swap / Solaris
/dev/sda3    *    771,971,445   976,768,064   204,796,620   b W95 FAT32
/dev/sda4           8,193,150   771,971,444   763,778,295   5 Extended
/dev/sda5           8,193,213   203,511,419   195,318,207  83 Linux
/dev/sda6         203,511,483   771,971,444   568,459,962  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="a0c8e58e-8815-421a-9a9b-d323e730cd19" TYPE="ext2" 
/dev/sda2: UUID="a430c045-d875-4663-88f7-62b0bc2a8c36" TYPE="swap" 
/dev/sda3: UUID="4A0E-E8BE" TYPE="vfat" 
/dev/sda5: UUID="7ea9bd82-c1ac-41d2-b9a3-1e9e4f3d242b" TYPE="ext4" 
/dev/sda6: UUID="7ce68921-5288-4fa5-bdd6-23411d3893d0" TYPE="ext4" 

=============================== "mount" output: ===============================

/dev/sda5 on / type ext4 (rw,relatime,errors=remount-ro)
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
/dev/sda1 on /boot type ext2 (rw,relatime)
/dev/sda6 on /home type ext4 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/peter/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=peter)
/dev/sda3 on /home/peter/test type vfat (rw)


============================= sda1/grub/menu.lst: =============================

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
timeout        4

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
# kopt=root=UUID=7ea9bd82-c1ac-41d2-b9a3-1e9e4f3d242b ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=a0c8e58e-8815-421a-9a9b-d323e730cd19

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
uuid        a0c8e58e-8815-421a-9a9b-d323e730cd19
kernel        /vmlinuz-2.6.28-11-generic root=UUID=7ea9bd82-c1ac-41d2-b9a3-1e9e4f3d242b ro quiet splash 
initrd        /initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        a0c8e58e-8815-421a-9a9b-d323e730cd19
kernel        /vmlinuz-2.6.28-11-generic root=UUID=7ea9bd82-c1ac-41d2-b9a3-1e9e4f3d242b ro  single
initrd        /initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        a0c8e58e-8815-421a-9a9b-d323e730cd19
kernel        /memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

## ## Windows Options ##

 title        Windows XP
 root        (hd0,2)
 makeactive
 chainloader    +1

### END WINDOWS

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: grub/menu.lst
    .0GB: grub/stage2
    .0GB: initrd.img-2.6.28-11-generic
    .0GB: vmlinuz-2.6.28-11-generic

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
timeout        4

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
# kopt=root=UUID=7ea9bd82-c1ac-41d2-b9a3-1e9e4f3d242b ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=a0c8e58e-8815-421a-9a9b-d323e730cd19

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
uuid        a0c8e58e-8815-421a-9a9b-d323e730cd19
kernel        /vmlinuz-2.6.28-11-generic root=UUID=7ea9bd82-c1ac-41d2-b9a3-1e9e4f3d242b ro quiet splash 
initrd        /initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        a0c8e58e-8815-421a-9a9b-d323e730cd19
kernel        /vmlinuz-2.6.28-11-generic root=UUID=7ea9bd82-c1ac-41d2-b9a3-1e9e4f3d242b ro  single
initrd        /initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        a0c8e58e-8815-421a-9a9b-d323e730cd19
kernel        /memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

## ## Windows Options ##

 title        Windows XP
 root        (hd0,2)
 makeactive
 chainloader    +1

### END WINDOWS

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
UUID=7ea9bd82-c1ac-41d2-b9a3-1e9e4f3d242b /               ext4    relatime,errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=a0c8e58e-8815-421a-9a9b-d323e730cd19 /boot           ext2    relatime        0       2
# /home was on /dev/sda6 during installation
UUID=7ce68921-5288-4fa5-bdd6-23411d3893d0 /home           ext4    relatime        0       2
# swap was on /dev/sda2 during installation
UUID=a430c045-d875-4663-88f7-62b0bc2a8c36 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


   4.2GB: boot/grub/menu.lst
   4.2GB: boot/grub/stage2
   4.2GB: boot/initrd.img-2.6.28-11-generic
   4.2GB: boot/vmlinuz-2.6.28-11-generic
   4.2GB: initrd.img
   4.2GB: vmlinuz
```

---

