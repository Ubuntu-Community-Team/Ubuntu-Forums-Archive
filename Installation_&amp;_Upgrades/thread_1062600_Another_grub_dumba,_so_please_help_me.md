---
title: "Another grub dumba**, so please help me"
date: 2009-02-07
forum: Installation &amp; Upgrades
---

### Post by momcilosystem on 2009-02-07
Hi all, I am a Linux newbie, but Windows pro, so I am not quite dumb, just a little :)

So, like a lot of other people I am having problem booting Fedora 10 from Ubuntu's grub.

Order of installation was: XP (MBR) -> Fedora (Self) -> Ubuntu (MBR)

I guess I should post my fdisk and menu.lst (as seen on so many places :D)

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x922d5f18

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3264    26218048+   7  HPFS/NTFS
/dev/sda2            3265        3289      200812+  83  Linux
/dev/sda3            3290       19457   129869460    f  W95 Ext'd (LBA)
/dev/sda5            3290        5900    20972826    7  HPFS/NTFS
/dev/sda6            5901        8511    20972826    7  HPFS/NTFS
/dev/sda7            8512       11122    20972826    7  HPFS/NTFS
/dev/sda8           11123       11644     4192933+  82  Linux swap / Solaris
/dev/sda9           11645       14255    20972826    6  FAT16
/dev/sda10          14256       16866    20972826    6  FAT16
/dev/sda11          16867       194
```

*little explanation of partitions (skip if not interesed :p):
```
sda1 = XP (x86)
sda2 = /boot (ubuntu grub)
sda3 = extended
sda5 = XP (x64)
sda6 = Vista (x86)
sda7 = Vista (x64)
sda8 = Linux Swap
sda9 = / Fedora 10 (x64)
sda10 = / Ubuntu 8.10 (x64)
sda11 = fat16 partition... just for fun :D
```

and

```
default		0
timeout		10
color cyan/blue white/blue

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		de076fd8-3336-491c-810b-548613cfa863
kernel		/vmlinuz-2.6.27-7-generic root=UUID=118c0fd2-1108-4992-bdde-c727443620e5 ro quiet splash 
initrd		/initrd.img-2.6.27-7-generic
quiet

title Fedora (2.6.27.5-117.fc10.x86_64)
root (hd0,8)
kernel /boot/vmlinuz-2.6.27.5-117.fc10.x86_64 ro root=UUID=caa82743-ce2$
initrd /boot/initrd-2.6.27.5-117.fc10.x86_64.img

title		Microsoft Windows
root		(hd0,0)
savedefault
chainloader	+1

```

So, booting Ubuntu works like a charm, booting XP also, but when booting to Fedora it states:

```
Error 17: Cannot mount selected partition

Press any key to continue...
```

Thanks to everybody and again sorry for reposting this ancient question

---

### Post by Pumalite on 2009-02-07
[http://users.bigpond.net.au/hermanzone/p15.htm#17](http://users.bigpond.net.au/hermanzone/p15.htm#17)

---

### Post by momcilosystem on 2009-02-07
Thanks for your reply, no use from there :(

All it said was to check partition number in menu.lst, and I did (before even posting) and to run ext3 check, which I did and nothing has changed...

I can imagine why I am not geting a lot of replys, because it seems that everything is just fine... and still it doesn't work.

So... please help.

Tnx again

---

### Post by caljohnsmith on 2009-02-07
In order to get a clearer picture of your setup, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by Tomatz on 2009-02-07
Try the super grub live cd. It allows you to boot from the cd or rewrite grub to the mbr:

[http://supergrub.forjamari.linex.org/?section=download](http://supergrub.forjamari.linex.org/?section=download)

;)

---

### Post by momcilosystem on 2009-02-07
OK, I did the boot info, and here are the results:
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #2 for /grub/stage2 and /grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  Windows Vista
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  Windows Vista
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda9: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Fedora release 10 (Cambridge) 
                       Kernel on an ()
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.conf /etc/fstab

sda10: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda11: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  According to the info in the boot sector, sda11 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x922d5f18

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    52,436,159    52,436,097   7 HPFS/NTFS
/dev/sda2          52,436,160    52,837,784       401,625  83 Linux
/dev/sda3          52,837,785   312,576,704   259,738,920   f W95 Ext d (LBA)
/dev/sda5          52,837,848    94,783,499    41,945,652   7 HPFS/NTFS
/dev/sda6          94,783,563   136,729,214    41,945,652   7 HPFS/NTFS
/dev/sda7         136,729,278   178,674,929    41,945,652   7 HPFS/NTFS
/dev/sda8         178,674,993   187,060,859     8,385,867  82 Linux swap / Solaris
/dev/sda9         187,060,923   229,006,574    41,945,652   6 FAT16
/dev/sda10        229,006,638   270,952,289    41,945,652   6 FAT16
/dev/sda11        270,952,353   312,576,704    41,624,352   b W95 FAT32


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7663f5f0

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   976,768,064   976,768,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="B0A4FE84A4FE4BFA" LABEL="XP x86" TYPE="ntfs" 
/dev/sda2: UUID="de076fd8-3336-491c-810b-548613cfa863" TYPE="ext2" 
/dev/sda5: UUID="A05475D65475AFA0" LABEL="XP x64" TYPE="ntfs" 
/dev/sda6: UUID="2228E01528DFE637" LABEL="Vista x86" TYPE="ntfs" 
/dev/sda7: UUID="BAB0C8D3B0C89773" LABEL="Vista x64" TYPE="ntfs" 
/dev/sda8: TYPE="swap" UUID="97ce0c0a-f62a-43a7-887e-6b32eb708b1b" 
/dev/sda9: LABEL="/" UUID="caa82743-ce2b-41a5-9adb-601a13087e96" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda10: UUID="118c0fd2-1108-4992-bdde-c727443620e5" TYPE="ext3" 
/dev/sda11: LABEL="DATA F32" UUID="9406-19E9" TYPE="vfat" 
/dev/sdb1: UUID="08E84435E8442374" LABEL="DATA" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda10 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=755)
/dev/sda2 on /boot type ext2 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/momcilo/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=momcilo)
/dev/scd0 on /media/cdrom1 type iso9660 (rw,nosuid,nodev,utf8,user=momcilo)

================================ sda1/boot.ini: ================================

;

;Warning: Boot.ini is used on Windows XP and earlier operating systems.

;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.

;

[boot loader]

timeout=15

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional x86" /NOEXECUTE=OPTIN /FASTDETECT

multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Professional x64" /NOEXECUTE=OPTIN /FASTDETECT


============================= sda2/grub/menu.lst: =============================

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
default		2

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

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
# kopt=root=UUID=118c0fd2-1108-4992-bdde-c727443620e5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=de076fd8-3336-491c-810b-548613cfa863

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
uuid		de076fd8-3336-491c-810b-548613cfa863
kernel		/vmlinuz-2.6.27-7-generic root=UUID=118c0fd2-1108-4992-bdde-c727443620e5 ro quiet splash 
initrd		/initrd.img-2.6.27-7-generic
quiet

#title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
#uuid		de076fd8-3336-491c-810b-548613cfa863
#kernel		/vmlinuz-2.6.27-7-generic root=UUID=118c0fd2-1108-4992-bdde-c727443620e5 ro  single
#initrd		/initrd.img-2.6.27-7-generic

#title		Ubuntu 8.10, memtest86+
#uuid		de076fd8-3336-491c-810b-548613cfa863
#kernel		/memtest86+.bin
#quiet

title Fedora (2.6.27.5-117.fc10.x86_64)
root (hd0,8)
kernel /boot/vmlinuz-2.6.27.5-117.fc10.x86_64 ro root=UUID=caa82743-ce2$
initrd /boot/initrd-2.6.27.5-117.fc10.x86_64.img

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
#title		Other operating systems:
#root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows
root		(hd0,0)
savedefault
chainloader	+1


=================== sda2: Location of files loaded by Grub: ===================


  26.9GB: grub/menu.lst
  26.9GB: grub/stage2
  26.8GB: initrd.img-2.6.27-7-generic
  26.8GB: vmlinuz-2.6.27-7-generic

========================== sda9/boot/grub/grub.conf: ==========================

# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You do not have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /, eg.
#          root (hd0,8)
#          kernel /boot/vmlinuz-version ro root=/dev/sda9
#          initrd /boot/initrd-version.img
#boot=/dev/sda9
default=0
timeout=5
splashimage=(hd0,8)/boot/grub/splash.xpm.gz
hiddenmenu
title Fedora (2.6.27.5-117.fc10.x86_64)
	root (hd0,8)
	kernel /boot/vmlinuz-2.6.27.5-117.fc10.x86_64 ro root=UUID=caa82743-ce2b-41a5-9adb-601a13087e96 rhgb quiet
	initrd /boot/initrd-2.6.27.5-117.fc10.x86_64.img
title Other
	rootnoverify (hd0,0)
	chainloader +1

=============================== sda9/etc/fstab: ===============================


#
# /etc/fstab
# Created by anaconda on Sat Feb  7 08:16:01 2009
#
# Accessible filesystems, by reference, are maintained under '/dev/disk'
# See man pages fstab(5), findfs(8), mount(8) and/or vol_id(8) for more info
#
UUID=caa82743-ce2b-41a5-9adb-601a13087e96 /                       ext3    defaults        1 1
tmpfs                   /dev/shm                tmpfs   defaults        0 0
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
sysfs                   /sys                    sysfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0
UUID=97ce0c0a-f62a-43a7-887e-6b32eb708b1b swap                    swap    defaults        0 0

=================== sda9: Location of files loaded by Grub: ===================


 110.1GB: boot/grub/grub.conf
 110.1GB: boot/grub/menu.lst
 110.1GB: boot/grub/stage2
 110.0GB: boot/initrd-2.6.27.5-117.fc10.x86_64.img
 110.1GB: boot/vmlinuz-2.6.27.5-117.fc10.x86_64

========================== sda10/boot/grub/menu.lst: ==========================

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
default		2

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

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
# kopt=root=UUID=118c0fd2-1108-4992-bdde-c727443620e5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=de076fd8-3336-491c-810b-548613cfa863

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
uuid		de076fd8-3336-491c-810b-548613cfa863
kernel		/vmlinuz-2.6.27-7-generic root=UUID=118c0fd2-1108-4992-bdde-c727443620e5 ro quiet splash 
initrd		/initrd.img-2.6.27-7-generic
quiet

#title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
#uuid		de076fd8-3336-491c-810b-548613cfa863
#kernel		/vmlinuz-2.6.27-7-generic root=UUID=118c0fd2-1108-4992-bdde-c727443620e5 ro  single
#initrd		/initrd.img-2.6.27-7-generic

#title		Ubuntu 8.10, memtest86+
#uuid		de076fd8-3336-491c-810b-548613cfa863
#kernel		/memtest86+.bin
#quiet

title Fedora (2.6.27.5-117.fc10.x86_64)
root (hd0,8)
kernel /boot/vmlinuz-2.6.27.5-117.fc10.x86_64 ro root=UUID=caa82743-ce2$
initrd /boot/initrd-2.6.27.5-117.fc10.x86_64.img

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
#title		Other operating systems:
#root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows
root		(hd0,0)
savedefault
chainloader	+1


=============================== sda10/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda10
UUID=118c0fd2-1108-4992-bdde-c727443620e5 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=de076fd8-3336-491c-810b-548613cfa863 /boot           ext2    relatime        0       2
# /dev/sda8
UUID=97ce0c0a-f62a-43a7-887e-6b32eb708b1b none            swap    sw              0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda10: Location of files loaded by Grub: ===================


 117.3GB: boot/grub/menu.lst
 117.3GB: boot/grub/stage2
 117.2GB: boot/initrd.img-2.6.27-7-generic
 117.2GB: boot/vmlinuz-2.6.27-7-generic
 117.2GB: initrd.img
 117.2GB: vmlinuz

```

I hope it can help clarify any errors.

Regearding SuperGrub - my grub is working fine, I can boot to Ubuntu and XP, it just cannot boot to fedora, and I can't see the way I could use super grub to resolve my problem - please advise.

Tnx again all for your effort

edit: Boot on /dev/sdb is something you should ignore... it's just leftover from old windows (it's not included anywhere)

---

### Post by Tomatz on 2009-02-07
> **momcilosystem said:**
> OK, I did the boot info, and here are the results:
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #2 for /grub/stage2 and /grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  Windows Vista
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  Windows Vista
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda9: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Fedora release 10 (Cambridge) 
                       Kernel on an ()
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.conf /etc/fstab

sda10: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda11: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  According to the info in the boot sector, sda11 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x922d5f18

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    52,436,159    52,436,097   7 HPFS/NTFS
/dev/sda2          52,436,160    52,837,784       401,625  83 Linux
/dev/sda3          52,837,785   312,576,704   259,738,920   f W95 Ext d (LBA)
/dev/sda5          52,837,848    94,783,499    41,945,652   7 HPFS/NTFS
/dev/sda6          94,783,563   136,729,214    41,945,652   7 HPFS/NTFS
/dev/sda7         136,729,278   178,674,929    41,945,652   7 HPFS/NTFS
/dev/sda8         178,674,993   187,060,859     8,385,867  82 Linux swap / Solaris
/dev/sda9         187,060,923   229,006,574    41,945,652   6 FAT16
/dev/sda10        229,006,638   270,952,289    41,945,652   6 FAT16
/dev/sda11        270,952,353   312,576,704    41,624,352   b W95 FAT32


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7663f5f0

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   976,768,064   976,768,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="B0A4FE84A4FE4BFA" LABEL="XP x86" TYPE="ntfs" 
/dev/sda2: UUID="de076fd8-3336-491c-810b-548613cfa863" TYPE="ext2" 
/dev/sda5: UUID="A05475D65475AFA0" LABEL="XP x64" TYPE="ntfs" 
/dev/sda6: UUID="2228E01528DFE637" LABEL="Vista x86" TYPE="ntfs" 
/dev/sda7: UUID="BAB0C8D3B0C89773" LABEL="Vista x64" TYPE="ntfs" 
/dev/sda8: TYPE="swap" UUID="97ce0c0a-f62a-43a7-887e-6b32eb708b1b" 
/dev/sda9: LABEL="/" UUID="caa82743-ce2b-41a5-9adb-601a13087e96" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda10: UUID="118c0fd2-1108-4992-bdde-c727443620e5" TYPE="ext3" 
/dev/sda11: LABEL="DATA F32" UUID="9406-19E9" TYPE="vfat" 
/dev/sdb1: UUID="08E84435E8442374" LABEL="DATA" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda10 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=755)
/dev/sda2 on /boot type ext2 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/momcilo/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=momcilo)
/dev/scd0 on /media/cdrom1 type iso9660 (rw,nosuid,nodev,utf8,user=momcilo)

================================ sda1/boot.ini: ================================

;

;Warning: Boot.ini is used on Windows XP and earlier operating systems.

;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.

;

[boot loader]

timeout=15

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional x86" /NOEXECUTE=OPTIN /FASTDETECT

multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Professional x64" /NOEXECUTE=OPTIN /FASTDETECT


============================= sda2/grub/menu.lst: =============================

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
default		2

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

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
# kopt=root=UUID=118c0fd2-1108-4992-bdde-c727443620e5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=de076fd8-3336-491c-810b-548613cfa863

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
uuid		de076fd8-3336-491c-810b-548613cfa863
kernel		/vmlinuz-2.6.27-7-generic root=UUID=118c0fd2-1108-4992-bdde-c727443620e5 ro quiet splash 
initrd		/initrd.img-2.6.27-7-generic
quiet

#title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
#uuid		de076fd8-3336-491c-810b-548613cfa863
#kernel		/vmlinuz-2.6.27-7-generic root=UUID=118c0fd2-1108-4992-bdde-c727443620e5 ro  single
#initrd		/initrd.img-2.6.27-7-generic

#title		Ubuntu 8.10, memtest86+
#uuid		de076fd8-3336-491c-810b-548613cfa863
#kernel		/memtest86+.bin
#quiet

title Fedora (2.6.27.5-117.fc10.x86_64)
root (hd0,8)
kernel /boot/vmlinuz-2.6.27.5-117.fc10.x86_64 ro root=UUID=caa82743-ce2$
initrd /boot/initrd-2.6.27.5-117.fc10.x86_64.img

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
#title		Other operating systems:
#root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows
root		(hd0,0)
savedefault
chainloader	+1


=================== sda2: Location of files loaded by Grub: ===================


  26.9GB: grub/menu.lst
  26.9GB: grub/stage2
  26.8GB: initrd.img-2.6.27-7-generic
  26.8GB: vmlinuz-2.6.27-7-generic

========================== sda9/boot/grub/grub.conf: ==========================

# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You do not have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /, eg.
#          root (hd0,8)
#          kernel /boot/vmlinuz-version ro root=/dev/sda9
#          initrd /boot/initrd-version.img
#boot=/dev/sda9
default=0
timeout=5
splashimage=(hd0,8)/boot/grub/splash.xpm.gz
hiddenmenu
title Fedora (2.6.27.5-117.fc10.x86_64)
	root (hd0,8)
	kernel /boot/vmlinuz-2.6.27.5-117.fc10.x86_64 ro root=UUID=caa82743-ce2b-41a5-9adb-601a13087e96 rhgb quiet
	initrd /boot/initrd-2.6.27.5-117.fc10.x86_64.img
title Other
	rootnoverify (hd0,0)
	chainloader +1

=============================== sda9/etc/fstab: ===============================


#
# /etc/fstab
# Created by anaconda on Sat Feb  7 08:16:01 2009
#
# Accessible filesystems, by reference, are maintained under '/dev/disk'
# See man pages fstab(5), findfs(8), mount(8) and/or vol_id(8) for more info
#
UUID=caa82743-ce2b-41a5-9adb-601a13087e96 /                       ext3    defaults        1 1
tmpfs                   /dev/shm                tmpfs   defaults        0 0
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
sysfs                   /sys                    sysfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0
UUID=97ce0c0a-f62a-43a7-887e-6b32eb708b1b swap                    swap    defaults        0 0

=================== sda9: Location of files loaded by Grub: ===================


 110.1GB: boot/grub/grub.conf
 110.1GB: boot/grub/menu.lst
 110.1GB: boot/grub/stage2
 110.0GB: boot/initrd-2.6.27.5-117.fc10.x86_64.img
 110.1GB: boot/vmlinuz-2.6.27.5-117.fc10.x86_64

========================== sda10/boot/grub/menu.lst: ==========================

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
default		2

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

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
# kopt=root=UUID=118c0fd2-1108-4992-bdde-c727443620e5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=de076fd8-3336-491c-810b-548613cfa863

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
uuid		de076fd8-3336-491c-810b-548613cfa863
kernel		/vmlinuz-2.6.27-7-generic root=UUID=118c0fd2-1108-4992-bdde-c727443620e5 ro quiet splash 
initrd		/initrd.img-2.6.27-7-generic
quiet

#title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
#uuid		de076fd8-3336-491c-810b-548613cfa863
#kernel		/vmlinuz-2.6.27-7-generic root=UUID=118c0fd2-1108-4992-bdde-c727443620e5 ro  single
#initrd		/initrd.img-2.6.27-7-generic

#title		Ubuntu 8.10, memtest86+
#uuid		de076fd8-3336-491c-810b-548613cfa863
#kernel		/memtest86+.bin
#quiet

title Fedora (2.6.27.5-117.fc10.x86_64)
root (hd0,8)
kernel /boot/vmlinuz-2.6.27.5-117.fc10.x86_64 ro root=UUID=caa82743-ce2$
initrd /boot/initrd-2.6.27.5-117.fc10.x86_64.img

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
#title		Other operating systems:
#root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows
root		(hd0,0)
savedefault
chainloader	+1


=============================== sda10/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda10
UUID=118c0fd2-1108-4992-bdde-c727443620e5 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=de076fd8-3336-491c-810b-548613cfa863 /boot           ext2    relatime        0       2
# /dev/sda8
UUID=97ce0c0a-f62a-43a7-887e-6b32eb708b1b none            swap    sw              0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda10: Location of files loaded by Grub: ===================


 117.3GB: boot/grub/menu.lst
 117.3GB: boot/grub/stage2
 117.2GB: boot/initrd.img-2.6.27-7-generic
 117.2GB: boot/vmlinuz-2.6.27-7-generic
 117.2GB: initrd.img
 117.2GB: vmlinuz

```

I hope it can help clarify any errors.

Regearding SuperGrub - my grub is working fine, I can boot to Ubuntu and XP, it just cannot boot to fedora, and I can't see the way I could use super grub to resolve my problem - please advise.

Tnx again all for your effort

Supergrub will/should rewrite grub to boot fedora also. You can add the fedora boot option manually if you like though. ;)

---

### Post by momcilosystem on 2009-02-07
I did, I added it manualy (copy/paste from Fedora's menu.lst) and that didn't work, and I don't have any idea how to work with supergrub, so please be patient and precise in your explanation

Tnx

---

### Post by Pumalite on 2009-02-07
Who owns the Grub?

---

### Post by momcilosystem on 2009-02-07
I am not sure what are you asking, but if you ask from which distro I installed grub to MBR and /boot partition then it's owned by Ubuntu

In Fedora I said to install it to its partition /dev/sda8 so there would be files in /boot on /dev/sda8

Correct me if I didn't understood what are you asking

Tnx again!

---

### Post by caljohnsmith on 2009-02-07
How about trying:
```
sudo grub
grub> root (hd0,8)
grub> setup (hd0,8)
grub> quit
```
And then in your Ubuntu's menu.lst, try using the following entry for Fedora:
```
title Fedora on sda9
root (hd0,8)
chainloader +1
```
Let me know if that works OK.

---

### Post by momcilosystem on 2009-02-07
Nope, it's not working:

```
grub> setup (hd0,8)
setup (hd0,8)

Error 17: Cannot mount selected partition

```

---

### Post by caljohnsmith on 2009-02-07
[QUOTE=momcilosystem]```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x922d5f18

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    52,436,159    52,436,097   7 HPFS/NTFS
/dev/sda2          52,436,160    52,837,784       401,625  83 Linux
/dev/sda3          52,837,785   312,576,704   259,738,920   f W95 Ext d (LBA)
/dev/sda5          52,837,848    94,783,499    41,945,652   7 HPFS/NTFS
/dev/sda6          94,783,563   136,729,214    41,945,652   7 HPFS/NTFS
/dev/sda7         136,729,278   178,674,929    41,945,652   7 HPFS/NTFS
/dev/sda8         178,674,993   187,060,859     8,385,867  82 Linux swap / Solaris
[COLOR="Blue"]/dev/sda9         187,060,923   229,006,574    41,945,652   6 FAT16[/COLOR]
/dev/sda10        229,006,638   270,952,289    41,945,652   6 FAT16
/dev/sda11        270,952,353   312,576,704    41,624,352   b W95 FAT32
```
[/QUOTE]
Somehow your partition table has your Fedora sda9 partition incorrectly listed as having a FAT16 file system instead of Linux, so I would suggest first correcting that:
```
sudo sfdisk -c /dev/sda 9 83
```
Then try running the Grub commands from my previous post again (make sure to use "sudo grub" and not just "grub" to get the Grub CLI), and if you still get error 17, please post:
```
sudo mount /dev/sda9 /mnt && ls -l /mnt
```
And we can work from there.

---

### Post by momcilosystem on 2009-02-07
Your advice helped me! I can now boot to Fedora.

You pointed out that ext3 wasn't detected corectly and what is more surprising is that it does the same thing with Ubuntu's / filesystem (it's sda10)

Do you think that if I formatted both partitions to ext2 - I could be able to do everything smoothly: Ubuntu's grub would recognise Fedora and add it to Grub automaticly and if so, what woould I loose by choosing ext2 over ext3?

I just want to understand this a little better, tnx!

---

### Post by caljohnsmith on 2009-02-07
I would definitely not format your sda9 and sda10 linux partitions, because they mount and are accessible just fine; the only problem was that your partition table somehow did not have the correct file system listed for those partitions. That problem is really easy to correct with a single command as you saw. And by the way, since your sda10 Ubuntu partition is also incorrectly listed as FAT16 in the partition table, it would be good to correct it too:
```
sudo sfdisk -c /dev/sda 10 83
```
And then you should be all set.

---

### Post by momcilosystem on 2009-02-07
Ok, I will do that,

I have two more questions:

If I now run 
```
sudo grub
root (hd0,1)
setup (hd0,1)
quit
```

would I be able to boot to linuxes? Or should I keep the current config (I am asking this for future restorations of grub - I might forget where to execute setup (hd0,x) :))

And another thing, I just run updates and I have a dilema, there's a window asking me about menu.lst. Please advise:

---

### Post by momcilosystem on 2009-02-07
So, I was able to setup grub on hd0,1 and everything works just fine.

I would like to give my best regards to caljohnsmith who helped me and had a lot of patience to explain everything. And I would like to say that this thread is officialy **SOLVED** :D


Tnx again, and I hope I won't bug you for a while ;)

---

### Post by caljohnsmith on 2009-02-07
Glad to hear it's all working; cheers and enjoy all your Linux distros and Windows. :)

---

