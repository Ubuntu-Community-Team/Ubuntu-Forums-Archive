---
title: "Triple boot with WIndows 7, OpenSuse and Ubuntu 9.04"
date: 2009-09-06
forum: Installation &amp; Upgrades
---

### Post by isotonic_uk on 2009-09-06
Hi

Was wondering if someone could help me with a right mess I have got myself in.

I have been keen to try out OpenSuse 11.1 for some time now, I have been a Ubuntu user for a year and wanted the best of both, so went on a journey to install all 3 on my laptop. 

My laptop had Windows 7 on it and within the disk management I shrunk my 320gb drive to 250gb, so had 70gb to install my linux distros which I separated so both had 35gb each.

Once I had shrunk this, i then installed Suse 11.1. it installed fine, once I restarted I had a green bootloader, suse was the first option and it had windows in there. Both booted fine when there selection was chosen. 

I then installed Ubuntu, and that identified I had 2 OS's on there, I chose auto configure assuming it would use the unallocated 35gb remaining space to install itself on. 

Once I booted up though it goes straight into windows, I have lost the boot loader that Suse installed. 

Can anyone advise me on how I can get the two working? If I can manage to get one working, I would be grateful but would prefer to use Ubuntu.

Thanks

---

### Post by presence1960 on 2009-09-06
let's see exactly what you got on that machine first. Do this:

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by isotonic_uk on 2009-09-06
============================= Boot Info Summary: ==============================

 => Acer 3 is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda3 and 
                       looks at sector 543750819 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #6 for 
                       /boot/grub/menu.lst.

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Welcome to openSUSE 11.1 - 
                       Kernel ().
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda9: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x910c910c

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   507,266,845   507,059,998   7 HPFS/NTFS
/dev/sda3         507,268,440   625,137,344   117,868,905   f W95 Ext d (LBA)
/dev/sda5         512,505,693   516,714,659     4,208,967  82 Linux swap / Solaris
/dev/sda6         516,714,723   558,306,944    41,592,222  83 Linux
/dev/sda7         558,307,008   625,137,344    66,830,337  83 Linux
/dev/sda8         507,268,566   512,152,199     4,883,634  83 Linux
/dev/sda9         512,152,263   512,505,629       353,367  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe9784848

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   976,769,023   976,766,976   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="6C961049961015E4" LABEL="System Reserved" TYPE="ntfs" 
/dev/sda2: UUID="C24838D44838C8C5" TYPE="ntfs" 
/dev/sda5: TYPE="swap" UUID="0a8b3f84-651e-4984-a2bd-c3a156ea6aff" 
/dev/sda6: UUID="407173ae-3f65-4be8-a3ac-02f49c7933e6" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: UUID="65c4cf34-b6fe-4060-8678-0d910d3fff42" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda8: UUID="74792035-ba86-443c-8300-42133f8ca1aa" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda9: TYPE="swap" UUID="c47a612c-8874-43ee-a9c9-fcab4c7b4ba8" 
/dev/sdb1: UUID="2EE086E3E086B11F" LABEL="Virtualisation Drive" TYPE="ntfs" 

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
/dev/sdb1 on /media/Virtualisation Drive type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


=========================== sda6/boot/grub/menu.lst: ===========================

# Modified by YaST2. Last modification on Sun Aug 23 09:11:09 BST 2009
default 0
timeout 8
##YaST - generic_mbr
gfxmenu (hd0,5)/boot/message
##YaST - activate

###Don't change this comment - YaST2 identifier: Original name: linux###
title openSUSE 11.1
    root (hd0,5)
    kernel /boot/vmlinuz root=/dev/disk/by-id/ata-FUJITSU_MHZ2320BH_G2_K60LT952YE90-part6 resume=/dev/disk/by-id/ata-FUJITSU_MHZ2320BH_G2_K60LT952YE90-part5 splash=silent showopts vga=0x318
    initrd /boot/initrd

###Don't change this comment - YaST2 identifier: Original name: xen###
title XEN
    root (hd0,5)
    kernel /boot/xen.gz 
    module /boot/vmlinuz-xen root=/dev/disk/by-id/ata-FUJITSU_MHZ2320BH_G2_K60LT952YE90-part6 resume=/dev/disk/by-id/ata-FUJITSU_MHZ2320BH_G2_K60LT952YE90-part5 splash=silent showopts vga=0x318
    module /boot/initrd-xen

###Don't change this comment - YaST2 identifier: Original name:  Ubuntu 9.04, kernel 2.6.28-11-generic (/dev/sda8)###
title  Ubuntu 9.04, kernel 2.6.28-11-generic (/dev/sda8)
    root (hd0,7)
    configfile /boot/grub/menu.lst

###Don't change this comment - YaST2 identifier: Original name: windows 1###
title Windows 7 Enterprise
    rootnoverify (hd0,0)
    chainloader +1

###Don't change this comment - YaST2 identifier: Original name: windows 2###
title windows 2
    rootnoverify (hd0,1)
    chainloader +1

###Don't change this comment - YaST2 identifier: Original name: failsafe###
title Failsafe -- openSUSE 11.1
    root (hd0,5)
    kernel /boot/vmlinuz root=/dev/disk/by-id/ata-FUJITSU_MHZ2320BH_G2_K60LT952YE90-part6 showopts ide=nodma apm=off noresume nosmp maxcpus=0 edd=off powersaved=off nohz=off highres=off processor.max_cstate=1  x11failsafe vga=0x318
    initrd /boot/initrd

###Don't change this comment - YaST2 identifier: Original name: memtest86###
title Memory Test
    kernel (hd0,5)/boot/memtest.bin

###Don't change this comment - YaST2 identifier: Original name: linux###
title Kernel-2.6.27.29-0.1-default
    root (hd0,5)
    kernel /boot/vmlinuz-2.6.27.29-0.1-default root=/dev/disk/by-id/ata-FUJITSU_MHZ2320BH_G2_K60LT952YE90-part6 resume=/dev/disk/by-id/ata-FUJITSU_MHZ2320BH_G2_K60LT952YE90-part5 splash=silent showopts vga=0x318
    initrd /boot/initrd-2.6.27.29-0.1-default

###Don't change this comment - YaST2 identifier: Original name: linux###
title Kernel-xen
    root (hd0,5)
    kernel /boot/vmlinuz-xen root=/dev/disk/by-id/ata-FUJITSU_MHZ2320BH_G2_K60LT952YE90-part6 resume=/dev/disk/by-id/ata-FUJITSU_MHZ2320BH_G2_K60LT952YE90-part5 splash=silent showopts vga=0x318
    initrd /boot/initrd-xen

###Don't change this comment - YaST2 identifier: Original name: linux###
title Kernel-2.6.27.29-0.1-xen
    root (hd0,5)
    kernel /boot/vmlinuz-2.6.27.29-0.1-xen root=/dev/disk/by-id/ata-FUJITSU_MHZ2320BH_G2_K60LT952YE90-part6 resume=/dev/disk/by-id/ata-FUJITSU_MHZ2320BH_G2_K60LT952YE90-part5 splash=silent showopts vga=0x318
    initrd /boot/initrd-2.6.27.29-0.1-xen

=============================== sda6/etc/fstab: ===============================

/dev/disk/by-id/ata-FUJITSU_MHZ2320BH_G2_K60LT952YE90-part5 swap                 swap       defaults              0 0
/dev/disk/by-id/ata-FUJITSU_MHZ2320BH_G2_K60LT952YE90-part6 /                    ext3       acl,user_xattr        1 1
/dev/disk/by-id/ata-FUJITSU_MHZ2320BH_G2_K60LT952YE90-part7 /home                ext3       acl,user_xattr        1 2
/dev/disk/by-id/ata-FUJITSU_MHZ2320BH_G2_K60LT952YE90-part1 /windows/C           ntfs-3g    users,gid=users,fmask=133,dmask=022,locale=en_GB.UTF-8 0 0
/dev/disk/by-id/ata-FUJITSU_MHZ2320BH_G2_K60LT952YE90-part2 /windows/D           ntfs-3g    users,gid=users,fmask=133,dmask=022,locale=en_GB.UTF-8 0 0
proc                 /proc                proc       defaults              0 0
sysfs                /sys                 sysfs      noauto                0 0
debugfs              /sys/kernel/debug    debugfs    noauto                0 0
devpts               /dev/pts             devpts     mode=0620,gid=5       0 0

=================== sda6: Location of files loaded by Grub: ===================


 278.3GB: boot/grub/menu.lst
 278.4GB: boot/grub/stage2
 278.4GB: boot/initrd
 278.4GB: boot/initrd-2.6.27.29-0.1-default
 278.5GB: boot/initrd-2.6.27.29-0.1-xen
 278.5GB: boot/initrd-xen
 278.4GB: boot/vmlinuz
 278.4GB: boot/vmlinuz-2.6.27.29-0.1-default
 278.5GB: boot/vmlinuz-2.6.27.29-0.1-xen
 278.5GB: boot/vmlinuz-xen

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
# kopt=root=UUID=74792035-ba86-443c-8300-42133f8ca1aa ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=74792035-ba86-443c-8300-42133f8ca1aa

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
uuid        74792035-ba86-443c-8300-42133f8ca1aa
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=74792035-ba86-443c-8300-42133f8ca1aa ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        74792035-ba86-443c-8300-42133f8ca1aa
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=74792035-ba86-443c-8300-42133f8ca1aa ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        74792035-ba86-443c-8300-42133f8ca1aa
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


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title        openSUSE 11.1 - 2.6.27.29-0.1 (default) (on /dev/sda6)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.27.29-0.1-default root=/dev/disk/by-id/ata-FUJITSU_MHZ2320BH_G2_K60LT952YE90-part6 resume=/dev/disk/by-id/ata-FUJITSU_MHZ2320BH_G2_K60LT952YE90-part5 splash=silent showopts vga=0x318 
initrd        /boot/initrd-2.6.27.29-0.1-default
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title        Failsafe -- openSUSE 11.1 - 2.6.27.29-0.1 (on /dev/sda6)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.27.29-0.1-default root=/dev/disk/by-id/ata-FUJITSU_MHZ2320BH_G2_K60LT952YE90-part6 showopts ide=nodma apm=off noresume nosmp maxcpus=0 edd=off powersaved=off nohz=off highres=off processor.max_cstate=1 x11failsafe vga=0x317 
initrd        /boot/initrd-2.6.27.29-0.1-default
savedefault
boot


=============================== sda8/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda8 during installation
UUID=74792035-ba86-443c-8300-42133f8ca1aa /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda9 during installation
UUID=c47a612c-8874-43ee-a9c9-fcab4c7b4ba8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda8: Location of files loaded by Grub: ===================


 260.3GB: boot/grub/menu.lst
 259.9GB: boot/grub/stage2
 260.3GB: boot/initrd.img-2.6.28-11-generic
 261.5GB: boot/vmlinuz-2.6.28-11-generic
 260.3GB: initrd.img
 261.5GB: vmlinuz

---

### Post by presence1960 on 2009-09-06
Ok, this is what i would do. I would put jaunty's GRUB on MBR of sda and chainload Vista and Suse off of that. This has an advantage in the fact that when  a linux distro updates kernels it only auto updates the kernel in that distro's menu.lst. if you don't chainload the other distro(s) then you have to manually edit each menu.lst of the other distro(s) to use the new kernel.

Boot off the Ubuntu Live CD. Choose "try Ubuntu without any changes". When the desktop loads open a terminal. Do this:
```

1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,7)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,7)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or 
   whatever your hard disk + partition # is, to install GRUB to a 
   partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.

**In # 6 use setup (hd0)**
```

Reboot and choose Ubuntu to boot into Ubuntu. Then open a terminal and run this command ```
gksu gedit /boot/grub/menu.lst
``` That is a lowercase L in .lst

Scroll down to this line: ### END DEBIAN AUTOMAGIC KERNELS LIST

Delete everything after that line and add this:

```
title         Windows Vista (loader)
rootnoverify  (hd0,1)
chainloader   +1

title         Open Suse 11.1
rootnoverify  (hd0,5)
chainloader   +1
```

Click save on the toolbar and close the file. Reboot & try your Suse and Windows entries when GRUB loads.

---

### Post by isotonic_uk on 2009-09-06
Thank you, thank you, thank you. IT WORKS!!!

Did exactly what you said in the last post and it all works.

Thanks again.

---

### Post by presence1960 on 2009-09-06
> **isotonic_uk said:**
> Thank you, thank you, thank you. IT WORKS!!!

Did exactly what you said in the last post and it all works.

Thanks again.

Glad you got it working! Enjoy Ubuntu.

---

