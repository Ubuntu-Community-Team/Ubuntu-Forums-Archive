---
title: "grub stage1.5 error2 pata with sata issues"
date: 2009-05-07
forum: Installation &amp; Upgrades
---

### Post by phazei on 2009-05-07
My g/f hosed my hardy install (no more admin for her), so I was doing a reinstall, but grub is having issues.  When I installed it the first time, I had windows on it, I wiped that a while ago.

After grub failed with hardy I went with Jaunty and had the same problem.

I've googled all over and found this solution:
[http://gnuski.blogspot.com/2009/04/grub-stage-15-error-2-howto-fix.html]("http://gnuski.blogspot.com/2009/04/grub-stage-15-error-2-howto-fix.html")
But I don't want to go with it.

In ubuntu it's showing my drives as sda, sdb, sdc.  SDC is my pata, the other are sata.  My mobo, ASUS A7V8X, was one of the first with sata, and doesn't have many options for it in the bios.  It cannot boot off of them, only PATA.  I installed 9.4 on SDA.  Which I'm guessing grub is seeing as hd0.  It starts to load grub, but then I get stage1.5 error2.

What to do?  At boot something isn't quite in the right order...

Thanks

---

### Post by caljohnsmith on 2009-05-07
I think it would help to first get a clearer picture of your setup related to your booting problem, so how about downloading the **Boot Info Script** to your Ubuntu desktop (can be the Live CD):

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

John

---

### Post by phazei on 2009-05-07
I have since installed 9.4 on SDC1 as well.  So it's on both SDC1 and SDA1, but grub still fails.  Here is that results.txt file:

```



============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #3 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => Grub0.97 is installed in the MBR of /dev/sdc and looks on boot drive #3 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

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

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda8 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb8 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdc2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xfcec1fbd

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    51,167,024    51,166,962  83 Linux
/dev/sda2          55,167,210   137,901,959    82,734,750  83 Linux
/dev/sda3         137,901,960   976,768,064   838,866,105   f W95 Ext d (LBA)
/dev/sda5         137,902,023   347,614,469   209,712,447   7 HPFS/NTFS
/dev/sda6         347,614,533   557,326,979   209,712,447   7 HPFS/NTFS
/dev/sda7         557,327,043   767,039,489   209,712,447   7 HPFS/NTFS
/dev/sda8         767,039,553   976,768,064   209,728,512   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders, total 586114704 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc562ec8c

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   125,837,144   125,837,082   7 HPFS/NTFS
/dev/sdb2         125,837,145   586,099,394   460,262,250   f W95 Ext d (LBA)
/dev/sdb5         125,837,208   251,674,289   125,837,082   7 HPFS/NTFS
/dev/sdb6         251,674,353   377,511,434   125,837,082   7 HPFS/NTFS
/dev/sdb7         377,511,498   503,348,579   125,837,082   7 HPFS/NTFS
/dev/sdb8         503,348,643   586,099,394    82,750,752   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders, total 120103200 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x017a0179

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63    52,436,159    52,436,097  83 Linux
/dev/sdc2          52,436,160    62,910,539    10,474,380  83 Linux
/dev/sdc3          62,910,540    67,087,439     4,176,900  82 Linux swap / Solaris
/dev/sdc4          67,087,440   120,101,939    53,014,500   f W95 Ext d (LBA)
/dev/sdc5          67,087,503   120,101,939    53,014,437   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="7cbd86f1-f656-4b7a-875e-26a893a8e300" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="DE5C63BE5C638FD7" LABEL="LD3 1 Media" TYPE="ntfs" 
/dev/sda6: UUID="E2EC6E36EC6E055F" LABEL="LD3 2 Media" TYPE="ntfs" 
/dev/sda7: UUID="86E473F5E473E5B9" LABEL="LD3 3 Data" TYPE="ntfs" 
/dev/sda8: UUID="9E107A4F107A2F01" LABEL="LD3 4 Work" TYPE="ntfs" 
/dev/sdb1: UUID="B8A80137A800F5A2" LABEL="LD2 Movies" TYPE="ntfs" 
/dev/sdb5: UUID="08E02701E026F51A" LABEL="LD2 Anime" TYPE="ntfs" 
/dev/sdb6: UUID="E2204D13204CEFD9" LABEL="LD2 Mp3" TYPE="ntfs" 
/dev/sdb7: UUID="0630507030506927" LABEL="LD2 TV" TYPE="ntfs" 
/dev/sdb8: UUID="381C54281C53E004" LABEL="LD2 Books" TYPE="ntfs" 
/dev/sdc1: UUID="4935632c-8513-47f6-81ea-f3398cbededd" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc2: UUID="47fdfb33-b5e8-48ef-bc3f-fffc4aadd21f" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc3: UUID="f930ab93-a001-410f-b30b-e02dfe017096" TYPE="swap" 
/dev/sdc5: LABEL="LD1 DATA1" UUID="75F3-5CEA" TYPE="vfat" 

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


=========================== sda1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=7cbd86f1-f656-4b7a-875e-26a893a8e300 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=7cbd86f1-f656-4b7a-875e-26a893a8e300

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

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		7cbd86f1-f656-4b7a-875e-26a893a8e300
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=7cbd86f1-f656-4b7a-875e-26a893a8e300 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		7cbd86f1-f656-4b7a-875e-26a893a8e300
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=7cbd86f1-f656-4b7a-875e-26a893a8e300 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		7cbd86f1-f656-4b7a-875e-26a893a8e300
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=7cbd86f1-f656-4b7a-875e-26a893a8e300 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda4 during installation
UUID=5777f1ba-d907-461b-9d7b-addbf62d8a76 none            swap    sw              0       0
# swap was on /dev/sdc3 during installation
UUID=f930ab93-a001-410f-b30b-e02dfe017096 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


   5.7GB: boot/grub/menu.lst
   5.6GB: boot/grub/stage2
   5.1GB: boot/initrd.img-2.6.28-11-generic
   5.1GB: boot/vmlinuz-2.6.28-11-generic
   5.1GB: initrd.img
   5.1GB: vmlinuz

=========================== sdc1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=4935632c-8513-47f6-81ea-f3398cbededd ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=4935632c-8513-47f6-81ea-f3398cbededd

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

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		4935632c-8513-47f6-81ea-f3398cbededd
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=4935632c-8513-47f6-81ea-f3398cbededd ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		4935632c-8513-47f6-81ea-f3398cbededd
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=4935632c-8513-47f6-81ea-f3398cbededd ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		4935632c-8513-47f6-81ea-f3398cbededd
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=7cbd86f1-f656-4b7a-875e-26a893a8e300 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=7cbd86f1-f656-4b7a-875e-26a893a8e300 ro single 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, memtest86+ (on /dev/sda1)
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot


=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdc1 during installation
UUID=4935632c-8513-47f6-81ea-f3398cbededd /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdc3 during installation
UUID=f930ab93-a001-410f-b30b-e02dfe017096 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdc1: Location of files loaded by Grub: ===================


  21.6GB: boot/grub/menu.lst
  21.7GB: boot/grub/stage2
  21.6GB: boot/initrd.img-2.6.28-11-generic
  21.7GB: boot/vmlinuz-2.6.28-11-generic
  21.6GB: initrd.img
  21.7GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdc5

00000000  eb 3c 90 4d 53 57 49 4e  34 2e 31 00 02 10 24 00  |.<.MSWIN4.1...$.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 8f ac ff 03  |........?.......|
00000020  a5 ef 28 03 12 65 00 00  00 00 00 00 85 02 00 00  |..(..e..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 ea 5c f3 75 4e  4f 20 4e 41 4d 45 20 20  |..).\.uNO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 f6 f6 f6 f6 f6 f6  |  FAT32   ......|
00000060  f6 f6 f6 f6 f6 f6 f6 f6  f6 f6 f6 f6 f6 f6 f6 f6  |................|
*
000001f0  f6 f6 f6 f6 f6 f6 f6 f6  f6 f6 f6 f6 00 00 55 aa  |..............U.|
00000200





```

---

### Post by phazei on 2009-05-07
I have grub on 2 of the drives. I wanted to remove it from one but couldn't find anything but a way to replace it with the windows boot loader.  When I run grub on cli, how does it know which one to change?
I tried doing a "setup (hd0)" and it just said something about innaccessable drive.  Also, I've tried "root (hd0,1)" and "root (hd2,1)" but if I run that script afterwards, it doesn't change what it says at the top about "looks on boot drive #3 in partition #1"
Maybe it needs to be rebooted for that to take affect?  And I'm thinking if SDC is shown as the first drive, then SDA would probably be the second, not the third...
I'm going to try "root (hd1,1)" and reboot now.

---

### Post by caljohnsmith on 2009-05-07
How about trying this:
```
sudo grub
grub> root (hd0,0)
grub> setup (hd0)
grub> quit
```
Then reboot, make sure to set your 500 GB sda drive to boot first in your BIOS boot order, and then if all goes well you should get the Grub menu on start up if you press "ESC". Let me know how that goes or if you run into problems.

John

---

### Post by phazei on 2009-05-07
I set my boot order to CD,'SCSI/Onboard SATA Device', hard disk. And typed those commands successfully.

The bios doesn't actually show the SATA disks anywhere in it.  The only time I get to see them is when I see the FastTrak376 utility load during boot.

When set that way the system boots and then just says "Press a key to reboot" as if there were no drives.  I don't think it can boot off the sata.

It needs to boot off PATA and then look for the sata.


The only way to get the system to use individual sata drives is to set each drive up as a single disk raid 0.  It's had no problems with that since I got it and I've had Ubuntu on it for a couple years, but when it was originally installed, windows was on the PATA drive.

---

### Post by caljohnsmith on 2009-05-07
OK, if you can only boot from your 61 GB sdc PATA drive, how about trying this:
```
sudo grub
grub> root (hd2,0)
grub> setup (hd2)
grub> quit
```
Then make sure the 61 GB sdc drive is first in the BIOS boot order (I think that would mean putting "hard disk" before "SCSI/Onbord ATA Device"). Let me know how that goes or if you run into problems.

John

---

### Post by phazei on 2009-05-07
Ok, that worked.  While testing I didn't realize that after typing root () that I had to do setup () to save it there afterwards.

So after I typed root (hd2,0), setup (hd2) it booted off of the install on sdc, the pata drive, on boot grub said "Booting from hd0,0".  Seems I didn't need to do the translation, it did it for me.  I set it to (hd2,0) and it knew that at boot that was actually (hd0,0) at that time.

But I wanted to use the one installed on SDA, the sata drive.  So I went into grub again and typed:
```

root (hd0,0)
setup (hd2)
quit

```

It worked, read the MBR from SDC, and the /boot from SDA.  When it was booting it said "Booting from hd2,0".

So durring boot:
hd0 = pata
hd1 = sata 300gb
hd2 = sata 500gb

And after boot:
hd0 = sda = sata 500gb
hd1 = sdb = sata 300gb
hd2 = sdc = pata


That's odd.  Why does that happen?

The order durring boot makes sense, it loads the pata first, then it loads the fasttrak bios which loads the 300gb (which is set to primary, there's a little star next to it and it's listed first in FastTrak) and the 500gb last.


Then once loaded the drives are all handled by liata, which I could see it loading the sata drives before the pata, but even then, why doesn't it load the 300gb first?

It is all working now though.

Many thanks.

---

### Post by vertix on 2009-05-10
> **caljohnsmith said:**
> OK, if you can only boot from your 61 GB sdc PATA drive, how about trying this:
```
sudo grub
grub> root (hd2,0)
grub> setup (hd2)
grub> quit
```Then make sure the 61 GB sdc drive is first in the BIOS boot order (I think that would mean putting "hard disk" before "SCSI/Onbord ATA Device"). Let me know how that goes or if you run into problems.

John

I have a very similar problem, but my situation is different.
 It still does not work in my case.

What I have is a 2 drive box with 1 IDE and 1 SCSI drive.
There is a separate /boot partition on each drive as 1st
drive partition to avoid BIOS 1440 cylinder limitation problem.

There is an old Red Hat Linux on IDE drive
and I recently installed ubuntu on SCSI drive.
I did not have a chance to  work with ubuntu installation much.
But I recall correctly, i was able to boot it OK at least once after
initial install.

It is a dual boot system. And there are 2 potential difficulties:

1) It has a mix of IDE and SCSI drives.

2) The root partitions are located at the end of the drive
    (well past cylinders 1440, which is an old BIOS limitation
    affecting some boot loaders). This is the reason, the
    partition 1 on both drives has been specifically reserved
    for /boot partition, so we don't have a large cylinder number
    limitation.

Unfortunately, I had to reinstall Win XP and overwrote the grub.
It would not be a bad idea for Ubuntu to make a backup of both
MBR and anything it modifies during the install process and add
a choice on Live CD to search and restore either the original
MBR (from previous Windows installation for example), or from
its own modifications during the install, in case it gets overwritten
by the Windows being installed on the same drive after Linux was
installed on it.

When I tried to recover my grub, no matter what I did, nothing worked.
I did create several versions of grub, one of them on floppy, having
Stage 1 and Stage 2 files written on it by dd outside of file system
by direct writing to disk sectors. That one loads stage 1 and stage 2
with no problems. And it finds the kernel and kernel starts booting.
But then it panics because it can not mount the root filesystem
even though it is clean and supberblock is in a good shape.

I was even willing to do a fresh install of ubuntu, but there is a problem
with partitioning. It initially suggested I repartition one of my drives and
gave some suggestion on how to change my existing partitions and
that is the LAST thing in the world I'd want to do right now is to change
the partitions.

My box was infected with rootkit under Windows and I had huge amounts
of data I need to try to save before I have to wipe the drive off clean,
which is about the only realistic solution for rootkit issue, and even
that one is not guaranteed to clean your box.

So, the first thing I needed to do is to boot linux and save my data.
Changing partitions and possibly loosing all my data is about the
worstest of the worst scenarios.

But there is a problem with Ubuntu partitioning stage.
It does not give you a choice to keep your existing partitions.
It does give you "manual partitioning" option. But it can not be
trusted because once you click the "manual partition", the
drive you are going to install the Linux on, will be shown as
empty in a horizontal bar at the top of partitioning window.

When you select manual paritioning, the lower colored horisontal bar,
showing partitions on drive 2, turns all blue (meaning the entire disk
will be allocated to a single ubuntu partition), and that is the LAST
thing I would want to do. This is not right design for "manual
partitioning" choice. That bar should not change at all. Because
no decision as to how are you going to partition the drive has
been made at that point. So, what is the point of changing the
graphical representation of that drive before you even know how
it is going to be changed?

I tried to allow it to go to the next stage by pushing -> button.
But even at that stage, I was not sure the partition would not
be changed to what ubuntu suggested at some later stage,
and you can't take ANY risks in the situation I am in.
Because once you are at partitioning stage on a existing
installation it is like walking on a mine field. Just one "wrong"
button push, and you lost your drive.

So, beware! If you ever get to partitioning stage, better
stop it right there if you did not save your MBR and superblock,
cause the way that grub thing works, it can make you suffer
for weeks! Why nobody ever thought of making this stoopid
grub thing any more intelligent and make precautionary
backups if it EVER modifies ANYTHING?

People do not even suspect they are stepping into the
mine field zone. Most of them simply want their linux back
up and quick at that, and the quicker they want it, the more
likelihood they are going to have it in the longest way
imaginable.

Why?

Who wrote such a screwed up grub?
You should be ashamed of it. YEARS have passed since
it was written, and to this day, it causes more problems for
more people than anything else on any linux release.

So, I could not take a chance and let it repartition my drive.
Cause I have seen way too many screwups in Linux world,
some of which I could not even imagine in my wildest dreams.

But the bottom line is that no matter what I did, changing drives
around, changing location of grub (partition 1 on each drive),
MBR, or even root partition, it would still crash.

The kernel is getting loaded. But at the moment it tries the root
file system, it produces this error:
(last 4 lines of boot sequence)

[1.536064] RAMDISK: Compressed image found at block 0.

[1.959688] crc error
(CRC error on what?
Anybody knows what CRC error they are talking about?)

[2.023879] VFS: Cannot open root device "sdb8" or unknown block (0,0)
(Why can't you open it if it is a clean file system
and it is in correct place, just as Live CD reports?
Why not tell the EXACT reason you could not open it?
Was there a bad magic number or whatever?)

[2.239447] Please append a correct "root=" boot option; here are available partitions:
(This IS a correct root option!)

[2.024051] Kernel panic - not syncing; VFS: unable to mount root fs on unknown-block (o,o)

I am beginning to think that device driver for SCSI isn't yet loaded
when root partition is attempted to be mounted, for some strange
reason. It does not make much sense. Because they wouln't
mount a partition before the drivers are loaded. But who knows,
may be the driver is somehow missing or something of the sorts.

Because the root partition is clean and superblock is restored
from one of the oldest backups, and so is MBR.

Also, I tried to put grub on root partition. I recall seeing it somewhere.
But not sure if this helps anything. But it prolly wipes out the superblock
alright!

:--}

Luckily, you can restore those from backups
(see Restoring damaged superblock at the end of this article).
 
In my case, the root partition is partition 8 on the SCSI drive.
Because ubuntu was installed after existing windows installation
and ended up at the end of drive. I know, performance is less
on the outer tracks of the drive, but that is not the issue at the
moment.

I have spent days, trying to get my box working. I can not
boot from Windows. Because my windows installation got
infected with rootkit virus. (See details at the end).

The rootkit virus progressed to such an extent, that I have
reasons to suspect it has control of the BIOS or at least some
drivers. Because even wiping my Windows partition and
reinstalling windows fresh from well known good CD and
trying to install antivirus, it immediately detected 7 errors
on preliminary virus check. So I had to shutdown quickly before
too much damage is being done.

Looks like this rootkit virus has infected a huge number of machines
in the world. And many people have it without even realizing it.
All they notice is their machine is getting slow and disk activity
looks busier than it outht to be. But their machine became one
of the proxy servers and is pumping ALL sorts of most
destructive and even criminal activity without them even knowing it.

I wrote my own monitoring firewall program for Windows
and I can't use any box unless it is installed on it. Because it allows
me to see every packet, suspicious or not, and with a single mouse
click I can see anything I want as far as net traffic goes.
Also, any packet that ends up being shown in the monitor window,
which is ANY suspicious packet, is automatically logged.
And logs are kept for as long as you like. It could be years
of logging of every suspicious packet, which really helps
nowadays. Because one of these days, sooner or later,
you will realize your box has been hacked or even rooted.
Then you can look at what is happening now and then
look up your logs and see when exactly it started.
Rootkit has no means to prevent you from logging its
activity. It can not intercept your logs. You can simply
verify them by opening a current log on a hot system
and see if it contains the right packets logged :--}

So, I looged the entire global network of rootkit machines.
Unfortunately, I asked about rootkit infection on IRC #linux channel
and once those lil fools knew that my machine was infected, one
of them prolly triggeed a destructive phase of rootkit toolbox, and
my anti-rootkit scan did show some significant discrepancies in
the shown and hidden files, registry entries, etc. and of large
enough size to save the small operating system in.

So, all they had to do is to dial my IP and push a single button
and my machine would start self-destruction sequence.
One of them even asked me: Did it start self-destructing?
Lil did he know that he was being logged also... :--}

Sure, I am just guessing why this rootkit just suddenly exploded.
It was relatively dormant before. Just trying to pump some traffic
thru my machine and trying to install new viruses, as they all do.

Because I have been watching it on my machine for at least a week
and blocking all the hosts to which it tries to communicate, informing
them of my infected machine, and all the incoming connection
attempts. Apparently, I did not even suspect they use remote
port 80, used by any web browser, and so I loosened that rule
at some point, which was a bad idea. Normally, I keep even port
80 blocked, or rather in a prompted mode. When my machine
wants to go out to some web page, I get a prompt dialong, and
can push a single button to allow it, which is the best strategy.
But then you get lazy to push a single button and say: hey,
what the heck. If I do a lot of browsing, there is just too many
times I have to push "Allow This Session Only" button...

And then...
Booooom!!!

The way it behaves in my case, is to send a UDP packet on port 80,
which no firewall would block as all of them allow remote port 80
by default, which exposes your machine to the most lethal virus
you can even imagine in your wildest dreams, and you simply have
no clue that your machine is infected. Nowadays, people keep
downloading all sorts of things without even thinking about what
could happen to their machine. And what prevents someone
from packing some virus into one of thos programs? How do you
know that the site you have visited is the real site and not a setup?

Fortunately, in my case, they would send this udp packet every
5 minutes, down to 20 second interval. So you could predict when
next broadcast would run.

But once the self-destruction sequence was triggered, the disk
activity would go to stratospheric levels even without being
connected to network or Internet. At that point, I had to completely
abandon usnig windows and I doublt I have a chance to use it
on this box no matter what I do. Even if I throw this drive away,
there is no guarantee that it will help anything as my study shows.

I am still amazed I have all the data on my drives and can
see all the partitions. But now I have all the most important
things backed up, including the MBR, partition tables and
you name it, including years worth of Interceptor logs.
Those logs worth in gold now!

Watch out, you stoopid hacksters, conmen and perverts.
Once you step on my toe, I get REALLY upset. Especially,
if you made me suffer for a week like you did it this time.

Better share really good now!
Cause I bet you are worth 5-7 years in jail EASY.
And your tracks are all over the world.
Down to millisecond level, if not better.

:--}

Look at the end of this post to see some hosts you'd better keep
in your firewall rules, especially remote port 80 and incoming
ICMP type 4 and File Sharing UDP (local and remote ports 137-139).

Anyway, back to ubuntu boot problem...

Here is my RESULTS.txt after running bootinfo.sh from
[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Hopefully, someone will be able to see the problem
before I do, cause I am kinda getting fed up with this
and can not believe my eyes that I can not boot my own
box for so long using the hottest Linux release.

You, developers, are screwed up, and screwed up REALLY
good. Because you make so many people suffer, and
unnecessarily, that you deserve a seat next to those
rootkit bozos.

You see, software engineering is an art form. It it not just
some dumb hacking procedure. Unless your software has
beauty, it is crap.

If one has to suffer for days to do the simpliest thing
imaginable, to install something, then what are you worth?

You mean you can not manage to find a place to make
a backup of what you are about to wipe out?
Does it take THAT much brain to figure it out?
You mean you can not make a backup of the thing
that can wipe YOU out in case someone installs Windows
after installing Linux without even suspecting he is going
to spend days, trying to fix it?

What IS the problem here?
Why can't you make it work like a clock?
Why can't you install and deinstall anything by simply
pushing a single button in most cases, just like it is
on windows for many programs?

You make this grub thing look like some kind ol particle
science, which is just a joke and a bad one at that.
If some software engineer has to spend days on really
understanding this stoopid lil thing, then what?
Well, then you are screwed up in your brain and your
"holier than thou" image isn't wort a piece of paper it
is written upon.

Anyway, I wonder if someone has some idea about this
grub issue I am struggling here with, wasting days, and
getting nowhere fast.

```

======================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #8 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #8 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst /grub/grub.conf

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda2 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda2 starts at sector 257103.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  According to the info in the boot sector, sda8 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  According to the info in the boot sector, sda9 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda10: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda11: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.95 is installed in the boot sector of sda11 and 
                       looks at sector 116639306 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #11 for 
                       /boot/grub/grub.conf.
    Operating System:  Red Hat Enterprise Linux AS 
                       release 4 (Nahant) Kernel on an
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.conf /etc/fstab

sda12: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda13: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst

sdb2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /BOOT.INI /ntldr /NTLDR /NTDETECT.COM 
                       /ntdetect.com

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb7: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb8: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sdb8 and 
                       looks at sector 264821940 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sdb. Stage2 looks on partition #8 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda11: _____Repeated for comparison.___________________________________________
(This one boots fine with Red Hat.
Looks exactly the same as non-working /dev/sdb8)

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.95 is installed in the boot sector of sda11 and 
                       looks at sector 116639306 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #11 for 
                       /boot/grub/grub.conf.
    Operating System:  Red Hat Enterprise Linux AS 
                       release 4 (Nahant) Kernel on an
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.conf /etc/fstab

sdb9: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb10: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 61.4 GB, 61471162368 bytes
255 heads, 63 sectors/track, 7473 cylinders, total 120060864 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0d670d66

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       257,039       256,977  83 Linux
/dev/sda2    *        257,103    23,760,134    23,503,032   c W95 FAT32 (LBA)
/dev/sda3          23,760,135   120,053,744    96,293,610   f W95 Ext d (LBA)
/dev/sda5          23,760,198    40,291,019    16,530,822   b W95 FAT32
/dev/sda6          40,291,083    62,701,694    22,410,612   b W95 FAT32
/dev/sda7          62,701,758    75,650,084    12,948,327   b W95 FAT32
/dev/sda8          75,650,148    88,309,304    12,659,157   b W95 FAT32
/dev/sda9          88,309,368   105,049,034    16,739,667   b W95 FAT32
/dev/sda10        105,049,098   108,776,114     3,727,017   b W95 FAT32
/dev/sda11        108,776,178   118,591,829     9,815,652  83 Linux
/dev/sda12        118,591,893   119,105,909       514,017  83 Linux
/dev/sda13        119,105,973   120,053,744       947,772  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd871d871

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63       257,039       256,977  83 Linux
/dev/sdb2             257,040    39,327,119    39,070,080   b W95 FAT32
/dev/sdb3          39,327,120   312,576,704   273,249,585   5 Extended
/dev/sdb5          39,327,183   117,451,214    78,124,032   b W95 FAT32
/dev/sdb6         117,451,278   195,575,309    78,124,032   b W95 FAT32
/dev/sdb7         195,575,373   254,164,364    58,588,992   b W95 FAT32
/dev/sdb8         254,164,428   293,234,444    39,070,017  83 Linux
/dev/sdb9         293,234,508   304,945,829    11,711,322  83 Linux
/dev/sdb10        304,945,893   312,576,704     7,630,812  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: LABEL="boot" UUID="fb479a4c-35ed-4b9d-8448-775ac86a23ed" TYPE="ext2" 
/dev/sda2: UUID="4A06-74D0" TYPE="vfat" 
/dev/sda5: LABEL="OLD_D" UUID="15ED-3119" TYPE="vfat" 
/dev/sda6: LABEL="OLD_E" UUID="50A1-9896" TYPE="vfat" 
/dev/sda7: LABEL="OLD_F" UUID="3C3F-8655" TYPE="vfat" 
/dev/sda8: LABEL="OLD_G" UUID="3C3F-8931" TYPE="vfat" 
/dev/sda9: LABEL="OLD_H" UUID="4554-7589" TYPE="vfat" 
/dev/sda10: LABEL="OLD_I_W2K" UUID="469A-CDF9" TYPE="vfat" 
/dev/sda11: LABEL="/1" UUID="6fa5af9c-c99a-407c-8b39-eb908efdd681" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda12: LABEL="/tmp" UUID="4b3a155e-281d-485c-949a-8e55db94c21f" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda13: TYPE="swap"

/dev/sdb1: UUID="33a1d591-78ed-44a7-8f7d-5c51cc00ca94" TYPE="ext2" 
/dev/sdb2: LABEL="NEW_C" UUID="BE63-7422" TYPE="vfat" 
/dev/sdb5: LABEL="NEW_E" UUID="AEF5-27E5" TYPE="vfat" 
/dev/sdb6: LABEL="NEW_F" UUID="BC09-47F7" TYPE="vfat" 
/dev/sdb7: LABEL="NEW_G" UUID="40E7-4B61" TYPE="vfat" 
/dev/sdb8: LABEL="/1" UUID="aa230e99-2a30-43f9-8f70-8d41f6ca5d83" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb9: LABEL="/tmp" UUID="6cf42f0a-b136-45f7-a41f-2f093ea726b7" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb10: TYPE="swap" 
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
/dev/sda5 on /media/OLD_D type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)


============================= sda1/grub/grub.conf: =============================

# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You do not have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /, eg.
#          root (hd0,9)
#          kernel /boot/vmlinuz-version ro root=/dev/hda10
#          initrd /boot/initrd-version.img
#boot=/dev/hda
#boot=/dev/fd0
root (hd0,10)
boot=/dev/hda
#kernel /boot/vmlinuz-2.6.9-5.EL ro root=/dev/hda10
kernel /boot/linux ro root=/dev/hda11
initrd /boot/initrd-2.6.9-5.EL.img
timeout=30
splashimage=(hd0,9)/boot/grub/splash.xpm.gz
hiddenmenu
title Red Hat Enterprise Linux AS (2.6.9-5.EL)
    root (hd0,10)
    kernel /boot/vmlinuz-2.6.9-5.EL ro root=LABEL=/1 rhgb quiet
    initrd /boot/initrd-2.6.9-5.EL.img
title Windows XP
    root (hd0,1)
    makeactive
    chainloader +1
title Windows XP
    root (hd0,1)
    setup (hd0)
title Windows 2000
    root (hd0,11)
    setup (hd0)
title Other
#    rootnoverify (hd0,1)
    rootnoverify (hd0,10)
    chainloader +1

#drwxr-xr-x  2 root root    4096 Jul 15 02:49 grub
#-rw-r--r--  1 root root  535183 Jul 14 20:22 initrd-2.6.9-5.EL.img
#-rw-r--r--  1 root root   23108 Dec  2  2004 message
#-rw-r--r--  1 root root   21282 Dec  2  2004 message.ja
#-rw-r--r--  1 root root  712698 Jan  6  2005 System.map-2.6.9-5.EL


=================== sda1: Location of files loaded by Grub: ===================


    .0GB: grub/grub.conf
    .0GB: grub/menu.lst
    .0GB: grub/stage2
    .0GB: initrd-2.6.9-5.EL.img
    .0GB: initrd-2.6.9-5.EL.img.orig
    .0GB: vmlinuz
    .0GB: vmlinuz-2.6.9-5.EL

========================== sda11/boot/grub/grub.conf: ==========================

# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You do not have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /, eg.
#          root (hd0,10)
#          kernel /boot/vmlinuz-version ro root=/dev/hda11
#          initrd /boot/initrd-version.img
default=0
#boot=/dev/hda
boot=/dev/fd0
root (hd0,10)
#kernel /boot/vmlinuz-2.6.9-5.EL ro root=/dev/hda10
kernel /boot/linux ro root=/dev/hda11
initrd /boot/initrd-2.6.9-5.EL.img
timeout=5
splashimage=(hd0,10)/boot/grub/splash.xpm.gz
hiddenmenu
title Red Hat Enterprise Linux AS (2.6.9-5.EL)
    root (hd0,10)
    kernel /boot/vmlinuz-2.6.9-5.EL ro root=LABEL=/1 rhgb quiet
    initrd /boot/initrd-2.6.9-5.EL.img
    savedefault
title Windows XP
    root (hd0,1)
    makeactive
    chainloader +1
    savedefault
title Windows XP
    root (hd0,1)
    setup (hd0)
    savedefault
title Windows 2000
    root (hd0,11)
    setup (hd0)
    savedefault
ritle Other
#    rootnoverify (hd0,1)
    rootnoverify (hd0,10)
    chainloader +1
    savedefault


=============================== sda11/etc/fstab: ===============================

# This file is edited by fstab-sync - see 'man fstab-sync' for details
LABEL=/1                /                       ext3    defaults        1 1
#/dev/hda11              /                       ext3    defaults        1 1
#/dev/hda1               /boot                   ext2    defaults        1 1
none                    /dev/pts                devpts  gid=5,mode=620  0 0
none                    /dev/shm                tmpfs   defaults        0 0
none                    /proc                   proc    defaults        0 0
none                    /sys                    sysfs   defaults        0 0
#LABEL=tmp               /tmp                    ext3    defaults        1 2
/dev/hda12              /tmp                    ext3    defaults        1 2
#/dev/fd0        /flop            ext3    defaults    1 2
LABEL=SWAP-hda13        swap                    swap    defaults        0 0
#/dev/hda13        swap                    swap    defaults        0 0


/dev/hda2        /c            auto    defaults    0 0
/dev/hda5        /d            auto    defaults    0 0
/dev/hda6        /e            auto    defaults    0 0
/dev/hda7        /f            auto    defaults    0 0
/dev/hda8        /g            auto    defaults    0 0
/dev/hda9        /h            auto    defaults    0 0
/dev/hda10        /i            auto    defaults    0 0

/dev/hdc                /media/cdrecorder1      auto    pamconsole,fscontext=system_u:object_r:removable_t,exec,noauto,managed 0 0
/dev/fd0                /media/floppy           auto    pamconsole,fscontext=system_u:object_r:removable_t,exec,noauto,managed 0 0

=================== sda11: Location of files loaded by Grub: ===================


  57.1GB: boot/grub/grub.conf
  57.1GB: boot/grub/menu.lst
  59.7GB: boot/grub/stage2
  56.9GB: boot/initrd-2.6.9-5.EL.img
  57.1GB: boot/initrd-2.6.9-5.EL.img.1
  59.4GB: boot/vmlinuz
  56.9GB: boot/vmlinuz-2.6.9-5.EL

============================= sdb1/grub/menu.lst: =============================

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
timeout        30

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
# kopt=root=UUID=aa230e99-2a30-43f9-8f70-8d41f6ca5d83 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=33a1d591-78ed-44a7-8f7d-5c51cc00ca94

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

title        Ubuntu 8.10, kernel Default
uuid        33a1d591-78ed-44a7-8f7d-5c51cc00ca94
kernel        /boot/vmlinuz root=UUID=aa230e99-2a30-43f9-8f70-8d41f6ca5d83 ro quiet splash 
quiet

title        Ubuntu 8.10, kernel Default (recovery mode)
uuid        33a1d591-78ed-44a7-8f7d-5c51cc00ca94
kernel        /boot/vmlinuz root=UUID=aa230e99-2a30-43f9-8f70-8d41f6ca5d83 ro  single

title        Ubuntu 8.10, kernel 2.6.27-7-generic
uuid        33a1d591-78ed-44a7-8f7d-5c51cc00ca94
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=aa230e99-2a30-43f9-8f70-8d41f6ca5d83 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-7-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid        33a1d591-78ed-44a7-8f7d-5c51cc00ca94
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=aa230e99-2a30-43f9-8f70-8d41f6ca5d83 ro  single
initrd        /boot/initrd.img-2.6.27-7-generic

title        Ubuntu 8.10, memtest86+
uuid        33a1d591-78ed-44a7-8f7d-5c51cc00ca94
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda11.
title        Red Hat Enterprise Linux AS release 4 (Nahant) (on /dev/sda11)
root        (hd0,10)
kernel        /boot/linux ro root=/dev/hda11 
initrd        /boot/initrd-2.6.9-5.EL.img
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda11.
title        Red Hat Enterprise Linux AS (2.6.9-5.EL) (on /dev/sda11)
root        (hd0,10)
kernel        /boot/vmlinuz-2.6.9-5.EL ro root=LABEL=/1 rhgb quiet 
initrd        /boot/initrd-2.6.9-5.EL.img
savedefault
boot


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows NT/2000/XP (loader)
root        (hd0,1)
savedefault
makeactive
chainloader    +1


=================== sdb1: Location of files loaded by Grub: ===================


    .1GB: grub/menu.lst
    .1GB: grub/stage2
    .0GB: initrd.img-2.6.27-7-generic
    .0GB: vmlinuz
    .0GB: vmlinuz-2.6.27-7-generic

================================ sdb2/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(1)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(1)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
C:\="Unidentified operating system on drive C."  

================================ sdb2/BOOT.INI: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(1)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(1)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
C:\="Unidentified operating system on drive C."  

=========================== sdb8/boot/grub/menu.lst: ===========================

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
timeout        30

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
# kopt=root=UUID=aa230e99-2a30-43f9-8f70-8d41f6ca5d83 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=33a1d591-78ed-44a7-8f7d-5c51cc00ca94

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

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda11.
#title        Red Hat Enterprise Linux AS release 4 (Nahant) (on /dev/sda11)
#root        (hd0,10)
#kernel        /boot/linux ro root=/dev/hda11 
#initrd        /boot/initrd-2.6.9-5.EL.img
#savedefault
#boot

title        Test 1 - Ubuntu 8.10, kernel 2.6.27-7-generic
#uuid        33a1d591-78ed-44a7-8f7d-5c51cc00ca94
kernel        /boot/vmlinuz-2.6.27-7-generic ro root=/dev/sdb8
#splash 
initrd        /boot/initrd.img-2.6.27-7-generic
quiet

title        Test 2 - Ubuntu 8.10, kernel 2.6.27-7-generic
#uuid        33a1d591-78ed-44a7-8f7d-5c51cc00ca94
root        (hd0,7)
kernel        /boot/vmlinuz-2.6.27-7-generic ro root=/dev/sdb8
#splash 
initrd        /boot/initrd.img-2.6.27-7-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-7-generic
uuid        33a1d591-78ed-44a7-8f7d-5c51cc00ca94
kernel        /vmlinuz-2.6.27-7-generic root=UUID=aa230e99-2a30-43f9-8f70-8d41f6ca5d83 ro quiet splash 
initrd        /initrd.img-2.6.27-7-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid        33a1d591-78ed-44a7-8f7d-5c51cc00ca94
kernel        /vmlinuz-2.6.27-7-generic root=UUID=aa230e99-2a30-43f9-8f70-8d41f6ca5d83 ro  single
initrd        /initrd.img-2.6.27-7-generic

title        Ubuntu 8.10, memtest86+
uuid        33a1d591-78ed-44a7-8f7d-5c51cc00ca94
kernel        /memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda11.
title        Red Hat Enterprise Linux AS release 4 (Nahant) (on /dev/sda11)
root        (hd0,10)
kernel        /boot/linux ro root=/dev/hda11 
initrd        /boot/initrd-2.6.9-5.EL.img
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda11.
title        Red Hat Enterprise Linux AS (2.6.9-5.EL) (on /dev/sda11)
root        (hd0,10)
kernel        /boot/vmlinuz-2.6.9-5.EL ro root=LABEL=/1 rhgb quiet 
initrd        /boot/initrd-2.6.9-5.EL.img
savedefault
boot


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows NT/2000/XP (loader)
root        (hd0,1)
savedefault
makeactive
chainloader    +1


=============================== sdb8/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda8       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda1       /boot           ext2    defaults        0       2
/dev/sda9       /tmp            ext3    defaults        0       2
/dev/hda13      none            swap    sw              0       0
/dev/sda10      none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

=================== sdb8: Location of files loaded by Grub: ===================


 135.5GB: boot/grub/menu.lst
 135.5GB: boot/grub/stage2
 135.5GB: boot/initrd.img-2.6.27-7-generic
 135.6GB: boot/vmlinuz
 135.5GB: boot/vmlinuz-2.6.27-7-generic
 135.5GB: initrd.img
 135.5GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1

00000000  f6 f6 f6 f6 f6 f6 f6 f6  f6 f6 f6 f6 f6 f6 f6 f6  |................|
*
00000200

Unknown BootLoader  on sda5

00000000  eb 3c 90 4d 53 57 49 4e  34 2e 31 00 02 08 21 00  |.<.MSWIN4.1...!.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  86 3d fc 00 f3 3e 00 00  00 00 00 00 83 cd 0a 00  |.=...>..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 19 31 ed 15 44  52 49 56 45 5f 44 00 00  |..).1..DRIVE_D..|
00000050  00 00 46 41 54 33 32 20  20 20 f6 f6 f6 f6 f6 f6  |..FAT32   ......|
00000060  f6 f6 f6 f6 f6 f6 f6 f6  f6 f6 f6 f6 f6 f6 f6 f6  |................|
*
000001f0  f6 f6 f6 f6 f6 f6 f6 f6  f6 f6 f6 f6 00 00 55 aa  |..............U.|
00000200


```If anybody has a clue of what we are dealing with here,
would be appreciated.

Restoring damaged superblock:

Find out superblock location for /dev/sda2:
# dumpe2fs /dev/sda2 | grep superblock
Sample output:

  Primary superblock at 0, Group descriptors at 1-6
  Backup superblock at 32768, Group descriptors at 32769-32774
  Backup superblock at 98304, Group descriptors at 98305-98310
  Backup superblock at 163840, Group descriptors at 163841-163846
  Backup superblock at 229376, Group descriptors at 229377-229382
  Backup superblock at 294912, Group descriptors at 294913-294918
  Backup superblock at 819200, Group descriptors at 819201-819206
  Backup superblock at 884736, Group descriptors at 884737-884742
  Backup superblock at 1605632, Group descriptors at 1605633-1605638
  Backup superblock at 2654208, Group descriptors at 2654209-2654214
  Backup superblock at 4096000, Group descriptors at 4096001-4096006
  Backup superblock at 7962624, Group descriptors at 7962625-7962630
  Backup superblock at 11239424, Group descriptors at 11239425-11239430
  Backup superblock at 20480000, Group descriptors at 20480001-20480006
  Backup superblock at 23887872, Group descriptors at 23887873-23887878

Now check and repair a Linux file system using alternate superblock # 32768:
# fsck -b 32768 /dev/sda2
Sample output:

fsck 1.40.2 (12-Jul-2007)
e2fsck 1.40.2 (12-Jul-2007)
/dev/sda2 was not cleanly unmounted, check forced.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
Free blocks count wrong for group #241 (32254, counted=32253).
Fix? yes

Free blocks count wrong for group #362 (32254, counted=32248).
Fix? yes

Free blocks count wrong for group #368 (32254, counted=27774).
Fix? yes
..........
/dev/sda2: ***** FILE SYSTEM WAS MODIFIED *****
/dev/sda2: 59586/30539776 files (0.6% non-contiguous), 3604682/61059048 blocks

Now try to mount file system using mount command:
# mount /dev/sda2 /mnt

You can also use superblock stored at 32768 to mount partition, enter:
# mount sb={alternative-superblock} /dev/device /mnt
# mount sb=32768 /dev/sda2 /mnt

Try to browse and access file system:
# cd /mnt
# mkdir test
# ls -l
# cp file /path/to/safe/location

You should always keep backup of all important data including configuration files.

============================================================
Rootkit network:

Finally, here is some rootkit network main hosts.
 Put it in your firewall rules:
 
 129.47.9.160 - One of main hosts
Belongs to some shady business of "enlarge your penis" type
and all sorts of high pressure sales propaganda.

I was unable to post anything to their forums becakse it was
blocked. Nor I was able to send them email. It was rejected by
their hosts. Who knows, their whole enterprise is either a part
of this network, or has been hijacked and blocked so tightly
for any kind of input that they simply have no clue of what they
are involved in, and that is utmost evil manifest.

Root servers: 
129.47.9.160 - static IP, reverse DNS does not resolve 
 
74.125.10.34  TCP, remote port 80
Also operates using File share (UDP Port 137 for local and remote ports)

Some more hosts:
67.55.13.135 
95.84.39.134 
85.127.83.238 
96.53.229.236 
208.122.31.28 
94.178.214.23 
195.241.64.60

Notice the incoming ICMP packets like this one:
 
 090503 18:13:28 Deny  In  ICMP  RIP: 195.241.64.60   Type:     4 LIP: 91.124.232.166  
 
Record format:

 YYMMDD | Time GMT+2 Action Direction Protocol Remote_IP Remote_Port Local_IP Local_Port
 090504 21:23:22 Deny  Out UDP   RIP: 208.122.31.28   RPort:   137 LIP: 192.168.1.3     LPort:   137 

58.148.245.222:26376

Some whois info:
Query on:          129.47.9.160 
Target Host Name:  No Data Exists 
WhoIs Server:      whois.arin.net 
 
 
OrgName:    Whittaker Corporation  
OrgID:      WHITTA 
Address:    1955 North Surveyor Ave 
City:       Simi Valley 
StateProv:  CA 
PostalCode: 93063-3386 
Country:    US 
 
NetRange:   129.47.0.0 - 129.47.255.255  
CIDR:       129.47.0.0/16  
NetName:    WCAIFHLS 
NetHandle:  NET-129-47-0-0-1 
Parent:     NET-129-0-0-0-0 
NetType:    Direct Assignment 
Comment:     
RegDate:    1987-07-31 
Updated:    2007-05-22 

And here are some fun sequences:

Sequence 1: 

Field description:
  Date in YYMMDD format. Time is GMT+2)
  Out/In - packet direction
  TCP/UDP/ICMP - Protocol
  RIP: Remote IP
  RPort: Remote port
  LIP: Local IP
  LPort: Local port
  No Data Exists: means no reverse DNS query could be suceeded.
  *** ROOTKIT Server - Rule name

090503 16:40:18 Deny  Out TCP   RIP: 129.47.9.160    RPort:    80 LIP: 91.124.232.166  LPort:  1447 No Data Exists        *** ROOTKIT Server 
090503 16:40:21 Deny  Out TCP   RIP: 129.47.9.160    RPort:    80 LIP: 91.124.232.166  LPort:  1447 No Data Exists        *** ROOTKIT Server 
090503 16:40:27 Deny  Out TCP   RIP: 129.47.9.160    RPort:    80 LIP: 91.124.232.166  LPort:  1447 No Data Exists        *** ROOTKIT Server 
090503 16:45:18 Deny  Out TCP   RIP: 129.47.9.160    RPort:    80 LIP: 91.124.232.166  LPort:  1486 No Data Exists        *** ROOTKIT Server 
090503 16:45:21 Deny  Out TCP   RIP: 129.47.9.160    RPort:    80 LIP: 91.124.232.166  LPort:  1486 No Data Exists        *** ROOTKIT Server 
090503 16:45:27 Deny  Out TCP   RIP: 129.47.9.160    RPort:    80 LIP: 91.124.232.166  LPort:  1486 No Data Exists        *** ROOTKIT Server 
090503 16:46:13 Deny  In  TCP   RIP: 207.228.233.20  RPort: 50575 LIP: 91.124.232.166  LPort:    80 dslb-088-068-193-193.pools.arcor-ip.net         Web Hosting: Deny 
090503 16:46:16 Deny  In  TCP   RIP: 207.228.233.20  RPort: 50575 LIP: 91.124.232.166  LPort:    80 dslb-088-068-193-193.pools.arcor-ip.net         Web Hosting: Deny 
 
Typical sequence: 
 
Notice other hosts become active at the same time. 
 
Sequence 2: 
090503 16:50:18 Deny  Out TCP   RIP: 129.47.9.160    RPort:    80 LIP: 91.124.232.166  LPort:  1624 No Data Exists        *** ROOTKIT Server 
090503 16:50:19 Deny  Out TCP   RIP: 89.138.54.59    RPort: 38802 LIP: 91.124.232.166  LPort:  1625 89-138-57-185.bb.netvision.net.il Penetration Attempts netvision.il 
090503 16:50:19 Deny  Out ARP    
090503 16:50:21 Deny  Out TCP   RIP: 129.47.9.160    RPort:    80 LIP: 91.124.232.166  LPort:  1624 No Data Exists        *** ROOTKIT Server 
090503 16:50:22 Deny  Out TCP   RIP: 89.138.54.59    RPort: 38802 LIP: 91.124.232.166  LPort:  1625 89-138-57-185.bb.netvision.net.il Penetration Attempts netvision.il 
090503 16:50:22 Deny  Out ARP    
090503 16:50:27 Deny  Out TCP   RIP: 129.47.9.160    RPort:    80 LIP: 91.124.232.166  LPort:  1624 No Data Exists        *** ROOTKIT Server 
090503 16:50:28 Deny  Out TCP   RIP: 89.138.54.59    RPort: 38802 LIP: 91.124.232.166  LPort:  1625 89-138-57-185.bb.netvision.net.il Penetration Attempts netvision.il 
090503 16:52:23 Deny  Out TCP   RIP: 89.138.54.59    RPort: 38802 LIP: 91.124.232.166  LPort:  1725 89-138-57-185.bb.netvision.net.il Penetration Attempts netvision.il 
090503 16:52:26 Deny  Out TCP   RIP: 89.138.54.59    RPort: 38802 LIP: 91.124.232.166  LPort:  1725 89-138-57-185.bb.netvision.net.il Penetration Attempts netvision.il 
090503 16:52:32 Deny  Out TCP   RIP: 89.138.54.59    RPort: 38802 LIP: 91.124.232.166  LPort:  1725 89-138-57-185.bb.netvision.net.il Penetration Attempts netvision.il 
090503 16:55:18 Deny  Out TCP   RIP: 129.47.9.160    RPort:    80 LIP: 91.124.232.166  LPort:  1850 No Data Exists        *** ROOTKIT Server 
090503 16:55:21 Deny  Out TCP   RIP: 129.47.9.160    RPort:    80 LIP: 91.124.232.166  LPort:  1850 No Data Exists        *** ROOTKIT Server 
090503 16:55:55 Deny  Out UDP   RIP: 120.86.195.162  RPort:    80 LIP: 91.124.232.166  LPort: 56143 
090503 16:58:53 Deny  Out UDP   RIP: 92.82.70.165    RPort:    80 LIP: 91.124.232.166  LPort: 56143 
090503 16:59:07 Deny  Out TCP   RIP: 221.130.195.237 RPort:    81 LIP: 91.124.232.166  LPort:  1977 
090503 16:59:10 Deny  Out TCP   RIP: 221.130.195.237 RPort:    81 LIP: 91.124.232.166  LPort:  1977 
090503 16:59:39 Deny  Out TCP   RIP: 221.130.195.237 RPort:    81 LIP: 91.124.232.166  LPort:  1998 
090503 16:59:42 Deny  Out TCP   RIP: 221.130.195.237 RPort:    81 LIP: 91.124.232.166  LPort:  1998 
090503 16:59:42 Deny  In  TCP   RIP: 78.27.46.150    RPort:  8100 LIP: 91.124.232.166  LPort:  1999 banana Backdoor/SubSeven Trojan Block 
090503 16:59:45 Deny  In  TCP   RIP: 78.27.46.150    RPort:  8100 LIP: 91.124.232.166  LPort:  1999 banana Backdoor/SubSeven Trojan Block 
090503 16:59:51 Deny  In  TCP   RIP: 195.137.203.98  RPort:  9595 LIP: 91.124.232.166  LPort:  2001 banana         TransScout: Block 
090503 16:59:54 Deny  In  TCP   RIP: 64.16.40.18     RPort: 58914 LIP: 91.124.232.166  LPort:  2004 banana         TransScout: Block 
090503 16:59:57 Deny  In  TCP   RIP: 64.16.40.18     RPort: 58914 LIP: 91.124.232.166  LPort:  2004 banana         TransScout: Block 
090503 16:59:57 Deny  In  TCP   RIP: 119.235.51.68   RPort: 49894 LIP: 91.124.232.166  LPort:  2005 banana         TransScout: Block 
090503 17:00:00 Deny  In  TCP   RIP: 195.137.203.98  RPort:  9595 LIP: 91.124.232.166  LPort:  2001 banana         TransScout: Block 
090503 17:00:00 Deny  In  TCP   RIP: 119.235.51.68   RPort: 49894 LIP: 91.124.232.166  LPort:  2005 banana         TransScout: Block 
090503 17:00:03 Deny  Out TCP   RIP: 221.130.195.237 RPort:    81 LIP: 91.124.232.166  LPort:  2007 
090503 17:00:04 Deny  In  TCP   RIP: 64.16.40.18     RPort: 58914 LIP: 91.124.232.166  LPort:  2004 banana         TransScout: Block 
090503 17:00:06 Deny  Out TCP   RIP: 221.130.195.237 RPort:    81 LIP: 91.124.232.166  LPort:  2007 
090503 17:00:06 Deny  In  TCP   RIP: 119.235.51.68   RPort: 49894 LIP: 91.124.232.166  LPort:  2005 banana         TransScout: Block 
090503 17:00:12 Deny  Out TCP   RIP: 221.130.195.237 RPort:    81 LIP: 91.124.232.166  LPort:  2007 
090503 17:00:18 Deny  Out TCP   RIP: 129.47.9.160    RPort:    80 LIP: 91.124.232.166  LPort:  2015 No Data Exists        *** ROOTKIT Server 
090503 17:00:21 Deny  Out TCP   RIP: 129.47.9.160    RPort:    80 LIP: 91.124.232.166  LPort:  2015 No Data Exists        *** ROOTKIT Server 
090503 17:00:27 Deny  Out TCP   RIP: 129.47.9.160    RPort:    80 LIP: 91.124.232.166  LPort:  2015 No Data Exists        *** ROOTKIT Server 
 
Sequence 3: 
090504 10:55:43 Deny  Out TCP   RIP: 129.47.9.160    RPort:    80 LIP: 91.124.199.187  LPort:  1773 Searching...        *** ROOTKIT Server 
090504 10:55:46 Deny  Out TCP   RIP: 129.47.9.160    RPort:    80 LIP: 91.124.199.187  LPort:  1773 Searching...        *** ROOTKIT Server 
090504 10:55:52 Deny  Out TCP   RIP: 129.47.9.160    RPort:    80 LIP: 91.124.199.187  LPort:  1773 Searching...        *** ROOTKIT Server 
090504 10:56:37 Deny  In  TCP   RIP: 82.208.213.2    RPort: 60869 LIP: 91.124.199.187  LPort:  1807 banana  Spy Sender Trojan: Block 
090504 10:57:22 Deny  Out UDP   RIP: 129.47.9.160    RPort:   137 LIP: 192.168.1.3     LPort:   137 No Data Exists        *** ROOTKIT Server 
090504 10:57:23 Deny  Out UDP   RIP: 129.47.9.160    RPort:   137 LIP: 192.168.1.3     LPort:   137 No Data Exists        *** ROOTKIT Server 
090504 10:57:25 Deny  Out UDP   RIP: 129.47.9.160    RPort:   137 LIP: 192.168.1.3     LPort:   137 No Data Exists        *** ROOTKIT Server 
090504 10:57:26 Deny  Out UDP   RIP: 129.47.9.160    RPort:   137 LIP: 192.168.1.3     LPort:   137 No Data Exists        *** ROOTKIT Server 
090504 10:57:28 Deny  Out UDP   RIP: 129.47.9.160    RPort:   137 LIP: 192.168.1.3     LPort:   137 No Data Exists        *** ROOTKIT Server 
090504 10:57:29 Deny  Out UDP   RIP: 129.47.9.160    RPort:   137 LIP: 192.168.1.3     LPort:   137 No Data Exists        *** ROOTKIT Server 
090504 10:58:52 Deny  Out UDP   RIP: 87.194.8.87     RPort:  3407 LIP: 91.124.199.187  LPort: 54333 
090504 10:58:56 Deny  Out UDP   RIP: 222.160.85.139  RPort:  1676 LIP: 91.124.199.187  LPort: 54333 
090504 10:59:03 Deny  Out UDP   RIP: 86.218.107.216  RPort:  6881 LIP: 91.124.199.187  LPort: 54333 
090504 11:00:43 Deny  Out TCP   RIP: 129.47.9.160    RPort:    80 LIP: 91.124.199.187  LPort:  1965 Searching...        *** ROOTKIT Server 
090504 11:00:46 Deny  Out TCP   RIP: 129.47.9.160    RPort:    80 LIP: 91.124.199.187  LPort:  1965 Searching...        *** ROOTKIT Server 
090504 11:00:52 Deny  Out TCP   RIP: 129.47.9.160    RPort:    80 LIP: 91.124.199.187  LPort:  1965 Searching...        *** ROOTKIT Server 
090504 11:01:37 Deny  In  TCP   RIP: 75.58.146.27    RPort: 37632 LIP: 91.124.199.187  LPort:  2002 banana         TransScout: Block 
090504 11:01:39 Deny  In  TCP   RIP: 75.58.146.27    RPort: 37632 LIP: 91.124.199.187  LPort:  2002 banana         TransScout: Block 
090504 11:01:46 Deny  In  TCP   RIP: 75.58.146.27    RPort: 37632 LIP: 91.124.199.187  LPort:  2002 banana         TransScout: Block 
090504 11:01:47 Deny  In  TCP   RIP: 77.195.198.189  RPort: 21828 LIP: 91.124.199.187  LPort:  2003 banana         TransScout: Block 
090504 11:01:47 Deny  In  TCP   RIP: 77.195.198.189  RPort: 21828 LIP: 91.124.199.187  LPort:  2003 banana         TransScout: Block 
090504 11:01:48 Deny  In  TCP   RIP: 91.191.138.2    RPort:  6969 LIP: 91.124.199.187  LPort:  2005 banana         TransScout: Block 
090504 11:01:52 Deny  In  TCP   RIP: 77.195.198.189  RPort: 21828 LIP: 91.124.199.187  LPort:  2003 banana         TransScout: Block 
090504 11:01:54 Deny  In  TCP   RIP: 91.191.138.2    RPort:  6969 LIP: 91.124.199.187  LPort:  2005 banana         TransScout: Block 
090504 11:02:22 Deny  Out UDP   RIP: 61.51.73.24     RPort:  7565 LIP: 91.124.199.187  LPort: 54333 
090504 11:02:25 Deny  Out UDP   RIP: 84.52.160.186   RPort:  1066 LIP: 91.124.199.187  LPort: 54333 
090504 11:02:30 Deny  Out UDP   RIP: 58.35.79.160    RPort:  7323 LIP: 91.124.199.187  LPort: 54333 
090504 11:05:43 Deny  Out TCP   RIP: 129.47.9.160    RPort:    80 LIP: 91.124.199.187  LPort:  2176 Searching...        *** ROOTKIT Server 
090504 11:05:46 Deny  Out TCP   RIP: 129.47.9.160    RPort:    80 LIP: 91.124.199.187  LPort:  2176 Searching...        *** ROOTKIT Server 
090504 11:05:52 Deny  Out TCP   RIP: 129.47.9.160    RPort:    80 LIP: 91.124.199.187  LPort:  2176 Searching...        *** ROOTKIT Server 
 
And here is an attack: 
 
----------------------------------------------------------------------- 
Session started on: Sunday, May 03, 2009, Time: 17:01:47  GMT+2
----------------------------------------------------------------------- 
090503 17:01:47 Deny  Out TCP   RIP: 91.77.225.222   RPort:  3722 LIP: 91.124.232.166  LPort: 56143 
090503 17:02:59 Deny  Out TCP   RIP: 221.130.195.237 RPort:    81 LIP: 91.124.232.166  LPort:  2096 
090503 17:03:02 Deny  Out TCP   RIP: 221.130.195.237 RPort:    81 LIP: 91.124.232.166  LPort:  2096 
090503 17:03:08 Deny  Out TCP   RIP: 221.130.195.237 RPort:    81 LIP: 91.124.232.166  LPort:  2096 
090503 17:04:53 Deny  In  TCP   RIP: 86.45.246.171   RPort: 26925 LIP: 91.124.232.166  LPort:  2140 banana   DeepThroat Trojan Block 
090503 17:05:18 Deny  Out TCP   RIP: 129.47.9.160    RPort:    80 LIP: 91.124.232.166  LPort:  2161 No Data Exists        *** ROOTKIT Server 
090503 17:05:21 Deny  Out TCP   RIP: 129.47.9.160    RPort:    80 LIP: 91.124.232.166  LPort:  2161 No Data Exists        *** ROOTKIT Server 
090503 17:05:27 Deny  Out TCP   RIP: 129.47.9.160    RPort:    80 LIP: 91.124.232.166  LPort:  2161 No Data Exists        *** ROOTKIT Server 
090503 17:05:47 Deny  Out TCP   RIP: 221.130.195.237 RPort:    81 LIP: 91.124.232.166  LPort:  2180 
090503 17:05:50 Deny  Out TCP   RIP: 221.130.195.237 RPort:    81 LIP: 91.124.232.166  LPort:  2180 
090503 17:05:56 Deny  Out TCP   RIP: 221.130.195.237 RPort:    81 LIP: 91.124.232.166  LPort:  2180 
090503 17:10:18 Deny  Out TCP   RIP: 129.47.9.160    RPort:    80 LIP: 91.124.232.166  LPort:  2313 No Data Exists        *** ROOTKIT Server 
090503 17:10:21 Deny  Out TCP   RIP: 129.47.9.160    RPort:    80 LIP: 91.124.232.166  LPort:  2313 No Data Exists        *** ROOTKIT Server 
090503 17:10:27 Deny  Out TCP   RIP: 129.47.9.160    RPort:    80 LIP: 91.124.232.166  LPort:  2313 No Data Exists        *** ROOTKIT Server 
090503 17:11:42 Deny  Out TCP   RIP: 221.130.195.237 RPort:    81 LIP: 91.124.232.166  LPort:  2354 
090503 17:11:48 Deny  Out TCP   RIP: 221.130.195.237 RPort:    81 LIP: 91.124.232.166  LPort:  2354 
090503 17:15:18 Deny  Out TCP   RIP: 129.47.9.160    RPort:    80 LIP: 91.124.232.166  LPort:  2461 No Data Exists        *** ROOTKIT Server 
090503 17:15:21 Deny  Out TCP   RIP: 129.47.9.160    RPort:    80 LIP: 91.124.232.166  LPort:  2461 No Data Exists        *** ROOTKIT Server 
090503 17:15:27 Deny  Out TCP   RIP: 129.47.9.160    RPort:    80 LIP: 91.124.232.166  LPort:  2461 No Data Exists        *** ROOTKIT Server 
090503 17:20:18 Deny  Out TCP   RIP: 129.47.9.160    RPort:    80 LIP: 91.124.232.166  LPort:  2610 No Data Exists        *** ROOTKIT Server 
090503 17:20:21 Deny  Out TCP   RIP: 129.47.9.160    RPort:    80 LIP: 91.124.232.166  LPort:  2610 No Data Exists        *** ROOTKIT Server 
090503 17:20:27 Deny  Out TCP   RIP: 129.47.9.160    RPort:    80 LIP: 91.124.232.166  LPort:  2610 No Data Exists        *** ROOTKIT Server 
090503 17:22:30 Deny  Out TCP   RIP: 221.130.195.237 RPort:    81 LIP: 91.124.232.166  LPort:  2678 
090503 17:22:36 Deny  Out TCP   RIP: 221.130.195.237 RPort:    81 LIP: 91.124.232.166  LPort:  2678 
090503 17:25:18 Deny  Out TCP   RIP: 129.47.9.160    RPort:    80 LIP: 91.124.232.166  LPort:  2764 No Data Exists        *** ROOTKIT Server 
090503 17:25:21 Deny  Out TCP   RIP: 129.47.9.160    RPort:    80 LIP: 91.124.232.166  LPort:  2764 No Data Exists        *** ROOTKIT Server 
090503 17:25:27 Deny  Out TCP   RIP: 129.47.9.160    RPort:    80 LIP: 91.124.232.166  LPort:  2764 No Data Exists        *** ROOTKIT Server 
090503 17:25:36 Deny  Out TCP   RIP: 78.151.134.63   RPort: 10758 LIP: 91.124.232.166  LPort:  2773 banana SubSeven 2.1/2.2 Trojan: Block 
090503 17:25:38 Deny  Out TCP   RIP: 41.212.201.251  RPort: 53384 LIP: 91.124.232.166  LPort:  2774 banana SubSeven 2.1/2.2 Trojan: Block 
090503 17:25:39 Deny  Out TCP   RIP: 78.151.134.63   RPort: 10758 LIP: 91.124.232.166  LPort:  2773 banana SubSeven 2.1/2.2 Trojan: Block 
090503 17:25:41 Deny  Out TCP   RIP: 41.212.201.251  RPort: 53384 LIP: 91.124.232.166  LPort:  2774 banana SubSeven 2.1/2.2 Trojan: Block 
090503 17:25:45 Deny  Out TCP   RIP: 78.151.134.63   RPort: 10758 LIP: 91.124.232.166  LPort:  2773 banana SubSeven 2.1/2.2 Trojan: Block 
090503 17:25:47 Deny  Out TCP   RIP: 41.212.201.251  RPort: 53384 LIP: 91.124.232.166  LPort:  2774 banana SubSeven 2.1/2.2 Trojan: Block 
090503 17:30:18 Deny  Out TCP   RIP: 129.47.9.160    RPort:    80 LIP: 91.124.232.166  LPort:  2909 No Data Exists        *** ROOTKIT Server 
090503 17:30:21 Deny  Out TCP   RIP: 129.47.9.160    RPort:    80 LIP: 91.124.232.166  LPort:  2909 No Data Exists        *** ROOTKIT Server 
090503 17:30:27 Deny  Out TCP   RIP: 129.47.9.160    RPort:    80 LIP: 91.124.232.166  LPort:  2909 No Data Exists        *** ROOTKIT Server 
090503 17:33:18 Deny  In  TCP   RIP: 74.216.26.235   RPort: 14167 LIP: 91.124.232.166  LPort:  2989 sewer-output         Rat Trojan: Block 
090503 17:33:21 Deny  In  TCP   RIP: 74.216.26.235   RPort: 14167 LIP: 91.124.232.166  LPort:  2989 sewer-output         Rat Trojan: Block 
090503 17:33:27 Deny  In  TCP   RIP: 74.216.26.235   RPort: 14167 LIP: 91.124.232.166  LPort:  2989 sewer-output         Rat Trojan: Block 
090503 17:34:32 Deny  In  TCP   RIP: 196.25.255.214  RPort: 37922 LIP: 91.124.232.166  LPort:  3024 banana    Wincrash Trojan: Block 
090503 17:34:35 Deny  In  TCP   RIP: 196.25.255.214  RPort: 37922 LIP: 91.124.232.166  LPort:  3024 banana    Wincrash Trojan: Block 
090503 17:35:18 Deny  Out TCP   RIP: 129.47.9.160    RPort:    80 LIP: 91.124.232.166  LPort:  3043 No Data Exists        *** ROOTKIT Server 
090503 17:35:21 Deny  Out TCP   RIP: 129.47.9.160    RPort:    80 LIP: 91.124.232.166  LPort:  3043 No Data Exists        *** ROOTKIT Server 
090503 17:35:27 Deny  Out TCP   RIP: 129.47.9.160    RPort:    80 LIP: 91.124.232.166  LPort:  3043 No Data Exists        *** ROOTKIT Server 
090503 17:40:18 Deny  Out TCP   RIP: 129.47.9.160    RPort:    80 LIP: 91.124.232.166  LPort:  3178 No Data Exists        *** ROOTKIT Server 
090503 17:40:21 Deny  Out TCP   RIP: 129.47.9.160    RPort:    80 LIP: 91.124.232.166  LPort:  3178 No Data Exists        *** ROOTKIT Server 
090503 17:40:27 Deny  Out TCP   RIP: 129.47.9.160    RPort:    80 LIP: 91.124.232.166  LPort:  3178 No Data Exists        *** ROOTKIT Server 
090503 17:44:14 Deny  Out TCP   RIP: 221.130.195.237 RPort:    81 LIP: 91.124.232.166  LPort:  3288 
090503 17:44:20 Deny  Out TCP   RIP: 221.130.195.237 RPort:    81 LIP: 91.124.232.166  LPort:  3288 
090503 17:45:18 Deny  Out TCP   RIP: 129.47.9.160    RPort:    80 LIP: 91.124.232.166  LPort:  3320 No Data Exists        *** ROOTKIT Server 
090503 17:45:21 Deny  Out TCP   RIP: 129.47.9.160    RPort:    80 LIP: 91.124.232.166  LPort:  3320 No Data Exists        *** ROOTKIT Server 
090503 17:45:27 Deny  Out TCP   RIP: 129.47.9.160    RPort:    80 LIP: 91.124.232.166  LPort:  3320 No Data Exists        *** ROOTKIT Server 
090503 17:50:18 Deny  Out TCP   RIP: 129.47.9.160    RPort:    80 LIP: 91.124.232.166  LPort:  3460 No Data Exists        *** ROOTKIT Server 
090503 17:50:21 Deny  Out TCP   RIP: 129.47.9.160    RPort:    80 LIP: 91.124.232.166  LPort:  3460 No Data Exists        *** ROOTKIT Server 
090503 17:50:27 Deny  Out TCP   RIP: 129.47.9.160    RPort:    80 LIP: 91.124.232.166  LPort:  3460 No Data Exists        *** ROOTKIT Server 
090503 17:51:15 Deny  Out UDP   RIP: 94.178.11.221   RPort:    81 LIP: 91.124.232.166  LPort: 56143 
090503 17:55:18 Deny  Out TCP   RIP: 129.47.9.160    RPort:    80 LIP: 91.124.232.166  LPort:  3625 No Data Exists        *** ROOTKIT Server 
090503 17:55:21 Deny  Out TCP   RIP: 129.47.9.160    RPort:    80 LIP: 91.124.232.166  LPort:  3625 No Data Exists        *** ROOTKIT Server 
090503 17:55:27 Deny  Out TCP   RIP: 129.47.9.160    RPort:    80 LIP: 91.124.232.166  LPort:  3625 No Data Exists        *** ROOTKIT Server 
090503 17:59:30 Deny  Out UDP   RIP: 76.113.20.46    RPort:   777 LIP: 91.124.232.166  LPort: 56143 
090503 18:00:18 Deny  Out TCP   RIP: 129.47.9.160    RPort:    80 LIP: 91.124.232.166  LPort:  3817 No Data Exists        *** ROOTKIT Server 
090503 18:00:21 Deny  Out TCP   RIP: 129.47.9.160    RPort:    80 LIP: 91.124.232.166  LPort:  3817 No Data Exists        *** ROOTKIT Server 
090503 18:00:27 Deny  Out TCP   RIP: 129.47.9.160    RPort:    80 LIP: 91.124.232.166  LPort:  3817 No Data Exists        *** ROOTKIT Server 
090503 18:05:18 Deny  Out TCP   RIP: 129.47.9.160    RPort:    80 LIP: 91.124.232.166  LPort:  3988 No Data Exists        *** ROOTKIT Server 
090503 18:05:21 Deny  Out TCP   RIP: 129.47.9.160    RPort:    80 LIP: 91.124.232.166  LPort:  3988 No Data Exists        *** ROOTKIT Server 
090503 18:05:27 Deny  Out TCP   RIP: 129.47.9.160    RPort:    80 LIP: 91.124.232.166  LPort:  3988 No Data Exists        *** ROOTKIT Server 
090503 18:07:04 Deny  Out UDP   RIP: 213.93.200.245  RPort:   526 LIP: 91.124.232.166  LPort: 56143 
090503 18:08:30 Deny  In  TCP   RIP: 79.124.103.203  RPort: 64895 LIP: 91.124.232.166  LPort:  4092 banana    Wincrash Trojan: Block 
090503 18:08:33 Deny  In  TCP   RIP: 79.124.103.203  RPort: 64895 LIP: 91.124.232.166  LPort:  4092 banana    Wincrash Trojan: Block 
090503 18:10:18 Deny  Out TCP   RIP: 129.47.9.160    RPort:    80 LIP: 91.124.232.166  LPort:  4149 No Data Exists        *** ROOTKIT Server 
090503 18:10:21 Deny  Out TCP   RIP: 129.47.9.160    RPort:    80 LIP: 91.124.232.166  LPort:  4149 No Data Exists        *** ROOTKIT Server 
090503 18:10:27 Deny  Out TCP   RIP: 129.47.9.160    RPort:    80 LIP: 91.124.232.166  LPort:  4149 No Data Exists        *** ROOTKIT Server 
090503 18:11:50 Deny  Out UDP   RIP: 120.8.54.143    RPort:    80 LIP: 91.124.232.166  LPort: 56143 
090503 18:13:28 Deny  In  ICMP  RIP: 195.241.64.60   Type:     4 LIP: 91.124.232.166  36.Red-83-46-94.dynamicIP.rima-tde.net ROOTKIT 36.Red-83-46-94.dynamicIP.rima-tde.net 
090503 18:14:05 Deny  Out TCP   RIP: 62.72.234.30    RPort: 16209 LIP: 91.124.232.166  LPort:  4267 banana                    banana 
090503 18:14:08 Deny  Out TCP   RIP: 62.72.234.30    RPort: 16209 LIP: 91.124.232.166  LPort:  4267 banana                    banana 
090503 18:14:14 Deny  Out TCP   RIP: 62.72.234.30    RPort: 16209 LIP: 91.124.232.166  LPort:  4267 banana                    banana 
090503 18:15:18 Deny  Out TCP   RIP: 129.47.9.160    RPort:    80 LIP: 91.124.232.166  LPort:  4313 No Data Exists        *** ROOTKIT Server 
090503 18:15:21 Deny  Out TCP   RIP: 129.47.9.160    RPort:    80 LIP: 91.124.232.166  LPort:  4313 No Data Exists        *** ROOTKIT Server 
090503 18:15:27 Deny  Out TCP   RIP: 129.47.9.160    RPort:    80 LIP: 91.124.232.166  LPort:  4313 No Data Exists        *** ROOTKIT Server 
090503 18:20:18 Deny  Out TCP   RIP: 129.47.9.160    RPort:    80 LIP: 91.124.232.166  LPort:  4471 No Data Exists        *** ROOTKIT Server 
090503 18:20:21 Deny  Out TCP   RIP: 129.47.9.160    RPort:    80 LIP: 91.124.232.166  LPort:  4471 No Data Exists        *** ROOTKIT Server 
090503 18:23:15 Deny  In  TCP   RIP: 198.54.202.250  RPort: 37922 LIP: 91.124.232.166  LPort:  4567 banana    Filenail Trojan: Block 
090503 18:25:18 Deny  Out TCP   RIP: 129.47.9.160    RPort:    80 LIP: 91.124.232.166  LPort:  4630 No Data Exists        *** ROOTKIT Server 
090503 18:25:21 Deny  Out TCP   RIP: 129.47.9.160    RPort:    80 LIP: 91.124.232.166  LPort:  4630 No Data Exists        *** ROOTKIT Server 
090503 18:25:27 Deny  Out TCP   RIP: 129.47.9.160    RPort:    80 LIP: 91.124.232.166  LPort:  4630 No Data Exists        *** ROOTKIT Server 
090503 18:26:59 Deny  Out TCP   RIP: 221.130.195.237 RPort:    81 LIP: 91.124.232.166  LPort:  4687 
090503 18:27:02 Deny  Out TCP   RIP: 221.130.195.237 RPort:    81 LIP: 91.124.232.166  LPort:  4687 
090503 18:27:08 Deny  Out TCP   RIP: 221.130.195.237 RPort:    81 LIP: 91.124.232.166  LPort:  4687 
090503 18:30:18 Deny  Out TCP   RIP: 129.47.9.160    RPort:    80 LIP: 91.124.232.166  LPort:  4796 No Data Exists        *** ROOTKIT Server 
090503 18:30:27 Deny  Out TCP   RIP: 129.47.9.160    RPort:    80 LIP: 91.124.232.166  LPort:  4796 No Data Exists        *** ROOTKIT Server 
090503 18:35:18 Deny  Out TCP   RIP: 129.47.9.160    RPort:    80 LIP: 91.124.232.166  LPort:  4956 No Data Exists        *** ROOTKIT Server 
090503 18:35:21 Deny  Out TCP   RIP: 129.47.9.160    RPort:    80 LIP: 91.124.232.166  LPort:  4956 No Data Exists        *** ROOTKIT Server 
090503 18:35:27 Deny  Out TCP   RIP: 129.47.9.160    RPort:    80 LIP: 91.124.232.166  LPort:  4956 No Data Exists        *** ROOTKIT Server 
090503 18:36:30 Deny  Out UDP   RIP: 91.78.183.46    RPort:     1 LIP: 91.124.232.166  LPort: 56143 
090503 18:36:42 Deny  In  TCP   RIP: 85.225.64.174   RPort: 51413 LIP: 91.124.232.166  LPort:  5000 banana Sokets de Trois v1. Trojan: Block 
090503 18:36:43 Deny  In  TCP   RIP: 85.225.64.174   RPort: 51413 LIP: 91.124.232.166  LPort:  5000 banana Sokets de Trois v1. Trojan: Block 
090503 18:36:45 Deny  In  TCP   RIP: 85.225.64.174   RPort: 51413 LIP: 91.124.232.166  LPort:  5000 banana Sokets de Trois v1. Trojan: Block 
090503 18:36:48 Deny  In  TCP   RIP: 85.225.64.174   RPort: 51413 LIP: 91.124.232.166  LPort:  5000 banana Sokets de Trois v1. Trojan: Block 
090503 18:36:50 Deny  In  TCP   RIP: 85.225.64.174   RPort: 51413 LIP: 91.124.232.166  LPort:  5000 banana Sokets de Trois v1. Trojan: Block 
090503 18:36:57 Deny  In  TCP   RIP: 85.225.64.174   RPort: 51413 LIP: 91.124.232.166  LPort:  5000 banana Sokets de Trois v1. Trojan: Block 
090503 18:37:13 Deny  In  TCP   RIP: 85.225.64.174   RPort: 51413 LIP: 91.124.232.166  LPort:  5000 banana Sokets de Trois v1. Trojan: Block 
090503 18:37:45 Deny  In  TCP   RIP: 85.225.64.174   RPort: 51413 LIP: 91.124.232.166  LPort:  5000 banana Sokets de Trois v1. Trojan: Block 
090503 18:37:56 Deny  In  TCP   RIP: 85.225.64.174   RPort: 51413 LIP: 91.124.232.166  LPort:  5000 banana Sokets de Trois v1. Trojan: Block 
090503 18:40:18 Deny  Out TCP   RIP: 129.47.9.160    RPort:    80 LIP: 91.124.232.166  LPort:  1150 No Data Exists        *** ROOTKIT Server 
090503 18:40:27 Deny  Out TCP   RIP: 129.47.9.160    RPort:    80 LIP: 91.124.232.166  LPort:  1150 No Data Exists        *** ROOTKIT Server 
090503 18:43:12 Deny  In  TCP   RIP: 122.2.96.217    RPort: 14038 LIP: 91.124.232.166  LPort:  1243 banana Backdoor/SubSeven Trojan Block 
090503 18:43:18 Deny  In  TCP   RIP: 122.2.96.217    RPort: 14038 LIP: 91.124.232.166  LPort:  1243 banana Backdoor/SubSeven Trojan Block 
090503 18:45:18 Deny  Out TCP   RIP: 129.47.9.160    RPort:    80 LIP: 91.124.232.166  LPort:  1312 No Data Exists        *** ROOTKIT Server 
090503 18:45:21 Deny  Out TCP   RIP: 129.47.9.160    RPort:    80 LIP: 91.124.232.166  LPort:  1312 No Data Exists        *** ROOTKIT Server 
090503 18:45:27 Deny  Out TCP   RIP: 129.47.9.160    RPort:    80 LIP: 91.124.232.166  LPort:  1312 No Data Exists        *** ROOTKIT Server 
090503 18:47:32 Deny  Out TCP   RIP: 89.138.54.59    RPort: 38802 LIP: 91.124.232.166  LPort:  1386 89-138-57-185.bb.netvision.net.il Penetration Attempts netvision.il 
090503 18:47:35 Deny  Out TCP   RIP: 89.138.54.59    RPort: 38802 LIP: 91.124.232.166  LPort:  1386 89-138-57-185.bb.netvision.net.il Penetration Attempts netvision.il 
090503 18:47:41 Deny  Out TCP   RIP: 89.138.54.59    RPort: 38802 LIP: 91.124.232.166  LPort:  1386 89-138-57-185.bb.netvision.net.il Penetration Attempts netvision.il 
090503 18:49:00 Deny  Out UDP   RIP: 76.254.61.116   RPort:   666 LIP: 91.124.232.166  LPort: 56143 
090503 18:49:19 Deny  Out TCP   RIP: 89.138.54.59    RPort: 38802 LIP: 91.124.232.166  LPort:  1441 89-138-57-185.bb.netvision.net.il Penetration Attempts netvision.il 
090503 18:49:22 Deny  Out TCP   RIP: 89.138.54.59    RPort: 38802 LIP: 91.124.232.166  LPort:  1441 89-138-57-185.bb.netvision.net.il Penetration Attempts netvision.il 
090503 18:49:28 Deny  Out TCP   RIP: 89.138.54.59    RPort: 38802 LIP: 91.124.232.166  LPort:  1441 89-138-57-185.bb.netvision.net.il Penetration Attempts netvision.il 
090503 18:50:18 Deny  Out TCP   RIP: 129.47.9.160    RPort:    80 LIP: 91.124.232.166  LPort:  1477 No Data Exists        *** ROOTKIT Server 
090503 18:50:21 Deny  Out TCP   RIP: 129.47.9.160    RPort:    80 LIP: 91.124.232.166  LPort:  1477 No Data Exists        *** ROOTKIT Server 
090503 18:50:27 Deny  Out TCP   RIP: 129.47.9.160    RPort:    80 LIP: 91.124.232.166  LPort:  1477 No Data Exists        *** ROOTKIT Server 
090503 18:50:45 Deny  In  TCP   RIP: 86.133.202.74   RPort:  8816 LIP: 91.124.232.166  LPort:  1492 banana    FTP99CMP Trojan: Block 
090503 18:50:48 Deny  In  TCP   RIP: 86.133.202.74   RPort:  8816 LIP: 91.124.232.166  LPort:  1492 banana    FTP99CMP Trojan: Block 
090503 18:50:54 Deny  In  TCP   RIP: 86.133.202.74   RPort:  8816 LIP: 91.124.232.166  LPort:  1492 banana    FTP99CMP Trojan: Block 
090503 18:50:55 Deny  In  TCP   RIP: 86.133.202.74   RPort:  8816 LIP: 91.124.232.166  LPort:  1492 banana    FTP99CMP Trojan: Block 
090503 18:53:58 Deny  Out TCP   RIP: 89.138.54.59    RPort: 38802 LIP: 91.124.232.166  LPort:  1604 89-138-57-185.bb.netvision.net.il Penetration Attempts netvision.il 
090503 18:54:01 Deny  Out TCP   RIP: 89.138.54.59    RPort: 38802 LIP: 91.124.232.166  LPort:  1604 89-138-57-185.bb.netvision.net.il Penetration Attempts netvision.il 
090503 18:54:07 Deny  Out TCP   RIP: 89.138.54.59    RPort: 38802 LIP: 91.124.232.166  LPort:  1604 89-138-57-185.bb.netvision.net.il Penetration Attempts netvision.il 
090503 18:55:03 Deny  Out TCP   RIP: 89.138.54.59    RPort: 38802 LIP: 91.124.232.166  LPort:  1636 89-138-57-185.bb.netvision.net.il Penetration Attempts netvision.il 
090503 18:55:12 Deny  Out TCP   RIP: 89.138.54.59    RPort: 38802 LIP: 91.124.232.166  LPort:  1636 89-138-57-185.bb.netvision.net.il Penetration Attempts netvision.il 
090503 18:55:18 Deny  Out TCP   RIP: 129.47.9.160    RPort:    80 LIP: 91.124.232.166  LPort:  1646 No Data Exists        *** ROOTKIT Server 
090503 18:55:21 Deny  Out TCP   RIP: 129.47.9.160    RPort:    80 LIP: 91.124.232.166  LPort:  1646 No Data Exists        *** ROOTKIT Server 
090503 18:55:27 Deny  Out TCP   RIP: 129.47.9.160    RPort:    80 LIP: 91.124.232.166  LPort:  1646 No Data Exists        *** ROOTKIT Server 
090503 18:56:44 Deny  Out UDP   RIP: 202.28.250.209  RPort:    80 LIP: 91.124.232.166  LPort: 56143 
090503 18:57:11 Deny  Out TCP   RIP: 192.168.1.1     RPort:    53 LIP: 192.168.1.3     LPort: 55637 
090503 18:57:14 Deny  Out TCP   RIP: 192.168.1.1     RPort:    53 LIP: 192.168.1.3     LPort: 55637 
090503 18:57:20 Deny  Out TCP   RIP: 192.168.1.1     RPort:    53 LIP: 192.168.1.3     LPort: 55637 
090503 18:57:48 Deny  Out TCP   RIP: 89.138.54.59    RPort: 38802 LIP: 91.124.232.166  LPort:  1731 89-138-57-185.bb.netvision.net.il Penetration Attempts netvision.il 
090503 18:57:51 Deny  Out TCP   RIP: 89.138.54.59    RPort: 38802 LIP: 91.124.232.166  LPort:  1731 89-138-57-185.bb.netvision.net.il Penetration Attempts netvision.il 
090503 18:57:57 Deny  Out TCP   RIP: 89.138.54.59    RPort: 38802 LIP: 91.124.232.166  LPort:  1731 89-138-57-185.bb.netvision.net.il Penetration Attempts netvision.il 
 
# ARIN WHOIS database, last updated 2009-04-30 19:10 
================================================================== 
host183-172-dynamic.56-79-r.retail.teleco 
 
Remote: 
94.178.214.23 
 
118-161-248- Packet data: 
00112 31 34 07 64 79 6e 61 6d  69 63 05 68 69 6e 65 74  14.dynamic.hinet 00128 03 6e 65 74 00 c0 0f 00  02 00 01 00 00 fd de 00  .net 
 
090501 20:33:01 Deny  In  TCP   RIP: 78.30.200.211   RPort:  4500 LIP: 91.124.151.53   LPort: 40217 
090501 20:25:35 Deny  In  TCP   RIP: 78.30.200.211   RPort:  4198 LIP: 91.124.151.53   LPort: 40217 
090501 20:25:39 Deny  Out UDP   RIP: 78.30.200.211   RPort:   137 LIP: 192.168.1.3     LPort:   137 
 
090501 20:32:41 Deny  In  TCP   RIP: 77.38.216.144   RPort:  3516 LIP: 91.124.151.53   LPort: 57289 
090501 20:32:44 Deny  Out UDP   RIP: 77.38.216.144   RPort:   137 LIP: 192.168.1.3     LPort:   137 
 
; ------------------------------------------------------------- 
; System is offline, browser is not running 
; ------------------------------------------------------------- 
090502 00:47:20 Deny  Out TCP   RIP: 89.138.54.59    RPort: 38802 LIP: 192.168.1.3     LPort:  1210 
090502 01:00:49 Deny  Out TCP   RIP: 89.138.54.59    RPort: 38802 LIP: 192.168.1.3     LPort:  1550 
 
090502 01:07:55 Deny  Out TCP   RIP: 221.130.195.237 RPort:    81 LIP: 192.168.1.3     LPort:  1721 
090502 03:11:55 Deny  Out TCP   RIP: 221.130.195.237 RPort:    81 LIP: 192.168.1.3     LPort:  2320 
090502 00:44:11 Deny  Out TCP   RIP: 221.130.195.237 RPort:    81 LIP: 192.168.1.3     LPort:  1129 
090502 00:44:14 Deny  Out TCP   RIP: 221.130.195.237 RPort:    81 LIP: 192.168.1.3     LPort:  1129 
090502 01:02:04 Deny  Out TCP   RIP: 221.130.195.237 RPort:    81 LIP: 192.168.1.3     LPort:  1581 
090502 01:14:06 Deny  Out TCP   RIP: 221.130.195.237 RPort:    81 LIP: 192.168.1.3     LPort:  1870 
090502 03:12:04 Deny  Out TCP   RIP: 221.130.195.237 RPort:    81 LIP: 192.168.1.3     LPort:  2320 
090502 03:12:04 Deny  Out TCP   RIP: 221.130.195.237 RPort:    81 LIP: 192.168.1.3     LPort:  2320 
 
65.54.89.90 cds87.ams9.llnw.net Microsoft Corp 
==================================================================== 
Immediately after going online, rootkit does a DNS request 
for dot.ep.net.hostmaster 
 
ROOTKIT SERVER 
-------------- 
090502 15:15:28 Deny  Out TCP   RIP: 129.47.9.160    RPort:    80 LIP: 192.168.1.3     LPort:  2564No Data Exists        *** ROOTKIT Server 
 
==========================================================

---

### Post by Officer Dibble on 2009-07-27
Erm... the butler did it... :confused:

(Man that's got to be the longest forum post I have seen in my life!!)

---

