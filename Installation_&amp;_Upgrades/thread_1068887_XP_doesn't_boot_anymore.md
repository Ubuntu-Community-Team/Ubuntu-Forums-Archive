---
title: "XP doesn't boot anymore"
date: 2009-02-13
forum: Installation &amp; Upgrades
---

### Post by zombaya01 on 2009-02-13
**This problem was fixed**



Hello,

I tried to install gfxboot using all sorts of guides I found but in the process I managed to screw up the booting of XP.  I still can get into GRUB and from there to kubuntu.  Bootgfx still doesn't work, but that's just a minor problem now.

One thing has changed though, in the past I got the GRUB-selectionscreen after stage 1.5, now after stage 2.0.  

My results from the info_boot_script are:

```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda2 and 
                       looks at sector 104958468 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #6 for 
                       /boot/grub/menu.lst.
    Mounting failed:
mount: onbekende bestandssysteemsoort ''

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       
    Boot sector type:  Grub
    Boot sector info:  Grub is installed in the boot sector of sda5 and looks 
                       at sector 66774076 of the same hard drive for the 
                       stage2 file, but no stage2 files can be found at this 
                       location.
    Mounting failed:
mount: onbekende bestandssysteemsoort ''

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Schijf /dev/sda: 120.0 GB, 120034123776 bytes
255 koppen, 63 sectoren/spoor, 14593 cilinders, totaal 234441648 sectoren
Eenheid = sectoren van 1 * 512 = 512 bytes
Schijf-ID: 0x30000000

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       240,974       240,912  de Dell Utility
/dev/sda2    *        241,664     4,435,967     4,194,304   7 HPFS/NTFS
/dev/sda3           4,450,005   135,315,494   130,865,490   f W95 Ext d (LBA)
/dev/sda5           4,450,068    65,882,564    61,432,497   7 HPFS/NTFS
/dev/sda6          65,882,628   127,315,124    61,432,497  83 Linux
/dev/sda7         127,315,188   135,315,494     8,000,307  82 Linux swap / Solaris
/dev/sda4         135,315,495   234,436,544    99,121,050   7 HPFS/NTFS

/dev/sda1 ends after the last cylinder of /dev/sda
/dev/sda2 ends after the last cylinder of /dev/sda
/dev/sda3 ends after the last cylinder of /dev/sda
/dev/sda5 ends after the last cylinder of /dev/sda
/dev/sda6 ends after the last cylinder of /dev/sda
/dev/sda7 ends after the last cylinder of /dev/sda
/dev/sda4 ends after the last cylinder of /dev/sda

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D7-0A0D" TYPE="vfat" 
/dev/sda4: UUID="3850851B5084E0CC" LABEL="WINUX" TYPE="ntfs" 
/dev/sda6: UUID="cba8dc55-786c-487c-b853-5fc8917bf433" TYPE="ext3" 
/dev/sda7: TYPE="swap" UUID="9c9d02dc-6b21-4058-93a8-b2ae11a952ff" 

=============================== "mount" output: ===============================

/dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
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
/dev/sda4 on /media/WINUX type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)

=========================== sda6/boot/grub/menu.lst: ===========================

gfxboot /boot/message
default 5
timeout 30

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
# kopt=root=UUID=cba8dc55-786c-487c-b853-5fc8917bf433 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=cba8dc55-786c-487c-b853-5fc8917bf433

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
# defoptions=splash quiet

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

title Ubuntu 8.10, kernel 2.6.27-11-generic
kernel /boot/vmlinuz-2.6.27-11-generic root=UUID=cba8dc55-786c-487c-b853-5fc8917bf433 ro splash quiet
initrd /boot/initrd.img-2.6.27-11-generic

title Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
kernel /boot/vmlinuz-2.6.27-11-generic root=UUID=cba8dc55-786c-487c-b853-5fc8917bf433 ro  single
initrd /boot/initrd.img-2.6.27-11-generic

title Ubuntu 8.10, memtest86+
kernel /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root

title Dell Utility Partition
root (hd0,0)
chainloader +1
savedefault
makeactive

# on /dev/sda2
title Microsoft Windows XP Professional
root (hd0,1)
chainloader +1
savedefault
makeactive


=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda6 :
UUID=cba8dc55-786c-487c-b853-5fc8917bf433 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda7 :
UUID=9c9d02dc-6b21-4058-93a8-b2ae11a952ff none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sda4 /media/WINUX ntfs-3g defaults,locale=nl_BE.UTF-8 0 0
/dev/sda5 /media/WindowsNTFS ntfs-3g defaults,locale=nl_BE.UTF-8 0 0


=================== sda6: Location of files loaded by Grub: ===================


  34.1GB: boot/grub/menu.lst
  53.7GB: boot/grub/stage2
  34.0GB: boot/initrd.img-2.6.27-11-generic
  34.0GB: boot/initrd.img-2.6.27-7-generic
  34.1GB: boot/initrd.img-2.6.27-9-generic
  34.0GB: boot/vmlinuz-2.6.27-11-generic
  34.1GB: boot/vmlinuz-2.6.27-7-generic
  34.1GB: boot/vmlinuz-2.6.27-9-generic
  34.0GB: initrd.img
  34.1GB: initrd.img.old
  34.0GB: vmlinuz
  34.1GB: vmlinuz.old

=============================== StdErr Messages: ===============================

/home/pieter/Bureaublad/boot_info_script024.sh: line 1043: [: =: eenzijdige operator verwacht
/home/pieter/Bureaublad/boot_info_script024.sh: line 1043: [: =: eenzijdige operator verwacht

```

The explanation of my partitions:

sda1: Dell partition software
sda2: Recovery partition for vista (I'm using XP now but kept it)
sda3: No idea what this does, probably nothing
sda4: my NTFS-partition which i use for sharing files between XP and kubuntu
sda5: NTFS-partition on which XP is actually installed
sda6: my linux partition
sda7: the swap-partition for linux


I also screwed around with ms-sys, trying to get things back, but I think it did more bad than good.

Is there a way to restore things back to what they were without losing any of my files?

---

### Post by dstew on 2009-02-13
What error message do you get when you select "Microsoft Windows XP Professional" from the grub menu?

---

### Post by caljohnsmith on 2009-02-13
It looks like you accidentally installed Grub to the boot sector of your sda2 and sda5 NTFS partitions (one of those must be Windows), so that's at least part of the problem preventing you from booting XP right now. To fix it, how about booting your Windows Install CD, go to the "recovery console" and do:
```
map
```
That will show a list of your partitions and their drive letters. Find the sda2 and sda5 NTFS partitions, and then do:
```
fixboot X:
```
And replace "X" with the drive letter of each of the sda2 and sda5 partitions. Also, you will need to reinstall Grub, because currently you are using a Windows MBR to boot Grub since the sda2 partition is marked as bootable. To fix Grub, how about booting your Live CD (the Ubuntu install CD), open a terminal (Applications > Accessories > Terminal) and do:
```
sudo grub
grub> root (hd0,5)
grub> setup (hd0)
grub> quit
```
Reboot, and let me know how far you get when booting the sda drive. We can work from there if necessary.

---

### Post by zombaya01 on 2009-02-13
Well, that worked like a charm.

Everything is back to normal, thank you very much.

May your karma be good and let you come back as something really good, a cow in India for example or a really spoiled petdog.

---

