---
title: "Windows 7 dual boot issues"
date: 2009-09-25
forum: Installation &amp; Upgrades
---

### Post by whitechinaman on 2009-09-25
So I've searched these forums and google and cant seem to find anyone who has the same setup as mine with the same problem I'm having, so I'm hoping someone can help me out. I'm attempting to setup a dual boot scenario with Kubuntu 9.04 and Windows 7 RC. I had Kubuntu installed first, then installed 7, managed to restore grub, but now I cant for the life of me add Windows 7 to the menu.lst so that I can choose it at boot time. I've tried every different combination of hard drive numbers (hd0,0 hd0,1 etc), and tried placing the stanza in various places inside the menu.lst file, but it will never show in the grub menu at boot. Per a previous post, I downloaded the boot_info_script, and here is the result file:

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /grub/stage2 and /grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /etc/fstab

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x55ca70e7

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63     1,975,994     1,975,932  83 Linux
/dev/sda2    *      1,975,995    80,116,154    78,140,160   7 HPFS/NTFS
/dev/sda3          80,116,155   394,668,854   314,552,700   5 Extended
/dev/sda5          80,116,218   289,844,729   209,728,512  83 Linux
/dev/sda6         289,844,793   352,771,334    62,926,542  83 Linux
/dev/sda7         352,771,398   365,366,294    12,594,897  82 Linux swap / Solaris
/dev/sda8         365,366,358   375,133,814     9,767,457  83 Linux
/dev/sda9         375,133,878   394,668,854    19,534,977  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="c1c4ae2a-8307-472b-b6ef-8b4b37f15118" TYPE="ext2" 
/dev/sda2: UUID="7E94527F945239BB" TYPE="ntfs" 
/dev/sda5: UUID="602ea8bd-19ce-48c6-9a36-da0ec0fa3179" TYPE="ext4" 
/dev/sda6: UUID="0877f550-a609-49e4-ad6d-e1ab639072d5" TYPE="ext4" 
/dev/sda7: UUID="f53217de-451e-40a8-ac39-0314998b4f88" TYPE="swap" 
/dev/sda8: UUID="a2103c4c-b0f4-4e04-973e-c3fd11645e62" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda9: UUID="295ed5c5-6983-4884-8608-382171ff1d9e" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/sda9 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-15-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)


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
timeout        10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=UUID=295ed5c5-6983-4884-8608-382171ff1d9e ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=295ed5c5-6983-4884-8608-382171ff1d9e

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
uuid        295ed5c5-6983-4884-8608-382171ff1d9e
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=295ed5c5-6983-4884-8608-382171ff1d9e ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

#title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
#uuid        295ed5c5-6983-4884-8608-382171ff1d9e
#kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=295ed5c5-6983-4884-8608-382171ff1d9e ro  single
#initrd        /boot/initrd.img-2.6.28-15-generic

#title        Ubuntu 9.04, kernel 2.6.28-11-generic
#uuid        295ed5c5-6983-4884-8608-382171ff1d9e
#kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=295ed5c5-6983-4884-8608-382171ff1d9e ro quiet splash 
#initrd        /boot/initrd.img-2.6.28-11-generic
#quiet

#title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
#uuid        295ed5c5-6983-4884-8608-382171ff1d9e
#kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=295ed5c5-6983-4884-8608-382171ff1d9e ro  single
#initrd        /boot/initrd.img-2.6.28-11-generic

#title        Ubuntu 9.04, memtest86+
#uuid        295ed5c5-6983-4884-8608-382171ff1d9e
#kernel        /boot/memtest86+.bin
#quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=================== sda1: Location of files loaded by Grub: ===================


    .9GB: boot/grub/stage2
    .8GB: grub/menu.lst
    .8GB: grub/stage2
    .0GB: initrd.img-2.6.28-11-generic
    .0GB: vmlinuz-2.6.28-11-generic

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=0877f550-a609-49e4-ad6d-e1ab639072d5 /               ext4    relatime,errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=c1c4ae2a-8307-472b-b6ef-8b4b37f15118 /boot           ext2    relatime        0       2
# /home was on /dev/sda5 during installation
UUID=602ea8bd-19ce-48c6-9a36-da0ec0fa3179 /home           ext4    relatime        0       2
# swap was on /dev/sda7 during installation
UUID=f53217de-451e-40a8-ac39-0314998b4f88 none            swap    sw              0       0

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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=UUID=295ed5c5-6983-4884-8608-382171ff1d9e ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=295ed5c5-6983-4884-8608-382171ff1d9e

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
uuid        295ed5c5-6983-4884-8608-382171ff1d9e
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=295ed5c5-6983-4884-8608-382171ff1d9e ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title Windows 7 (loader)
root (hd0,1)
savedefault
makeactive
chainloader +1

#title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
#uuid        295ed5c5-6983-4884-8608-382171ff1d9e
#kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=295ed5c5-6983-4884-8608-382171ff1d9e ro  single
#initrd        /boot/initrd.img-2.6.28-15-generic

#title        Ubuntu 9.04, kernel 2.6.28-11-generic
#uuid        295ed5c5-6983-4884-8608-382171ff1d9e
#kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=295ed5c5-6983-4884-8608-382171ff1d9e ro quiet splash 
#initrd        /boot/initrd.img-2.6.28-11-generic
#quiet

#title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
#uuid        295ed5c5-6983-4884-8608-382171ff1d9e
#kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=295ed5c5-6983-4884-8608-382171ff1d9e ro  single
#initrd        /boot/initrd.img-2.6.28-11-generic

#title        Ubuntu 9.04, memtest86+
#uuid        295ed5c5-6983-4884-8608-382171ff1d9e
#kernel        /boot/memtest86+.bin
#quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


=============================== sda9/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda9 during installation
UUID=295ed5c5-6983-4884-8608-382171ff1d9e /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=f53217de-451e-40a8-ac39-0314998b4f88 none            swap    sw              0       0

=================== sda9: Location of files loaded by Grub: ===================


 200.2GB: boot/grub/menu.lst
 200.2GB: boot/grub/stage2
 199.3GB: boot/initrd.img-2.6.28-11-generic
 199.4GB: boot/initrd.img-2.6.28-15-generic
 199.3GB: boot/vmlinuz-2.6.28-11-generic
 199.2GB: boot/vmlinuz-2.6.28-15-generic
 199.4GB: initrd.img
 199.3GB: initrd.img.old
 199.2GB: vmlinuz
 199.3GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb 


Any help would be much appreciated. Thanks in advance.

(btw, not sure how to turn off the html, so where you see the smiley with shades is a 8 inside parenthesis)

---

### Post by arrange on 2009-09-25
> **whitechinaman said:**
> 
 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /grub/stage2 and /grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst
......
(btw, not sure how to turn off the html, so where you see the smiley with shades is a 8 inside parenthesis)ad 2) Use CODE tags (see the # icon above the Message textarea)

ad 1) The problem is that you've set up Grub to use the *menu.lst* from *sda1*, but you've been editing the *sda9*'s *menu.lst*. So -

**either** use *sda1* as a [dedicated boot partition]("http://members.iinet.net/~herman546/p15.html#How_to_make_a_separate_Grub_Partition_") (I'm using it and it's great for a multi-boot setup, but could be tricky for a beginner);
**or** restore *Grub*, using ```
root (hd0,8)
``` instead of *(hd0,0)*.

But before doing any changes I would simply try [booting directly from Grub command line]("http://members.iinet.net/~herman546/p15.html#First_method:_direct_kernel_boot."), which is not very different from editing a *menu.lst* file.

---

### Post by spandon on 2009-09-25
Hi whitechinaman,
Dual/triple/Quad boot systems with Windows and Ubuntu/Kubuntu are quite simple to setup.
I use the following to achieve this:-
Plan the type of system I want to end up with.
partition & format the hard drive i.e.
A partition is required for each flavour of Windows (size and format depends on which you are installing).then at least 1 partition for data.
Once this has been done, then you require a partition for Ubuntu/Kubuntu (ext3) and a swap partition (swap).
Now install Windows FIRST (in the following order if installing more than one flavour XP, Vista, W7, the oldest OS first), once this system is working OK then you can go on to install Ubuntu/Kubuntu.
When installing Ubuntu from the LIVE Session, choose the MANUAL partition method from the menu and edit the ext3 that you made earlier to install Ubuntu/Kubuntu to, Grub will automatically install itself as a dual boot system.
As an example, if I had a 160gb drive and wanted to install W7 and ubuntu as a dual boot system I would do it this way:-
Partition and format the drive
50 NTFS W7
49 NTFS Data 1
49 NTFS Data 2
10 Ext3 Ubuntu
2  Linux Swap
Install Windows 7 (I am running numerous machines multi booting with W7 (RC) & Ubuntu with NO problems being experienced)
Once W7 is running to your satisfaction, then install Ubuntu/Kubuntu as explained above - you should now have a dual boot system.
The time it takes me to do this is around 2 hours including the updates via the internet (ADSL).
I find the partitioner on the Live cd, quite adequate (Sys-Admin-Partition Editor).
Also, I find with multi boot systems with ubuntu, installing Startup-Manager in Ubuntu, as it gives a colourful and manageble menu at startup/Restart of the system.
**If you already have a system with Windows installed and are happy with it, then all you need do, is to shrink the last patition by 12 gb and create and format the 2 patitions required to install Ubuntu/Kubuntu and swap**
Hope this helps you and anyone else wishing to setup a multi boot system?
Don

---

### Post by whitechinaman on 2009-09-25
I ran grub and put in root (hd0,8) and that works perfect. I'd like to think that I understand a good deal about Linux in general (I've been on Debian for the last 4 years or so), but grub has always confused me. I thought that it needed to point at the /boot partition, not the / partition. You learn something new every day, right? Thanks, Arrange, you rock!

---

