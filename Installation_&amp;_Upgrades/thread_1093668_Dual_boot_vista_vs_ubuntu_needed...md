---
title: "Dual boot vista vs ubuntu needed.."
date: 2009-03-11
forum: Installation &amp; Upgrades
---

### Post by Tuliku on 2009-03-11
Hi, i need some advice.
My pc is as following:

Disk1 (hd0, sda)
- 200 gb  NTFS (win vista 64bit) 
- 50 gb NTFS
- 500 gb NTFS

Disk2 (hd1, sdb)
- 8 gb swap
- 20 gb EXT3 (/)
- 37 gb EXT3 (/home)
- 686 gb NTFS

Disk3 (hd2, sdc)
- 750 gb NTFS	

After i installed ubuntu 8.10, i got grub error 22.
I re-installed grub using the live cd, but still same error.
I re-installed Ubuntu completely, installing grub on sdb, but still the same error 22 message.
Using the vista cd, i fixed te mbr using the command line.

Now my question.
I can install ubuntu 8.10 64bit again, but where should i install the boot loader, to make it work ?
- to the vista partition ?
- to the / partition ?
- somewhere else ?

thanks in advance

---

### Post by confused57 on 2009-03-11
What you might want to do is install grub to the / partition, then use EasyBCD to boot Ubuntu from the Vista's bootloader:
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)

---

### Post by Tuliku on 2009-03-12
Hi, did what you suggested, and Vista works fine formt eh bootloader menu.
From when choosing ubuntu, i end up in grub with some error messages.

I also run the "https://sourceforge.net/projects/bootinfoscript/" script from CalJohnSmith, and this is the output:


```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     BootPart in the file 
                       /NST/nst_grub-557F88DCF7618D9B8108762B4CEAD95B.mbr is 
                       trying to chain load sector #16386300 on boot drive #2 
                       BootPart in the file /NST/nst_grub.mbr is trying to 
                       chain load sector #16386300 on boot drive #2
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /grldr

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sdb2 and 
                       looks at sector 56498436 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sdb. Stage2 looks on partition #2 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x55135513

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   308,030,309   308,030,247   7 HPFS/NTFS
/dev/sda2         453,434,625 1,465,144,064 1,011,709,440   f W95 Ext d (LBA)
/dev/sda5         453,434,688 1,465,144,064 1,011,709,377   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xfac4a6a9

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    16,386,299    16,386,237  82 Linux swap / Solaris
/dev/sdb2    *     16,386,300    58,171,364    41,785,065  83 Linux
/dev/sdb3          58,171,365   133,949,969    75,778,605  83 Linux
/dev/sdb4         133,949,970 1,465,144,064 1,331,194,095   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 750.1 GB, 750156374016 bytes
81 heads, 62 sectors/track, 291746 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x554e554e

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63 1,465,149,166 1,465,149,104   7 HPFS/NTFS

/dev/sdc1 ends after the last cylinder of /dev/sdc

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="BCE60F5FE60F18F2" TYPE="ntfs" 
/dev/sda5: UUID="908486BB8486A2F8" TYPE="ntfs" 
/dev/sdb1: TYPE="swap" UUID="9e15023d-d0d3-4b97-8497-9856e11d5f1f" 
/dev/sdb2: UUID="0ee3dd0e-436a-45ad-81e7-f5572255e1c8" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb3: UUID="b429b03b-6ef3-437f-a01f-2ada93bb8df4" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb4: UUID="9864D20E64D1EECE" TYPE="ntfs" 
/dev/sdc1: UUID="3E8055228054E1C7" TYPE="ntfs" 
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


=========================== sdb2/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=0ee3dd0e-436a-45ad-81e7-f5572255e1c8 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=0ee3dd0e-436a-45ad-81e7-f5572255e1c8

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
uuid		0ee3dd0e-436a-45ad-81e7-f5572255e1c8
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=0ee3dd0e-436a-45ad-81e7-f5572255e1c8 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		0ee3dd0e-436a-45ad-81e7-f5572255e1c8
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=0ee3dd0e-436a-45ad-81e7-f5572255e1c8 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		0ee3dd0e-436a-45ad-81e7-f5572255e1c8
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
chainloader	+1


=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb2
UUID=0ee3dd0e-436a-45ad-81e7-f5572255e1c8 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb3
UUID=b429b03b-6ef3-437f-a01f-2ada93bb8df4 /home           ext3    relatime        0       2
# /dev/sdb1
UUID=9e15023d-d0d3-4b97-8497-9856e11d5f1f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb2: Location of files loaded by Grub: ===================


  28.9GB: boot/grub/menu.lst
  28.9GB: boot/grub/stage2
  28.9GB: boot/initrd.img-2.6.27-7-generic
  28.9GB: boot/vmlinuz-2.6.27-7-generic
  28.9GB: initrd.img
  28.9GB: vmlinuz
```

---

### Post by Tuliku on 2009-03-12
Also tried SuperGrubDisk now, but no luck, it says it cant read the linux partitions. :(

---

### Post by Tuliku on 2009-03-12
Getting fed up with trying everything.
Disk 2 is formatted to NTFS, and now preparing disk one for some more partitions for Ubuntu, lets see if it works then.
Will keep this updated here.

---

### Post by Tuliku on 2009-03-12
Installed Ubuntu now on the same disk as vista, and all is perfectly running fine.

Bye for now :-)

---

