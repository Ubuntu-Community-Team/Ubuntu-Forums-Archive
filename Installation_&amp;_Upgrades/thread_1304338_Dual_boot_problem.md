---
title: "Dual boot problem"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by nandyboy on 2009-10-29
Hello frenz.......I am new to Ubuntu and want your help in coming out of a problem. I had installed Oracle Enterprise Linux previously. Now I have installed Ubuntu in the free space of harddisk. But now, while booting, my system is not showing Oracle Enterprise Linux. I have googled but unable to resolve. I can figure out that MBR might have been overwritten. But not sure about it.....Please tell me how to make both OSs visible during booting.....

Thanx in advance
Nand

---

### Post by presence1960 on 2009-10-29
> **nandyboy said:**
> Hello frenz.......I am new to Ubuntu and want your help in coming out of a problem. I had installed Oracle Enterprise Linux previously. Now I have installed Ubuntu in the free space of harddisk. But now, while booting, my system is not showing Oracle Enterprise Linux. I have googled but unable to resolve. I can figure out that MBR might have been overwritten. But not sure about it.....Please tell me how to make both OSs visible during booting.....

Thanx in advance
Nand

Let's get a better look at your setup & boot process. Boot into Ubuntu. Come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by nandyboy on 2009-10-29
Thank you for the reply Presence1960.....Please see below...I have pasted the information from RESULTS.txt

```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #9 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst /grub/grub.conf

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
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Enterprise Linux Enterprise 
                       Linux Server release 5.1 (Carthage) Kernel on an
    Boot files/dirs:   /etc/fstab

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda9: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda10: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0009ffcd

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63       514,079       514,017  83 Linux
/dev/sda2             514,080    82,429,514    81,915,435  83 Linux
/dev/sda3          82,429,515    84,309,119     1,879,605  83 Linux
/dev/sda4         124,375,230   312,576,704   188,201,475   5 Extended
/dev/sda5         124,375,293   165,340,979    40,965,687  83 Linux
/dev/sda6         165,341,043   186,305,804    20,964,762  83 Linux
/dev/sda7         186,305,868   198,595,529    12,289,662  82 Linux swap / Solaris
/dev/sda8         198,595,593   218,596,454    20,000,862  83 Linux
/dev/sda9         218,596,518   308,640,779    90,044,262  83 Linux
/dev/sda10        308,640,843   312,576,704     3,935,862  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: LABEL="/boot" UUID="03f65779-26d7-4bc5-b814-042d2acf1bd2" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda2: LABEL="/u01" UUID="bb090aa3-aacd-4df8-9ad1-6610af9bd27b" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda3: LABEL="/var" UUID="555022c0-b0f4-402b-b3a6-7982ba1bc54a" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: LABEL="/" UUID="81d75afc-dc60-426f-af46-8d75c45f8f8a" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: LABEL="/tmp" UUID="687ce0e2-3b5c-46cb-ab31-08979407268b" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: TYPE="swap" UUID="864321ec-38c8-4724-bc94-314721f12f9c" 
/dev/sda8: UUID="38774ea2-3f76-4b37-add1-014e85c9afd2" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda9: UUID="a8149b4a-0896-4948-919b-9ba103904502" TYPE="ext3" 
/dev/sda10: TYPE="swap" UUID="9c9888fc-00e9-42d5-a45c-b349ff9f81c9" 

=============================== "mount" output: ===============================

/dev/sda9 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/nand/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=nand)


============================= sda1/grub/grub.conf: =============================

# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /boot/, eg.
#          root (hd0,0)
#          kernel /vmlinuz-version ro root=/dev/sda5
#          initrd /initrd-version.img
#boot=/dev/sda
default=3
timeout=5
splashimage=(hd0,0)/grub/splash.xpm.gz
hiddenmenu
title Enterprise Linux (2.6.18-53.el5PAE)
    root (hd0,0)
    kernel /vmlinuz-2.6.18-53.el5PAE ro root=LABEL=/ rhgb quiet
    initrd /initrd-2.6.18-53.el5PAE.img
title Enterprise Linux-xen (2.6.18-53.el5xen)
    root (hd0,0)
    kernel /xen.gz-2.6.18-53.el5
    module /vmlinuz-2.6.18-53.el5xen ro root=LABEL=/ rhgb quiet
    module /initrd-2.6.18-53.el5xen.img
title Enterprise Linux-base (2.6.18-53.el5)
    root (hd0,0)
    kernel /vmlinuz-2.6.18-53.el5 ro root=LABEL=/ rhgb quiet
    initrd /initrd-2.6.18-53.el5.img
title Ubuntu
    rootnoverify (hd0,9)
    chainloader +1

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: grub/grub.conf
    .0GB: grub/menu.lst
    .0GB: grub/stage2
    .0GB: initrd-2.6.18-53.el5debug.img
    .0GB: initrd-2.6.18-53.el5.img
    .0GB: initrd-2.6.18-53.el5PAE.img
    .0GB: initrd-2.6.18-53.el5xen.img
    .0GB: vmlinuz-2.6.18-53.el5
    .0GB: vmlinuz-2.6.18-53.el5debug
    .0GB: vmlinuz-2.6.18-53.el5PAE
    .0GB: vmlinuz-2.6.18-53.el5xen

=============================== sda5/etc/fstab: ===============================

LABEL=/                 /                       ext3    defaults        1 1
LABEL=/tmp              /tmp                    ext3    defaults        1 2
LABEL=/var              /var                    ext3    defaults        1 2
LABEL=/u01              /u01                    ext3    defaults        1 2
LABEL=/boot             /boot                   ext3    defaults        1 2
tmpfs                   /dev/shm                tmpfs   defaults        0 0
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
sysfs                   /sys                    sysfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0

=========================== sda8/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=38774ea2-3f76-4b37-add1-014e85c9afd2 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,7)

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

title        Oracle Enterprise Linux 5.1
configfile    (hd0,0) /etc/grub.conf

title        Ubuntu 8.04, kernel 2.6.24-16-generic
root        (hd0,7)
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=38774ea2-3f76-4b37-add1-014e85c9afd2 ro quiet splash
initrd        /boot/initrd.img-2.6.24-16-generic
quiet

title        Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root        (hd0,7)
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=38774ea2-3f76-4b37-add1-014e85c9afd2 ro single
initrd        /boot/initrd.img-2.6.24-16-generic

title        Ubuntu 8.04, memtest86+
root        (hd0,7)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda8/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda8
UUID=38774ea2-3f76-4b37-add1-014e85c9afd2 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=864321ec-38c8-4724-bc94-314721f12f9c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda8: Location of files loaded by Grub: ===================


 106.8GB: boot/grub/menu.lst
 106.8GB: boot/grub/stage2
 106.8GB: boot/initrd.img-2.6.24-16-generic
 106.8GB: boot/initrd.img-2.6.24-16-generic.bak
 106.8GB: boot/vmlinuz-2.6.24-16-generic
 106.8GB: initrd.img
 106.8GB: vmlinuz

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
# kopt=root=UUID=a8149b4a-0896-4948-919b-9ba103904502 ro

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
title        Oracle Enterprise Linux 5.1
configfile    (hd0,1)/grub/grub.conf

title        Ubuntu 8.04, kernel 2.6.24-16-generic
root        (hd0,8)
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=a8149b4a-0896-4948-919b-9ba103904502 ro quiet splash
initrd        /boot/initrd.img-2.6.24-16-generic
quiet

title        Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root        (hd0,8)
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=a8149b4a-0896-4948-919b-9ba103904502 ro single
initrd        /boot/initrd.img-2.6.24-16-generic

title        Ubuntu 8.04, memtest86+
root        (hd0,8)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda8.
title        Ubuntu 8.04, kernel 2.6.24-16-generic (on /dev/sda8)
root        (hd0,7)
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=38774ea2-3f76-4b37-add1-014e85c9afd2 ro quiet splash 
initrd        /boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda8.
title        Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode) (on /dev/sda8)
root        (hd0,7)
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=38774ea2-3f76-4b37-add1-014e85c9afd2 ro single 
initrd        /boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda8.
title        Ubuntu 8.04, memtest86+ (on /dev/sda8)
root        (hd0,7)
kernel        /boot/memtest86+.bin  
savedefault
boot


=============================== sda9/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda9
UUID=a8149b4a-0896-4948-919b-9ba103904502 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda10
UUID=9c9888fc-00e9-42d5-a45c-b349ff9f81c9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda9: Location of files loaded by Grub: ===================


 132.3GB: boot/grub/menu.lst
 132.4GB: boot/grub/stage2
 132.4GB: boot/initrd.img-2.6.24-16-generic
 132.3GB: boot/initrd.img-2.6.24-16-generic.bak
 132.3GB: boot/vmlinuz-2.6.24-16-generic
 132.4GB: initrd.img
 132.3GB: vmlinuz


```


-Nand

---

### Post by presence1960 on 2009-10-29
it looks like you installed Enterprise with a separate /boot partition. Since you are using Ubuntu's GRUB on MBR you need to chainload Enterprise from Ubuntu's menu.lst. Here is what I would do:

Boot into Ubuntu. Open a terminal and run this command ```
gksu gedit /boot/grub/menu.lst
``` That is a lowercase L in .lst

remove the entry in red below:
```

## ## End Default Options ##

[COLOR="Red"]title        Oracle Enterprise Linux 5.1
configfile    (hd0,0) /etc/grub.conf[/COLOR]

title        Ubuntu 8.04, kernel 2.6.24-16-generic
root        (hd0,7)
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=38774ea2-3f76-4b37-add1-014e85c9afd2 ro quiet splash
initrd        /boot/initrd.img-2.6.24-16-generic
quiet

title        Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root        (hd0,7)
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=38774ea2-3f76-4b37-add1-014e85c9afd2 ro single
initrd        /boot/initrd.img-2.6.24-16-generic

title        Ubuntu 8.04, memtest86+
root        (hd0,7)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

Now below END DEBIAN AUTO MAGIC KERNELS LIST  add this entry:
 
```
title          Oracle Enterprise Linux 5.1
rootnoverify   (hd0,0)
chainloader    +1
```

Click Save on the toolbar & close file. Reboot & try to boot Enterprise Linux.

---

### Post by nandyboy on 2009-10-29
Hi Presence1960, I have followed your instructions and edited the menu.lst file. But after rebooting, on choosing the Enterprise Linux option, its giving an error:

```
Error 13: Unsupported executable file format 
```

Following is how my menu.lst looks:

```

title        Ubuntu 8.04, kernel 2.6.24-16-generic
root        (hd0,8)
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=a8149b4a-0896-4948-919b-9ba103904502 ro quiet splash
initrd        /boot/initrd.img-2.6.24-16-generic
quiet

title        Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root        (hd0,8)
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=a8149b4a-0896-4948-919b-9ba103904502 ro single
initrd        /boot/initrd.img-2.6.24-16-generic

title        Ubuntu 8.04, memtest86+
root        (hd0,8)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title          Oracle Enterprise Linux 5.1
rootnoverify   (hd0,0)
chainloader    +1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda8.
title        Ubuntu 8.04, kernel 2.6.24-16-generic (on /dev/sda8)
root        (hd0,7)
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=38774ea2-3f76-4b37-add1-014e85c9afd2 ro quiet splash 
initrd        /boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda8.
title        Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode) (on /dev/sda8)
root        (hd0,7)
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=38774ea2-3f76-4b37-add1-014e85c9afd2 ro single 
initrd        /boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda8.
title        Ubuntu 8.04, memtest86+ (on /dev/sda8)
root        (hd0,7)
kernel        /boot/memtest86+.bin  
savedefault
boot

```



You might have noticed that I have installed two Ubuntu operating systems, one on hda7 and other on hda8. May be this is resulting in a conflict. Anyhow,since both are identical Ubuntu OS, I want to remove the one on hda7 and leave the system with Enterprise Linux and Ubuntu on hda8 (The one with 40GB disk space).

 Also, I had made a mess of SWAP partitions as well by creating two swap partitions. I assume, one might be enough and can be used with either of the two OS.....so one swap can also be dropped right??

Please suggest how to reconfigure my  setup, since I have some data present on Enterprise Linux which I want to retain.

-Nand

---

### Post by nandyboy on 2009-10-30
It seems Presence1960 is not there.....Can anyone of the forum members help me out of this situation???

I have installed Enterprise Linux, then two Ubuntu s/w (same version). My problem is now Iam unable to get Enterprise Linux option during startup screen. I want to do away with one of the Ubuntus (one installed on lesser disksize) and the other to be able to dual boot with Enterprise LInux and Ubuntu OS.

Thanx in advance
Nand

---

