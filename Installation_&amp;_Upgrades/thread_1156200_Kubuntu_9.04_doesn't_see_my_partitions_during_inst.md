---
title: "Kubuntu 9.04 doesn't see my partitions during install"
date: 2009-05-11
forum: Installation &amp; Upgrades
---

### Post by V1RUSW0rm on 2009-05-11
It's another thread about problem with partitions =) Here is my RESULTS of execution [BootInfoScript]("http://sourceforge.net/projects/bootinfoscript/"):
```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #7 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

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

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu karmic (development 
                       branch)
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

&#1056;”&#1056;&#1105;&#1057;&#1027;&#1056;&#1108; /dev/sda: 250.0 &#1056;“&#1056;‘, 250059350016 &#1056;±&#1056;°&#1056;&#8470;&#1057;‚
255 heads, 63 sectors/track, 30401 cylinders, &#1056;&#1030;&#1057;&#1027;&#1056;µ&#1056;&#1110;&#1056;&#1109; 488397168 &#1057;&#1027;&#1056;µ&#1056;&#1108;&#1057;‚&#1056;&#1109;&#1057;&#1026;&#1056;&#1109;&#1056;&#1030;
Units = &#1057;&#1027;&#1056;µ&#1056;&#1108;&#1057;‚&#1056;&#1109;&#1057;&#1026;&#1057;‹ of 1 * 512 = 512 bytes
Disk identifier: 0x97646c29

Partition  Boot         Start           End          Size  Id System

/dev/sda1         381,254,580   433,578,284    52,323,705   7 HPFS/NTFS
/dev/sda2    *     20,482,875    62,476,784    41,993,910   7 HPFS/NTFS
/dev/sda3          62,476,785   488,392,064   425,915,280   5 Extended
/dev/sda5          62,476,848   381,254,579   318,777,732   7 HPFS/NTFS
/dev/sda6         433,578,348   437,482,079     3,903,732  82 Linux swap / Solaris
/dev/sda7         437,482,143   488,392,064    50,909,922  83 Linux

/dev/sda1 overlaps with /dev/sda3

Drive: sdb ___________________ _____________________________________________________

&#1056;”&#1056;&#1105;&#1057;&#1027;&#1056;&#1108; /dev/sdb: 4009 &#1056;&#1114;&#1056;‘, 4009230336 &#1056;±&#1056;°&#1056;&#8470;&#1057;‚
255 heads, 63 sectors/track, 487 cylinders, &#1056;&#1030;&#1057;&#1027;&#1056;µ&#1056;&#1110;&#1056;&#1109; 7830528 &#1057;&#1027;&#1056;µ&#1056;&#1108;&#1057;‚&#1056;&#1109;&#1057;&#1026;&#1056;&#1109;&#1056;&#1030;
Units = &#1057;&#1027;&#1056;µ&#1056;&#1108;&#1057;‚&#1056;&#1109;&#1057;&#1026;&#1057;‹ of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *            128     7,830,527     7,830,400   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="AD1C2544FF6F36DA" LABEL="Vienna" TYPE="ntfs" 
/dev/sda2: UUID="7292E5D292E59ABD" LABEL="VistaOS" TYPE="ntfs" 
/dev/sda5: UUID="FC4518EAC7AB3530" TYPE="ntfs" 
/dev/sda6: TYPE="swap" UUID="ef5b27f4-adfe-48a2-94d9-828a33104c45" 
/dev/sda7: UUID="933f4ffa-d0a3-4779-96fc-2e796f9f8b23" TYPE="ext3" 
/dev/sdb1: LABEL="KUBUNTU" UUID="52F6-4B6E" TYPE="vfat" 

=============================== "mount" output: ===============================

/dev/sda7 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/v1rusw0rm/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=v1rusw0rm)
/dev/sdb1 on /media/KUBUNTU type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)


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
# kopt=root=UUID=933f4ffa-d0a3-4779-96fc-2e796f9f8b23 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=933f4ffa-d0a3-4779-96fc-2e796f9f8b23

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

title        Ubuntu jaunty (development branch), kernel 2.6.29-rc6
uuid        933f4ffa-d0a3-4779-96fc-2e796f9f8b23
kernel        /boot/vmlinuz-2.6.29-rc6 root=UUID=933f4ffa-d0a3-4779-96fc-2e796f9f8b23 ro quiet splash 
initrd        /boot/initrd.img-2.6.29-rc6
quiet

title        Ubuntu jaunty (development branch), kernel 2.6.29-rc6 (recovery mode)
uuid        933f4ffa-d0a3-4779-96fc-2e796f9f8b23
kernel        /boot/vmlinuz-2.6.29-rc6 root=UUID=933f4ffa-d0a3-4779-96fc-2e796f9f8b23 ro  single
initrd        /boot/initrd.img-2.6.29-rc6

title        Ubuntu jaunty (development branch), memtest86+
uuid        933f4ffa-d0a3-4779-96fc-2e796f9f8b23
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows Vista/Longhorn (loader)
rootnoverify    (hd0,1)
savedefault
chainloader    +1


=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=933f4ffa-d0a3-4779-96fc-2e796f9f8b23 /               ext3    relatime,errors=remount-ro 0       1
# none was on /dev/sda7 during installation
UUID=ef5b27f4-adfe-48a2-94d9-828a33104c45 none            swap    sw              0       0

=================== sda7: Location of files loaded by Grub: ===================


 235.8GB: boot/grub/menu.lst
 235.8GB: boot/grub/stage2
 235.8GB: boot/initrd.img-2.6.28-11-generic
 235.8GB: boot/initrd.img-2.6.28-8-generic
 235.8GB: boot/initrd.img-2.6.29-rc6
 235.8GB: boot/vmlinuz-2.6.28-11-generic
 235.9GB: boot/vmlinuz-2.6.28-8-generic
 235.8GB: boot/vmlinuz-2.6.29-rc6
 235.8GB: initrd.img
 235.8GB: initrd.img.old
 235.8GB: vmlinuz
 235.8GB: vmlinuz.old


```

My hardware is ASUS N10J with 250 GB hard drive.

Sorry for my very bad English.

---

### Post by V1RUSW0rm on 2009-05-12
I think that problem in sda1 which is primary partition but it is in logical disk part.

---

