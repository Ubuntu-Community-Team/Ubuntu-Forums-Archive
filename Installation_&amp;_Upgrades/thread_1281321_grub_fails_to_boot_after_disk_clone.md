---
title: "grub fails to boot after disk clone"
date: 2009-10-03
forum: Installation &amp; Upgrades
---

### Post by ottosykora on 2009-10-03
I need to make full copy of first hard drive. Tried with clonzilla, acronis, and simple dd, all does same results.
After cloning all seems to be present, windows partitons do boot, not so any linux.
Main bootmanager is a 3rd party thing, but works well on the original disk.

for ubuntu, there is a 7boot partiton on disk 1 (sda10) here the grub and boot kernel etc are located.
ubuntu 9.04 itself is on disk 2 (sdb13) and has no grub in it installed.

on the original disk, I can simply boot the sda10 and this will load the rest from the sdb13.
On the copy this does not work, have tried all sorts of things chekcd the UUID of the drives, they still the same. Only the sector numbers have changed, the new disk is bigger.

I thought it would be possible to use the boot CD of ubuntu to repair such installation, but can not see there any way of doing it so far.

Any idea how to bring grub to life again?

---

### Post by arrange on 2009-10-03
Please attach all the drives and post the output of [boot_info_script]("https://sourceforge.net/projects/bootinfoscript/") here. We need more (structured) info.

---

### Post by keerthanak on 2009-10-03
[CENTER][CENTER]**[click here to know more]("http://www.google.com")                                                      **[/CENTER]
[/CENTER]

---

### Post by ottosykora on 2009-10-03
> **arrange said:**
> Please attach all the drives and post the output of [boot_info_script]("https://sourceforge.net/projects/bootinfoscript/") here. We need more (structured) info.

yes will try, but at present no linux boots here, only windows partitions.
Can this be run also from live CD somehow?

---

### Post by ottosykora on 2009-10-03
> **arrange said:**
> Please attach all the drives and post the output of [boot_info_script]("https://sourceforge.net/projects/bootinfoscript/") here. We need more (structured) info.

did download the script, but what next?

---

### Post by ottosykora on 2009-10-03
ok , managed to run it, here theresults:

============================= Boot Info Summary: ==============================

 => Lilo is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
 => Lilo is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
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

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda9: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda10: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda10 and 
                       looks at sector 131210031 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #10 for 
                       /grub/menu.lst.
    Operating System:  
    Boot files/dirs:   /grub/menu.lst

sda11: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda12: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda13: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda13 and 
                       looks at sector 144707241 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on the same partition for 
                       /boot/grub/menu.lst.
    Operating System:   Welcome to SUSE LINUX 10.1 
                       (i586) - Kernel ().
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /etc/lilo.conf /boot/map

sda14: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  According to the info in the boot sector, sdb6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb7: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  According to the info in the boot sector, sdb7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb8: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  According to the info in the boot sector, sdb8 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb9: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  According to the info in the boot sector, sdb9 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb10: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  According to the info in the boot sector, sdb10 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb11: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  According to the info in the boot sector, sdb11 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb12: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb13: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb14: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc6: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdc7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Platte /dev/sda: 250.0 GByte, 250059350016 Byte
255 Köpfe, 63 Sektoren/Spuren, 30401 Zylinder, zusammen 488397168 Sektoren
Einheiten = Sektoren von 1 × 512 = 512 Bytes
Disk identifier: 0xe4651a0a

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        64,259        64,197  de Dell Utility
/dev/sda2           8,434,125    39,327,119    30,892,995  17 Hidden HPFS/NTFS
/dev/sda3          39,327,120   156,248,189   116,921,070   f W95 Ext d (LBA)
/dev/sda5          39,327,183    47,536,334     8,209,152   b W95 FAT32
/dev/sda6          47,536,398    80,292,869    32,756,472   b W95 FAT32
/dev/sda7          80,292,933   121,258,619    40,965,687   b W95 FAT32
/dev/sda8         121,258,683   123,314,939     2,056,257  82 Linux swap / Solaris
/dev/sda9         123,315,003   131,186,789     7,871,787  83 Linux
/dev/sda10   *    131,186,853   131,283,179        96,327  83 Linux
/dev/sda11        131,283,243   131,395,634       112,392  83 Linux
/dev/sda12        131,395,698   131,508,089       112,392  83 Linux
/dev/sda13        131,508,153   154,320,389    22,812,237  83 Linux
/dev/sda14        154,320,453   156,248,189     1,927,737  83 Linux
/dev/sda4              64,260     8,434,124     8,369,865  1b Hidden W95 FAT32


Drive: sdb ___________________ _____________________________________________________

Platte /dev/sdb: 500.1 GByte, 500107862016 Byte
255 Köpfe, 63 Sektoren/Spuren, 60801 Zylinder, zusammen 976773168 Sektoren
Einheiten = Sektoren von 1 × 512 = 512 Bytes
Disk identifier: 0xda031b5f

Partition  Boot         Start           End          Size  Id System

/dev/sdb2              16,065   488,392,064   488,376,000   f W95 Ext d (LBA)
/dev/sdb5              16,128    65,561,264    65,545,137   b W95 FAT32
/dev/sdb6          65,561,328   131,106,464    65,545,137   b W95 FAT32
/dev/sdb7         131,106,528   196,651,664    65,545,137   b W95 FAT32
/dev/sdb8         196,651,728   262,196,864    65,545,137   b W95 FAT32
/dev/sdb9         262,196,928   327,742,064    65,545,137   b W95 FAT32
/dev/sdb10        327,742,128   393,287,264    65,545,137   b W95 FAT32
/dev/sdb11        393,287,328   458,832,464    65,545,137   b W95 FAT32
/dev/sdb12        458,832,528   469,355,039    10,522,512  83 Linux
/dev/sdb13   *    469,355,103   481,644,764    12,289,662  83 Linux
/dev/sdb14        481,644,828   488,392,064     6,747,237  83 Linux


Drive: sdc ___________________ _____________________________________________________

Platte /dev/sdc: 320.0 GByte, 320072933376 Byte
255 Köpfe, 63 Sektoren/Spuren, 38913 Zylinder, zusammen 625142448 Sektoren
Einheiten = Sektoren von 1 × 512 = 512 Bytes
Disk identifier: 0x40a1dbb0

Partition  Boot         Start           End          Size  Id System

/dev/sdc1              16,065   625,137,344   625,121,280   f W95 Ext d (LBA)
/dev/sdc5              16,128   402,653,159   402,637,032   b W95 FAT32
/dev/sdc6         402,653,223   604,060,064   201,406,842   b W95 FAT32
/dev/sdc7         604,060,128   625,137,344    21,077,217   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D2-0A11" TYPE="vfat" 
/dev/sda2: UUID="583805083804E73A" LABEL="XP" TYPE="ntfs" 
/dev/sda4: LABEL="W98SE" UUID="4469-C7D7" TYPE="vfat" 
/dev/sda5: LABEL="DATA8" UUID="445F-46A7" TYPE="vfat" 
/dev/sda6: LABEL="DATA" UUID="CB56-7A27" TYPE="vfat" 
/dev/sda7: LABEL="INSTPATH" UUID="0F1D-F83C" TYPE="vfat" 
/dev/sda8: TYPE="swap" 
/dev/sda9: LABEL="KN4" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda10: LABEL="BOOTU" UUID="dfb1be63-3f69-4a75-a52e-71443765e161" TYPE="ext3" 
/dev/sda11: LABEL="BOOTD" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda12: LABEL="BOOTX" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda13: LABEL="SU" UUID="681dba5c-7fc2-487f-96ab-68d0da98cdcd" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda14: LABEL="HOME" UUID="d06efc52-a7e9-4e17-94d0-a8d11ca3e39b" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: LABEL="DOWNLOAD" UUID="44C1-0575" TYPE="vfat" 
/dev/sdb6: LABEL="VM" UUID="8982-0B66" TYPE="vfat" 
/dev/sdb7: UUID="CE43-11D9" TYPE="vfat" 
/dev/sdb8: LABEL="BACKUP" UUID="44C1-1465" TYPE="vfat" 
/dev/sdb9: UUID="8982-28D6" TYPE="vfat" 
/dev/sdb10: LABEL="SOFTWARE" UUID="CE43-3D53" TYPE="vfat" 
/dev/sdb11: UUID="1304-51E4" TYPE="vfat" 
/dev/sdb12: UUID="07f42ac1-eae3-4aca-8a92-266f1ace2b02" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb13: LABEL="UBUNTU" UUID="d64ef18f-14be-41d4-84dd-ccbb778967a9" TYPE="ext3" 
/dev/sdb14: UUID="1a50c6a2-03e8-4002-96c6-b92f1359657f" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc5: LABEL="PORT10" UUID="4798-C84F" TYPE="vfat" 
/dev/sdc6: LABEL="PORT11" UUID="8F31-9252" TYPE="vfat" 
/dev/sdc7: UUID="6A90D77790D747E9" LABEL="PORT12" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sdb13 on / type ext3 (rw,relatime,errors=remount-ro)
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
/dev/sda10 on /boot type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/otto/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=otto)
/dev/sdc7 on /media/PORT12 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdc6 on /media/PORT11 type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
/dev/sdc5 on /media/PORT10 type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)


================================ sda2/boot.ini: ================================

[boot loader]

timeout=15

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn










============================= sda10/grub/menu.lst: =============================

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
default saved

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=d64ef18f-14be-41d4-84dd-ccbb778967a9 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=dfb1be63-3f69-4a75-a52e-71443765e161

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

title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		dfb1be63-3f69-4a75-a52e-71443765e161
kernel		/vmlinuz-2.6.28-15-generic root=UUID=d64ef18f-14be-41d4-84dd-ccbb778967a9 ro quiet splash 
initrd		/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		dfb1be63-3f69-4a75-a52e-71443765e161
kernel		/vmlinuz-2.6.28-15-generic root=UUID=d64ef18f-14be-41d4-84dd-ccbb778967a9 ro  single
initrd		/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, memtest86+
uuid		dfb1be63-3f69-4a75-a52e-71443765e161
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda13.
title		SL_10.1 (on /dev/sda13)
root		(hd0,12)
kernel		/boot/vmlinuz root=/dev/hda13 ro append = "   resume=/dev/hda8  splash=silent showopts vga = 0x31a 
initrd		/boot/initrd
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda13.
title		Failsafe (on /dev/sda13)
root		(hd0,12)
kernel		/boot/vmlinuz root=/dev/hda13 ro append = "showopts ide=nodma apm=off acpi=off noresume nosmp noapic maxcpus=0 edd=off 3 vga = normal 
initrd		/boot/initrd
savedefault
boot


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Professional
rootnoverify	(hd0,1)
savedefault
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda4
title		Windows 95/98/Me
rootnoverify	(hd0,3)
savedefault
chainloader	+1


=================== sda10: Location of files loaded by Grub: ===================


  67.1GB: grub/menu.lst
  67.1GB: grub/stage2
  67.1GB: initrd.img-2.6.28-15-generic
  67.1GB: vmlinuz-2.6.28-15-generic

========================== sda13/boot/grub/menu.lst: ==========================

# Modified by YaST2. Last modification on Sa Okt  3 11:44:33 CEST 2009
color white/blue black/light-gray
default 0
timeout 8
gfxmenu (hd0,12)/boot/message

###Don't change this comment - YaST2 identifier: Original name: linux###
title SL_10.1
    root (hd0,12)
    kernel /boot/vmlinuz root=/dev/hda13 vga=0x31a resume=/dev/hda8  splash=silent showopts
    initrd /boot/initrd

###Don't change this comment - YaST2 identifier: Original name: failsafe###
title Failsafe
    root (hd0,12)
    kernel /boot/vmlinuz root=/dev/hda13 vga=normal showopts ide=nodma apm=off acpi=off noresume nosmp noapic maxcpus=0 edd=off 3
    initrd /boot/initrd

=============================== sda13/etc/fstab: ===============================

/dev/hda13           /                    ext3       acl,user_xattr        1 1
/dev/hda8            swap                 swap       defaults              0 0
proc                 /proc                proc       defaults              0 0
sysfs                /sys                 sysfs      noauto                0 0
debugfs              /sys/kernel/debug    debugfs    noauto                0 0
usbfs                /proc/bus/usb        usbfs      noauto                0 0
devpts               /dev/pts             devpts     mode=0620,gid=5       0 0
/dev/fd0             /media/floppy        auto       noauto,user,sync      0 0
/dev/hda14           /home                ext3       defaults              1 2
/dev/hdb5            /DOWNLOAD            vfat       users,gid=users,umask=0002,utf8=true 0 0

============================= sda13/etc/lilo.conf: =============================

# Modified by YaST2. Last modification on Mon Jun  4 13:56:00 CEST 2007
menu-scheme = Wb:kw:Wb:Wb
timeout = 80
lba32
change-rules
reset
read-only
prompt
default = SL_10.1
message = /boot/message
boot = /dev/hda13

image = /boot/vmlinuz
###Don't change this comment - YaST2 identifier: Original name: linux###
    label = SL_10.1
    append = "   resume=/dev/hda8  splash=silent showopts"
    vga = 0x31a
    initrd = /boot/initrd
    root = /dev/hda13

image = /boot/vmlinuz
###Don't change this comment - YaST2 identifier: Original name: failsafe###
    label = Failsafe
    append = "showopts ide=nodma apm=off acpi=off noresume nosmp noapic maxcpus=0 edd=off 3"
    vga = normal
    initrd = /boot/initrd
    root = /dev/hda13

=================== sda13: Location of files loaded by Grub: ===================


  75.2GB: boot/grub/menu.lst
  74.0GB: boot/grub/stage2
  72.6GB: boot/initrd
  72.6GB: boot/initrd-2.6.16.27-0.9-default
  72.4GB: boot/vmlinuz
  72.4GB: boot/vmlinuz-2.6.16.27-0.9-default

========================== sdb13/boot/grub/menu.lst: ==========================

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
default saved

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=d64ef18f-14be-41d4-84dd-ccbb778967a9 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=dfb1be63-3f69-4a75-a52e-71443765e161

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

title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		dfb1be63-3f69-4a75-a52e-71443765e161
kernel		/vmlinuz-2.6.28-15-generic root=UUID=d64ef18f-14be-41d4-84dd-ccbb778967a9 ro quiet splash 
initrd		/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		dfb1be63-3f69-4a75-a52e-71443765e161
kernel		/vmlinuz-2.6.28-15-generic root=UUID=d64ef18f-14be-41d4-84dd-ccbb778967a9 ro  single
initrd		/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, memtest86+
uuid		dfb1be63-3f69-4a75-a52e-71443765e161
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda13.
title		SL_10.1 (on /dev/sda13)
root		(hd0,12)
kernel		/boot/vmlinuz root=/dev/hda13 ro append = "   resume=/dev/hda8  splash=silent showopts vga = 0x31a 
initrd		/boot/initrd
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda13.
title		Failsafe (on /dev/sda13)
root		(hd0,12)
kernel		/boot/vmlinuz root=/dev/hda13 ro append = "showopts ide=nodma apm=off acpi=off noresume nosmp noapic maxcpus=0 edd=off 3 vga = normal 
initrd		/boot/initrd
savedefault
boot


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Professional
rootnoverify	(hd0,1)
savedefault
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda4
title		Windows 95/98/Me
rootnoverify	(hd0,3)
savedefault
chainloader	+1


=============================== sdb13/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sdb13 :
UUID=d64ef18f-14be-41d4-84dd-ccbb778967a9 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda10 :
UUID=dfb1be63-3f69-4a75-a52e-71443765e161 /boot ext3 relatime 0 2
/dev/sda8 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0

=================== sdb13: Location of files loaded by Grub: ===================


 240.3GB: boot/grub/menu.lst
 240.3GB: boot/grub/stage2
 240.3GB: boot/initrd.img-2.6.28-15-generic
 240.3GB: boot/vmlinuz-2.6.28-15-generic
 240.3GB: initrd.img
 240.3GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1

00000000  eb 44 90 44 65 6c 6c 20  34 2e 31 00 02 04 01 00  |.D.Dell 4.1.....|
00000010  02 00 02 00 00 f8 3f 00  3f 00 ff 00 3f 00 00 00  |......?.?...?...|
00000020  c5 fa 00 00 80 00 29 11  0a d2 07 44 65 6c 6c 55  |......)....DellU|
00000030  74 69 6c 69 74 79 46 41  54 31 36 20 20 20 00 00  |tilityFAT16   ..|
00000040  00 00 00 00 00 00 fa b8  00 00 8e d0 bc fc 7b fb  |..............{.|
00000050  fc 8e d8 ff 0e 13 04 8b  0e 13 04 c1 e1 06 8e c1  |................|
00000060  b9 00 01 33 f6 33 ff f3  66 a5 c7 06 72 04 45 44  |...3.3..f...r.ED|
00000070  0e 1f 8e c0 e8 1d 01 0f  82 b9 00 66 0f b7 06 16  |...........f....|
00000080  7c 66 d1 e0 66 0f b7 1e  0e 7c 66 03 c3 66 03 06  ||f..f....|f..f..|
00000090  1c 7c 66 a3 3e 7c a1 11  7c ba 20 00 f7 e2 bb 00  |.|f.>|..|. .....|
000000a0  02 f7 f3 8b e8 bb 00 05  e8 a5 00 0f 82 85 00 ba  |................|
000000b0  10 00 b9 0b 00 be e0 7d  8b fb f3 a6 74 13 83 c3  |.......}....t...|
000000c0  20 4a 75 ee 66 ff 06 3e  7c 4d 75 d9 be d4 7d eb  | Ju.f..>|Mu...}.|
000000d0  6b 66 0f b7 06 11 7c 66  ba 20 00 00 00 66 f7 e2  |kf....|f. ...f..|
000000e0  66 0f b7 0e 0b 7c 66 03  c1 66 48 66 f7 f1 66 01  |f....|f..fHf..f.|
000000f0  06 3e 7c 66 a1 3e 7c 66  26 a3 fc 7b 66 26 0f b7  |.>|f.>|f&..{f&..|
00000100  47 1a 8b f8 2d 02 00 66  0f b6 1e 0d 7c 66 f7 e3  |G...-..f....|f..|
00000110  66 01 06 3e 7c bb 00 07  bd 04 00 e8 32 00 72 14  |f..>|.......2.r.|
00000120  81 c3 00 02 66 ff 06 3e  7c 4d 75 ef bd 00 7c ea  |....f..>|Mu...|.|
00000130  00 02 70 00 be c7 7d eb  03 be d4 7d e8 02 00 eb  |..p...}....}....|
00000140  fe ac 3c 00 74 09 b4 0e  bb 07 00 cd 10 eb f2 c3  |..<.t...........|
00000150  66 a1 3e 7c 66 33 d2 66  0f b7 0e 18 7c 66 f7 f1  |f.>|f3.f....|f..|
00000160  66 42 88 16 45 7c 66 33  d2 66 0f b7 0e 1a 7c 66  |fB..E|f3.f....|f|
00000170  f7 f1 88 16 44 7c a3 42  7c b8 01 02 8b 0e 42 7c  |....D|.B|.....B||
00000180  c0 e5 06 0a 2e 45 7c 86  e9 8a 36 44 7c 8a 16 24  |.....E|...6D|..$|
00000190  7c cd 13 c3 26 80 3e c2  07 06 74 2a b8 01 02 bb  ||...&.>...t*....|
000001a0  00 06 b9 01 00 b6 00 8a  16 24 7c cd 13 72 17 26  |.........$|..r.&|
000001b0  c6 06 c2 07 06 b8 01 03  bb 00 06 b9 01 00 b6 00  |................|
000001c0  8a 16 24 7c cd 13 c3 44  69 73 6b 20 65 72 72 6f  |..$|...Disk erro|
000001d0  72 0d 0a 00 4e 6f 20 6c  6f 61 64 65 72 0d 0a 00  |r...No loader...|
000001e0  49 4f 20 20 20 20 20 20  53 59 53 00 00 00 00 00  |IO      SYS.....|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

---

### Post by arrange on 2009-10-03
Sorry, that's too much of a mess for me... :) You've got 4(!) different bootloaders (Dell, Win, Lilo, Grub), several OSs and partitions, and all scattered throughout 3 drives... 

If I were you, I would tidy up a little bit first ;-)

---

### Post by presence1960 on 2009-10-03
> **keerthanak said:**
> [CENTER][CENTER]**[click here to know more]("http://www.google.com")                                                      **[/CENTER]
[/CENTER]

That is one of the most unhelpful posts I have ever seen. I hope you never have a problem that you need some help with!

It would have been better had you posted nothing.

---

### Post by ottosykora on 2009-10-04
> **arrange said:**
> Sorry, that's too much of a mess for me... :) You've got 4(!) different bootloaders (Dell, Win, Lilo, Grub), several OSs and partitions, and all scattered throughout 3 drives... 

If I were you, I would tidy up a little bit first ;-)

Well the things might be strange, but how to tide up?
The computer has one dell system partition, this can not be removed probably.
There is no lilo there, but i think the script understands the original bootmanager from powerquest, the bootmagic as lilo. This is the bootmanager on this one since it exist.
The suse linux has its grub in the boot sector of the root partition, the ubuntu has separate boot partition on the first drive and the ubuntu root is on drive 2.
Windows partitions are xp ans w98.
The only problem is, that none of the grubs , neither in the suse partition, nor the one the boot partition of ubuntu seems to be working after cloning of the drive 1.

---

### Post by CrazySat on 2009-11-05
Hi all,

I please need your help.

I cloned my ide2 hard disk of 20 GB to a new 200 GB hard drive and Ubuntu while booting is showing me some logs  with "I2C Master_Xfer Failed" error.
After that is normally running.

I paste here the script output.

Thank you for your help.

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

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

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.3 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xba41e824

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   133,323,434   133,323,372   7 HPFS/NTFS
/dev/sda2         133,323,435   390,716,864   257,393,430   f W95 Ext d (LBA)
/dev/sda5         133,323,498   219,174,794    85,851,297   7 HPFS/NTFS
/dev/sda6         219,174,858   305,058,284    85,883,427   7 HPFS/NTFS
/dev/sda7         305,058,348   390,716,864    85,658,517   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5453b3d6

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   206,885,069   206,885,007   7 HPFS/NTFS
/dev/sdb2         206,885,070   388,258,919   181,373,850  83 Linux
/dev/sdb3         388,258,920   390,716,864     2,457,945  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="36949FF3D4888EB6" TYPE="ntfs" 
/dev/sda5: UUID="549CC8E99CC8C728" TYPE="ntfs" 
/dev/sda6: UUID="8EE49A66E49A5077" TYPE="ntfs" 
/dev/sda7: UUID="6048779148776526" TYPE="ntfs" 
/dev/sdb1: UUID="E0C48CEEC48CC7EC" TYPE="ntfs" 
/dev/sdb2: UUID="45a1ba6a-ba66-4ae8-9ed8-1e70ce66cccc" TYPE="ext3" 
/dev/sdb3: TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sdb2 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-25-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/fabrizio/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=fabrizio)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn 

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
# kopt=root=UUID=45a1ba6a-ba66-4ae8-9ed8-1e70ce66cccc ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,1)

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

title        Ubuntu 8.04.3 LTS, kernel 2.6.24-25-generic
root        (hd1,1)
kernel        /boot/vmlinuz-2.6.24-25-generic root=UUID=45a1ba6a-ba66-4ae8-9ed8-1e70ce66cccc ro quiet splash
initrd        /boot/initrd.img-2.6.24-25-generic
quiet

title        Ubuntu 8.04.3 LTS, kernel 2.6.24-25-generic (recovery mode)
root        (hd1,1)
kernel        /boot/vmlinuz-2.6.24-25-generic root=UUID=45a1ba6a-ba66-4ae8-9ed8-1e70ce66cccc ro single
initrd        /boot/initrd.img-2.6.24-25-generic

title        Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic
root        (hd1,1)
kernel        /boot/vmlinuz-2.6.24-24-generic root=UUID=45a1ba6a-ba66-4ae8-9ed8-1e70ce66cccc ro quiet splash
initrd        /boot/initrd.img-2.6.24-24-generic
quiet

title        Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic (recovery mode)
root        (hd1,1)
kernel        /boot/vmlinuz-2.6.24-24-generic root=UUID=45a1ba6a-ba66-4ae8-9ed8-1e70ce66cccc ro single
initrd        /boot/initrd.img-2.6.24-24-generic

title        Ubuntu 8.04.3 LTS, memtest86+
root        (hd1,1)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
root        (hd0,0)
savedefault
makeactive
chainloader    +1


=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb2
UUID=45a1ba6a-ba66-4ae8-9ed8-1e70ce66cccc /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb3
UUID=7c2258f7-8d57-4f19-bebd-df4d7d1c3909 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb2: Location of files loaded by Grub: ===================


 107.2GB: boot/grub/menu.lst
 107.3GB: boot/grub/stage2
 107.2GB: boot/initrd.img-2.6.24-24-generic
 107.3GB: boot/initrd.img-2.6.24-24-generic.bak
 107.3GB: boot/initrd.img-2.6.24-25-generic
 107.3GB: boot/initrd.img-2.6.24-25-generic.bak
 107.3GB: boot/vmlinuz-2.6.24-24-generic
 107.3GB: boot/vmlinuz-2.6.24-25-generic
 107.3GB: initrd.img
 107.2GB: initrd.img.old
 107.3GB: vmlinuz
 107.3GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf sdg sdh sdi sdj 
```

---

### Post by marmaladejackson on 2009-11-05
Hi There,

Just trying to understand, did you just copy your old hard drive to the new one, switch the connections on the motherboard, and reboot?

Brian

---

### Post by CrazySat on 2009-11-05
Hi marmaladejackson,
thanks for answering.

I had cloned original hard disk of 20 GB to a new larger hard disk of 200 GB and
at the boot I got that error.
I had used to clone disk  Acronis Home 2010 "clone" function.
I also tryed following this explaination, but again no luck.
[http://www.linux.com/learn/tutorials/8225-clone-your-ubuntu-installation-onto-a-new-hard-disk](http://www.linux.com/learn/tutorials/8225-clone-your-ubuntu-installation-onto-a-new-hard-disk)

Finally it seems it worked a simple copy & paste with GParted Live

---

