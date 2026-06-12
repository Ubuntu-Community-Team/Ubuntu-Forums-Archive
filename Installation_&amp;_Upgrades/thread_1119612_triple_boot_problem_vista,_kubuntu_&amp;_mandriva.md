---
title: "triple boot problem: vista, kubuntu &amp; mandriva"
date: 2009-04-08
forum: Installation &amp; Upgrades
---

### Post by pedrogent on 2009-04-08
Hello all. I'm triple booting (or at least trying to) Vista, Kubuntu & Mandriva (installed in that order).

Mandriva has installed a nice graphical GRUB. From it I can boot into both Mandriva & Vista no problems at all. I can't boot Kubuntu altho' I could before I'd installed Mandriva. I can't even coax Kubuntu into booting using a Super Grub Disk.

The output of

```
cat /boot/grub/menu.lst
```

is as follows:

```
timeout 10
color black/cyan yellow/cyan
gfxmenu (hd0,3)/boot/gfxmenu
default 0

title linux
kernel (hd0,3)/boot/vmlinuz BOOT_IMAGE=linux root=LABEL=mandriva splash=silent vga=788
initrd (hd0,3)/boot/initrd.img

title linux-nonfb
kernel (hd0,3)/boot/vmlinuz BOOT_IMAGE=linux-nonfb root=LABEL=mandriva
initrd (hd0,3)/boot/initrd.img

title failsafe
kernel (hd0,3)/boot/vmlinuz BOOT_IMAGE=failsafe root=LABEL=mandriva failsafe
initrd (hd0,3)/boot/initrd.img

title windows
root (hd0,0)
makeactive
chainloader +1

title Ubuntu 8.10
root (hd0,1)
configfile /boot/grub/menu.lst

title 2.6.27-serverrc8-2mnb
kernel (hd0,3)/boot/vmlinuz-2.6.27-server-0.rc8.2mnb BOOT_IMAGE=2.6.27-serverrc8-2mnb root=LABEL=mandriva splash=silent vga=788
initrd (hd0,3)/boot/initrd-2.6.27-server-0.rc8.2mnb.img

title server 2.6.27.19-1mnb
kernel (hd0,3)/boot/vmlinuz-2.6.27.19-server-1mnb BOOT_IMAGE=server_2.6.27.19-1mnb root=LABEL=mandriva splash=silent vga=788
initrd (hd0,3)/boot/initrd-2.6.27.19-server-1mnb.img
```

The output of

```
sudo fdisk -l
```

is as follows:

```
Disk /dev/sda: 500.1 GB, 500106780160 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e106e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       43913   352729084    7  HPFS/NTFS
/dev/sda2           43914       52113    65866500   83  Linux
/dev/sda3           60314       60801     3919860   82  Linux swap / Solaris
/dev/sda4           52114       60313    65866500   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 640.1 GB, 640133946880 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0004552d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2       77825   625121280    7  HPFS/NTFS

Disk /dev/sdc: 320.0 GB, 320071851520 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000780fc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       38914   312567808    7  HPFS/NTFS

Disk /dev/sdd: 500.1 GB, 500106780160 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a3325

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           2       60801   488376000    7  HPFS/NTFS
```

I suspect the problem has something to do with the 'configfile /boot/grub/menu.lst' bit in the 'Ubuntu 8.10' entry, but I'm unsure.

Can anyone help me out here? I'm completely stuck.

Thanks in advance.

---

### Post by davideotape on 2009-04-08
Which partition is your kubuntu installation on (I'm guessing either sda 2 or sda 4)?

---

### Post by pedrogent on 2009-04-08
> **davideotape said:**
> Which partition is your kubuntu installation on (I'm guessing either sda 2 or sda 4)?

Vista is on sda1. Kubuntu is on sda2. Mandriva is on sda4.

Here is some more info that may be of use:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #4 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc
 => Grub0.97 is installed in the MBR of /dev/sdd and looks on boot drive #2 in 
    partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Mandriva Linux release 2009.0 
                       (Official) for x86_64 Kernel 2.6.27.19-server-1mnb on 
                       a Dual-processor x86_64 /
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb1: _________________________________________________________________________

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

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500106780160 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976771055 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000e106e

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   705,460,215   705,458,168   7 HPFS/NTFS
/dev/sda2         705,462,345   837,195,344   131,733,000  83 Linux
/dev/sda3         968,928,345   976,768,064     7,839,720  82 Linux swap / Solaris
/dev/sda4         837,195,345   968,928,344   131,733,000  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 640.1 GB, 640133946880 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250261615 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0004552d

Partition  Boot         Start           End          Size  Id System

/dev/sdb1              16,065 1,250,258,624 1,250,242,560   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 320.0 GB, 320071851520 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625140335 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000780fc

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               2,048   625,137,663   625,135,616   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 500.1 GB, 500106780160 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976771055 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000a3325

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *         16,065   976,768,064   976,752,000   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="749236D892369F14" LABEL="vista" TYPE="ntfs" 
/dev/sda2: UUID="a86375d0-c01a-43d1-bab2-16f8e8fa2180" TYPE="ext3" 
/dev/sda3: TYPE="swap" UUID="899e0f04-ee10-4c5e-9537-5e192ab4bb6d" 
/dev/sda4: LABEL="mandriva" UUID="5d34779a-802d-45c4-b623-289abae9b710" TYPE="ext3" 
/dev/sdb1: UUID="5D5AB0864C4975A7" LABEL="motherlode" TYPE="ntfs" 
/dev/sdc1: UUID="6E7478167477DEF1" LABEL="brick" TYPE="ntfs" 
/dev/sdd1: UUID="3629E3943D68E98B" LABEL="tunes" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda4 on / type ext3 (rw,relatime)
none on /proc type proc (rw)
/dev/sdc1 on /mnt/brick type fuseblk (rw,allow_other,blksize=4096)
/dev/sda2 on /mnt/kubuntu type ext3 (rw,relatime)
/dev/sdb1 on /mnt/motherlode type fuseblk (rw,allow_other,blksize=4096)
/dev/sdd1 on /mnt/tunes type fuseblk (rw,allow_other,blksize=4096)
/dev/sda1 on /mnt/vista type fuseblk (rw,allow_other,blksize=4096)
none on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)


=========================== sda2/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=a86375d0-c01a-43d1-bab2-16f8e8fa2180 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=a86375d0-c01a-43d1-bab2-16f8e8fa2180

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
uuid		a86375d0-c01a-43d1-bab2-16f8e8fa2180
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=a86375d0-c01a-43d1-bab2-16f8e8fa2180 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		a86375d0-c01a-43d1-bab2-16f8e8fa2180
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=a86375d0-c01a-43d1-bab2-16f8e8fa2180 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		a86375d0-c01a-43d1-bab2-16f8e8fa2180
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=a86375d0-c01a-43d1-bab2-16f8e8fa2180 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		a86375d0-c01a-43d1-bab2-16f8e8fa2180
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=a86375d0-c01a-43d1-bab2-16f8e8fa2180 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		a86375d0-c01a-43d1-bab2-16f8e8fa2180
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Teh BOLDNESS:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=a86375d0-c01a-43d1-bab2-16f8e8fa2180 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdc1
UUID=3629E3943D68E98B /media/music    ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb1
UUID=5D5AB0864C4975A7 /media/storage  ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda1
UUID=749236D892369F14 /media/vista    ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda3
UUID=899e0f04-ee10-4c5e-9537-5e192ab4bb6d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda2: Location of files loaded by Grub: ===================


 361.2GB: boot/grub/menu.lst
 361.2GB: boot/grub/stage2
 362.1GB: boot/initrd.img-2.6.27-11-generic
 361.2GB: boot/initrd.img-2.6.27-7-generic
 395.5GB: boot/vmlinuz-2.6.27-11-generic
 361.2GB: boot/vmlinuz-2.6.27-7-generic
 362.1GB: initrd.img
 361.2GB: initrd.img.old
 395.5GB: vmlinuz
 361.2GB: vmlinuz.old

=========================== sda4/boot/grub/menu.lst: ===========================

timeout 10
color black/cyan yellow/cyan
gfxmenu (hd0,3)/boot/gfxmenu
default 0

title linux
kernel (hd0,3)/boot/vmlinuz BOOT_IMAGE=linux root=LABEL=mandriva splash=silent vga=788
initrd (hd0,3)/boot/initrd.img

title linux-nonfb
kernel (hd0,3)/boot/vmlinuz BOOT_IMAGE=linux-nonfb root=LABEL=mandriva 
initrd (hd0,3)/boot/initrd.img

title failsafe
kernel (hd0,3)/boot/vmlinuz BOOT_IMAGE=failsafe root=LABEL=mandriva failsafe
initrd (hd0,3)/boot/initrd.img

title windows
root (hd0,0)
makeactive
chainloader +1

title Ubuntu 8.10
root (hd0,1)
configfile /boot/grub/menu.lst

title 2.6.27-serverrc8-2mnb
kernel (hd0,3)/boot/vmlinuz-2.6.27-server-0.rc8.2mnb BOOT_IMAGE=2.6.27-serverrc8-2mnb root=LABEL=mandriva splash=silent vga=788
initrd (hd0,3)/boot/initrd-2.6.27-server-0.rc8.2mnb.img

title server 2.6.27.19-1mnb
kernel (hd0,3)/boot/vmlinuz-2.6.27.19-server-1mnb BOOT_IMAGE=server_2.6.27.19-1mnb root=LABEL=mandriva splash=silent vga=788
initrd (hd0,3)/boot/initrd-2.6.27.19-server-1mnb.img

=============================== sda4/etc/fstab: ===============================

# Entry for /dev/sda4 :
LABEL=mandriva / ext3 relatime 1 1
/dev/cdrom /media/cdrom auto umask=0,users,iocharset=utf8,noauto,ro,exec 0 0
# Entry for /dev/sdc1 :
LABEL=brick /mnt/brick ntfs-3g defaults 0 0
# Entry for /dev/sda2 :
UUID=a86375d0-c01a-43d1-bab2-16f8e8fa2180 /mnt/kubuntu ext3 relatime 1 2
# Entry for /dev/sdb1 :
LABEL=motherlode /mnt/motherlode ntfs-3g defaults 0 0
# Entry for /dev/sdd1 :
LABEL=tunes /mnt/tunes ntfs-3g defaults 0 0
# Entry for /dev/sda1 :
LABEL=vista /mnt/vista ntfs-3g defaults 0 0
none /proc proc defaults 0 0
# Entry for /dev/sda3 :
UUID=899e0f04-ee10-4c5e-9537-5e192ab4bb6d swap swap defaults 0 0

=================== sda4: Location of files loaded by Grub: ===================


 446.5GB: boot/grub/menu.lst
 446.5GB: boot/grub/stage2
 446.5GB: boot/initrd-2.6.27.19-server-1mnb.img
 446.5GB: boot/initrd-2.6.27-server-0.rc8.2mnb.img
 446.5GB: boot/initrd.img
 446.5GB: boot/initrd-server.img
 446.5GB: boot/vmlinuz
 446.5GB: boot/vmlinuz-2.6.27.19-server-1mnb
 446.5GB: boot/vmlinuz-2.6.27-server-0.rc8.2mnb
 446.5GB: boot/vmlinuz-server

```

---

### Post by davideotape on 2009-04-08
Try adding changing the number on the ubuntu entry as highlighted below:

```
timeout 10
color black/cyan yellow/cyan
gfxmenu (hd0,3)/boot/gfxmenu
default 0

title linux
kernel (hd0,3)/boot/vmlinuz BOOT_IMAGE=linux root=LABEL=mandriva splash=silent vga=788
initrd (hd0,3)/boot/initrd.img

title linux-nonfb
kernel (hd0,3)/boot/vmlinuz BOOT_IMAGE=linux-nonfb root=LABEL=mandriva
initrd (hd0,3)/boot/initrd.img

title failsafe
kernel (hd0,3)/boot/vmlinuz BOOT_IMAGE=failsafe root=LABEL=mandriva failsafe
initrd (hd0,3)/boot/initrd.img

title windows
root (hd0,0)
makeactive
chainloader +1

title Ubuntu 8.10
root (hd0,[COLOR="Red"]3[/COLOR])
configfile /boot/grub/menu.lst

title 2.6.27-serverrc8-2mnb
kernel (hd0,3)/boot/vmlinuz-2.6.27-server-0.rc8.2mnb BOOT_IMAGE=2.6.27-serverrc8-2mnb root=LABEL=mandriva splash=silent vga=788
initrd (hd0,3)/boot/initrd-2.6.27-server-0.rc8.2mnb.img

title server 2.6.27.19-1mnb
kernel (hd0,3)/boot/vmlinuz-2.6.27.19-server-1mnb BOOT_IMAGE=server_2.6.27.19-1mnb root=LABEL=mandriva splash=silent vga=788
initrd (hd0,3)/boot/initrd-2.6.27.19-server-1mnb.img
```

---

### Post by pedrogent on 2009-04-08
OK, I've done this but still no luck.

(I can still boot into the other two mind you.)

Ah yes, the joys of multi-booting!

---

### Post by 3rag0n on 2009-04-08
> **pedrogent said:**
> OK, I've done this but still no luck.

(I can still boot into the other two mind you.)

Ah yes, the joys of multi-booting!

'sfar as i remember, mandriva 2009.0 kde4 One edition had a utility for editing grub in its control center.... in case u dont want to risk corrupting the file via manual editing, try that utility.. add the sda2 for kubuntu in the grub menu...:S

---

### Post by pedrogent on 2009-04-08
> **3rag0n said:**
> 'sfar as i remember, mandriva 2009.0 kde4 One edition had a utility for editing grub in its control center.... in case u dont want to risk corrupting the file via manual editing, try that utility.. add the sda2 for kubuntu in the grub menu...:S

I have the Free edition. Does this mean I have to download the One edition?

---

### Post by 3rag0n on 2009-04-08
> **pedrogent said:**
> I have the Free edition. Does this mean I have to download the One edition?

I dont think so... the free edition is a superset of the One... barring the proprietary stuff... so possibly the grub editing module is in ur control center.:lolflag:

---

### Post by pedrogent on 2009-04-08
> **3rag0n said:**
> I dont think so... the free edition is a superset of the One... barring the proprietary stuff... so possibly the grub editing module is in ur control center.:lolflag:

OK, I've done as you suggest but it still doesn't work. I can still boot into the other two.

Any other takers?

---

### Post by davideotape on 2009-04-09
Sorry, got the wrong hard drive. Try changing that 3 to a 1, as highlighted below:


```
timeout 10
color black/cyan yellow/cyan
gfxmenu (hd0,3)/boot/gfxmenu
default 0

title linux
kernel (hd0,3)/boot/vmlinuz BOOT_IMAGE=linux root=LABEL=mandriva splash=silent vga=788
initrd (hd0,3)/boot/initrd.img

title linux-nonfb
kernel (hd0,3)/boot/vmlinuz BOOT_IMAGE=linux-nonfb root=LABEL=mandriva
initrd (hd0,3)/boot/initrd.img

title failsafe
kernel (hd0,3)/boot/vmlinuz BOOT_IMAGE=failsafe root=LABEL=mandriva failsafe
initrd (hd0,3)/boot/initrd.img

title windows
root (hd0,0)
makeactive
chainloader +1

title Ubuntu 8.10
root (hd0,[COLOR="Red"]1[/COLOR])
configfile /boot/grub/menu.lst

title 2.6.27-serverrc8-2mnb
kernel (hd0,3)/boot/vmlinuz-2.6.27-server-0.rc8.2mnb BOOT_IMAGE=2.6.27-serverrc8-2mnb root=LABEL=mandriva splash=silent vga=788
initrd (hd0,3)/boot/initrd-2.6.27-server-0.rc8.2mnb.img

title server 2.6.27.19-1mnb
kernel (hd0,3)/boot/vmlinuz-2.6.27.19-server-1mnb BOOT_IMAGE=server_2.6.27.19-1mnb root=LABEL=mandriva splash=silent vga=788
initrd (hd0,3)/boot/initrd-2.6.27.19-server-1mnb.img
```

---

### Post by pedrogent on 2009-04-09
But that's what it was before! (I.e I changed it to 3 from 1 and now you want me to change it back to 1 from 3.)

Or am I missing something?

BTW, this is how things currently stand:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #4 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc
 => Grub0.97 is installed in the MBR of /dev/sdd and looks on boot drive #2 in 
    partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Mandriva Linux release 2009.0 
                       (Official) for x86_64 Kernel 2.6.27.19-server-1mnb on 
                       a Dual-processor x86_64 /
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb1: _________________________________________________________________________

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

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500106780160 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976771055 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000e106e

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   705,460,215   705,458,168   7 HPFS/NTFS
/dev/sda2         705,462,345   837,195,344   131,733,000  83 Linux
/dev/sda3         968,928,345   976,768,064     7,839,720  82 Linux swap / Solaris
/dev/sda4         837,195,345   968,928,344   131,733,000  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 640.1 GB, 640133946880 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250261615 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0004552d

Partition  Boot         Start           End          Size  Id System

/dev/sdb1              16,065 1,250,258,624 1,250,242,560   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 320.0 GB, 320071851520 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625140335 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000780fc

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               2,048   625,137,663   625,135,616   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 500.1 GB, 500106780160 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976771055 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000a3325

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *         16,065   976,768,064   976,752,000   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="749236D892369F14" LABEL="vista" TYPE="ntfs" 
/dev/sda2: LABEL="kubuntu" UUID="a86375d0-c01a-43d1-bab2-16f8e8fa2180" TYPE="ext3" 
/dev/sda3: TYPE="swap" UUID="899e0f04-ee10-4c5e-9537-5e192ab4bb6d" 
/dev/sda4: LABEL="mandriva" UUID="5d34779a-802d-45c4-b623-289abae9b710" TYPE="ext3" 
/dev/sdb1: UUID="5D5AB0864C4975A7" LABEL="motherlode" TYPE="ntfs" 
/dev/sdc1: UUID="6E7478167477DEF1" LABEL="brick" TYPE="ntfs" 
/dev/sdd1: UUID="3629E3943D68E98B" LABEL="tunes" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda4 on / type ext3 (rw,relatime)
none on /proc type proc (rw)
/dev/sdc1 on /mnt/brick type fuseblk (rw,allow_other,blksize=4096)
/dev/sda2 on /mnt/kubuntu type ext3 (rw,relatime)
/dev/sdb1 on /mnt/motherlode type fuseblk (rw,allow_other,blksize=4096)
/dev/sdd1 on /mnt/tunes type fuseblk (rw,allow_other,blksize=4096)
/dev/sda1 on /mnt/vista type fuseblk (rw,allow_other,blksize=4096)
none on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)


=========================== sda2/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=a86375d0-c01a-43d1-bab2-16f8e8fa2180 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=a86375d0-c01a-43d1-bab2-16f8e8fa2180

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
uuid		a86375d0-c01a-43d1-bab2-16f8e8fa2180
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=a86375d0-c01a-43d1-bab2-16f8e8fa2180 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		a86375d0-c01a-43d1-bab2-16f8e8fa2180
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=a86375d0-c01a-43d1-bab2-16f8e8fa2180 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		a86375d0-c01a-43d1-bab2-16f8e8fa2180
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=a86375d0-c01a-43d1-bab2-16f8e8fa2180 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		a86375d0-c01a-43d1-bab2-16f8e8fa2180
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=a86375d0-c01a-43d1-bab2-16f8e8fa2180 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		a86375d0-c01a-43d1-bab2-16f8e8fa2180
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Teh BOLDNESS:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=a86375d0-c01a-43d1-bab2-16f8e8fa2180 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdc1
UUID=3629E3943D68E98B /media/music    ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb1
UUID=5D5AB0864C4975A7 /media/storage  ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda1
UUID=749236D892369F14 /media/vista    ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda3
UUID=899e0f04-ee10-4c5e-9537-5e192ab4bb6d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda2: Location of files loaded by Grub: ===================


 361.2GB: boot/grub/menu.lst
 361.2GB: boot/grub/stage2
 362.1GB: boot/initrd.img-2.6.27-11-generic
 361.2GB: boot/initrd.img-2.6.27-7-generic
 395.5GB: boot/vmlinuz-2.6.27-11-generic
 361.2GB: boot/vmlinuz-2.6.27-7-generic
 362.1GB: initrd.img
 361.2GB: initrd.img.old
 395.5GB: vmlinuz
 361.2GB: vmlinuz.old

=========================== sda4/boot/grub/menu.lst: ===========================

timeout 10
color black/cyan yellow/cyan
gfxmenu (hd0,3)/boot/gfxmenu
default 0

title linux
kernel (hd0,3)/boot/vmlinuz BOOT_IMAGE=linux root=LABEL=mandriva splash=silent vga=788
initrd (hd0,3)/boot/initrd.img

title linux-nonfb
kernel (hd0,3)/boot/vmlinuz BOOT_IMAGE=linux-nonfb root=LABEL=mandriva 
initrd (hd0,3)/boot/initrd.img

title failsafe
kernel (hd0,3)/boot/vmlinuz BOOT_IMAGE=failsafe root=LABEL=mandriva failsafe
initrd (hd0,3)/boot/initrd.img

title windows
root (hd0,0)
makeactive
chainloader +1

title Ubuntu 8.10
root (hd0,1)
configfile /boot/grub/menu.lst

title 2.6.27-serverrc8-2mnb
kernel (hd0,3)/boot/vmlinuz-2.6.27-server-0.rc8.2mnb BOOT_IMAGE=2.6.27-serverrc8-2mnb root=LABEL=mandriva splash=silent vga=788
initrd (hd0,3)/boot/initrd-2.6.27-server-0.rc8.2mnb.img

title server 2.6.27.19-1mnb
kernel (hd0,3)/boot/vmlinuz-2.6.27.19-server-1mnb BOOT_IMAGE=server_2.6.27.19-1mnb root=LABEL=mandriva splash=silent vga=788
initrd (hd0,3)/boot/initrd-2.6.27.19-server-1mnb.img

=============================== sda4/etc/fstab: ===============================

# Entry for /dev/sda4 :
LABEL=mandriva / ext3 						relatime 					1 1
/dev/cdrom /media/cdrom auto 					umask=0,users,iocharset=utf8,noauto,ro,exec 	0 0

# Entry for /dev/sdc1 :
LABEL=brick /mnt/brick ntfs-3g 					defaults 					0 0

# Entry for /dev/sda2 :
UUID=a86375d0-c01a-43d1-bab2-16f8e8fa2180 /mnt/kubuntu ext3 	relatime 					1 2

# Entry for /dev/sdb1 :
LABEL=motherlode /mnt/motherlode ntfs-3g 			defaults 					0 0

# Entry for /dev/sdd1 :
LABEL=tunes /mnt/tunes ntfs-3g 					defaults 					0 0

# Entry for /dev/sda1 :
LABEL=vista /mnt/vista ntfs-3g 					defaults 					0 0

# Mysterious "procs"
none /proc proc 						defaults 					0 0

# Entry for /dev/sda3 :
UUID=899e0f04-ee10-4c5e-9537-5e192ab4bb6d swap swap 		defaults 					0 0

=================== sda4: Location of files loaded by Grub: ===================


 446.5GB: boot/grub/menu.lst
 446.5GB: boot/grub/stage2
 446.5GB: boot/initrd-2.6.27.19-server-1mnb.img
 446.5GB: boot/initrd-2.6.27-server-0.rc8.2mnb.img
 446.5GB: boot/initrd.img
 446.5GB: boot/initrd-server.img
 446.5GB: boot/vmlinuz
 446.5GB: boot/vmlinuz-2.6.27.19-server-1mnb
 446.5GB: boot/vmlinuz-2.6.27-server-0.rc8.2mnb
 446.5GB: boot/vmlinuz-server

```

This allows me to boot into both Vista and Mandriva.

---

### Post by pedrogent on 2009-04-10
So does this mean there's no easily correctable problem here and that I have to re-inatall Kubuntu?

I really hope that's not the case...

---

