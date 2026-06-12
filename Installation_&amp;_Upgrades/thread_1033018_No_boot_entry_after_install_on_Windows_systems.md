---
title: "No boot entry after install on Windows systems"
date: 2009-01-06
forum: Installation &amp; Upgrades
---

### Post by TSellers on 2009-01-06
I've tried intalling ubuntu on two different drives on the same computer, and on my laptop. I chose an Ext3 partation and told it to format it. While I created the partition first in Parition Magic once, then with Paragon, but each time I let the installer repartition and format the drives. The last time, in desperation, I told it to format the whole drive using the guided mode.

While the install says it has completed, when I reboot all I see are the Windows installations. The drive that has the first installation of ubuntu also has the swap and Ext3 partitions on it as well as an NTFS partition.

Do I need to run some sort of linux specific boot manager separately to modify the MBR of my drive before I can use Ubuntu?

---

### Post by jken146 on 2009-01-07
The Ubuntu installer should install GRUB (the bootloader) at the end of the installation procedure.

---

### Post by TSellers on 2009-01-08
Thanks for the reply. So as there seems to be a problem, what should I do to see what happened to interfere with the proper functioning of GRUB each time I try to install on this computer?

---

### Post by kranny on 2009-01-08
Try installing grub from the live cd...
Insert the Live Cd and fire up a terminal
type sudo grub...
and then type "find /boot/grub/stage1" 

You get sumthin like (hd0,x)
then type root (hd0,x)
followed by setup (hd0)
U should be done with

---

### Post by caljohnsmith on 2009-01-08
TSellers, in order to get a clearer picture of your setup, how about booting your Live CD (the Ubuntu install CD), open a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. If you don't have internet connectivity when using the Live CD, you can instead right-click [this link]("http://home.comcast.net/~ubuntu_grub/boot_info_script.txt") to the script in your web browser, choose "Save link as...", save the "boot_info_script.txt" file, transfer it to your Ubuntu desktop on the Live CD via USB stick, floppy, or however you want to do it, and then do the following in a terminal:
```
sudo bash ~/Desktop/boot_info_script.txt
```
The results of that script will help clarify your setup and hopefully what your problem might be.

---

### Post by TSellers on 2009-01-09
THanks to both for replies.

1: I tried the first suggestion. I got messages as noted by Kranny, everything went as noted and I got a message I believe something like "success". However when I rebooted, still nothing appears in the boot menu.

2: Moved on to next post:
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #3 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => Grub0.97 is installed in the MBR of /dev/sdc and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  Geometry: 240 Heads and 63 sectors per Track. No 
                       errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       Extended Partition

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  Geometry: 240 Heads and 63 sectors per Track.
    Operating System:  Windows XP
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: you must specify the filesystem type

sdb7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst /grub

sdb8: _________________________________________________________________________

    File system:       swap

sdc1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sdc2: _________________________________________________________________________

    File system:       Extended Partition

sdc5: _________________________________________________________________________

    File system:       swap

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x13e5233d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   488392064   244196001   42  SFS

sfdisk -V /dev/sda:

/dev/sda: OK

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
240 heads, 63 sectors/track, 32301 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x49fdba33

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   269362799   134681368+   7  HPFS/NTFS
/dev/sdb2       269362924   488391119   109514098    f  W95 Ext'd (LBA)
/dev/sdb5       269362925   310322879    20479977+   7  HPFS/NTFS
/dev/sdb6       310323005   453690781    71683888+  83  Linux
/dev/sdb7       453690783   484202879    15256048+  83  Linux
/dev/sdb8       484202943   488391119     2094088+  82  Linux swap / Solaris

sfdisk -V /dev/sdb:

Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Warning: partition 1 does not end at a cylinder boundary

Drive sdc: _____________________________________________________________________

fdisk -lu /dev/sdc:

Disk /dev/sdc: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000202ff

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63    74862899    37431418+  83  Linux
/dev/sdc2        74862900    78156224     1646662+   5  Extended
/dev/sdc5        74862963    78156224     1646631   82  Linux swap / Solaris

sfdisk -V /dev/sdc:

Warning: no primary partition is marked bootable (active)
This does not matter for LILO, but the DOS MBR will not boot this disk.
/dev/sdc: OK

Drive sdd: _____________________________________________________________________

fdisk -lu /dev/sdd:

Disk /dev/sdd: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x28dd6ba1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *          63   234436544   117218241    c  W95 FAT32 (LBA)

sfdisk -V /dev/sdd:

/dev/sdd: OK

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="A030186C30184BA2" LABEL="250_Backup" TYPE="ntfs" 
/dev/sdb1: UUID="48446F17446F0752" TYPE="ntfs" 
/dev/sdb5: UUID="6CC8784AC8781494" TYPE="ntfs" 
/dev/sdb7: UUID="663f9eb0-efdf-4a03-8762-5ccf7f99d686" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb8: UUID="48dfddbd-e810-4ce7-a1e6-1e6955bac424" TYPE="swap" 
/dev/sdc1: UUID="f423891d-002c-4422-8120-12c6a468d95b" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc5: UUID="73a1f5e0-4e1c-4142-9e40-872352c741d5" TYPE="swap" 
/dev/loop0: TYPE="squashfs" 
/dev/sdd1: LABEL="WD Passport" UUID="EB58-D385" TYPE="vfat" 

=============================== "mount" output: ===============================

/proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
none on /proc type proc (rw)
none on /dev/pts type devpts (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
rootfs on / type rootfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/scd0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdd1 on /media/WD Passport type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)

================================ sdb1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Professional x64 Edition" /noexecute=optin /fastdetect
multi(0)disk(0)rdisk(0)partition(1)\WIN_2003="Windows Server 2003, Web" /fastdetect

============================= sdb7/grub/menu.lst: =============================

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
# kopt=root=UUID=d65dfcfd-2168-482e-89bb-40fd50b95703 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=663f9eb0-efdf-4a03-8762-5ccf7f99d686

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
uuid		663f9eb0-efdf-4a03-8762-5ccf7f99d686
kernel		/vmlinuz-2.6.27-7-generic root=UUID=d65dfcfd-2168-482e-89bb-40fd50b95703 ro quiet splash 
initrd		/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		663f9eb0-efdf-4a03-8762-5ccf7f99d686
kernel		/vmlinuz-2.6.27-7-generic root=UUID=d65dfcfd-2168-482e-89bb-40fd50b95703 ro  single
initrd		/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		663f9eb0-efdf-4a03-8762-5ccf7f99d686
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows NT/2000/XP (loader)
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


================================== sdb7/grub: ==================================

total 220
drwxr-xr-x 3 root root   4096 2008-12-29 09:55 .
drwxr-xr-x 4 root root   4096 2008-12-29 09:55 ..
-rw-r--r-- 1 root root    197 2008-12-29 09:55 default
-rw-r--r-- 1 root root     30 2008-12-29 09:55 device.map
-rw-r--r-- 1 root root   8108 2008-12-29 09:55 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2008-12-29 09:55 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-12-29 09:55 installed-version
-rw-r--r-- 1 root root   8712 2008-12-29 09:55 jfs_stage1_5
-rw-r--r-- 1 root root   4624 2008-12-29 09:55 menu.lst
-rw-r--r-- 1 root root   7352 2008-12-29 09:55 minix_stage1_5
-rw-r--r-- 1 root root   9756 2008-12-29 09:55 reiserfs_stage1_5
drwxr-xr-x 2 root root   4096 2008-11-10 04:07 splashimages
-rw-r--r-- 1 root root    512 2008-12-29 09:55 stage1
-rw-r--r-- 1 root root 121460 2008-12-29 09:55 stage2
-rw-r--r-- 1 root root   9556 2008-12-29 09:55 xfs_stage1_5

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
# kopt=root=UUID=f423891d-002c-4422-8120-12c6a468d95b ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=f423891d-002c-4422-8120-12c6a468d95b

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
uuid		f423891d-002c-4422-8120-12c6a468d95b
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=f423891d-002c-4422-8120-12c6a468d95b ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		f423891d-002c-4422-8120-12c6a468d95b
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=f423891d-002c-4422-8120-12c6a468d95b ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		f423891d-002c-4422-8120-12c6a468d95b
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows NT/2000/XP (loader)
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc1
UUID=f423891d-002c-4422-8120-12c6a468d95b /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdc5
UUID=73a1f5e0-4e1c-4142-9e40-872352c741d5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sdc1/boot: ==================================

total 13220
drwxr-xr-x  3 root root    4096 2009-01-06 15:57 .
drwxr-xr-x 21 root root    4096 2009-01-06 15:57 ..
-rw-r--r--  1 root root  507665 2008-11-04 21:00 abi-2.6.27-7-generic
-rw-r--r--  1 root root   91364 2008-11-04 21:00 config-2.6.27-7-generic
drwxr-xr-x  3 root root    4096 2009-01-06 15:58 grub
-rw-r--r--  1 root root 9477640 2009-01-06 15:57 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root  124152 2008-09-11 20:11 memtest86+.bin
-rw-r--r--  1 root root 1029585 2008-11-04 21:00 System.map-2.6.27-7-generic
-rw-r--r--  1 root root    1073 2008-11-04 21:02 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root 2244272 2008-10-24 08:29 vmlinuz-2.6.27-7-generic

=============================== sdc1/boot/grub: ===============================

total 220
drwxr-xr-x 3 root root   4096 2009-01-06 15:58 .
drwxr-xr-x 3 root root   4096 2009-01-06 15:57 ..
-rw-r--r-- 1 root root    197 2009-01-06 15:57 default
-rw-r--r-- 1 root root     45 2009-01-06 15:57 device.map
-rw-r--r-- 1 root root   8108 2009-01-06 15:57 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2009-01-06 15:57 fat_stage1_5
-rw-r--r-- 1 root root     16 2009-01-06 15:57 installed-version
-rw-r--r-- 1 root root   8712 2009-01-06 15:57 jfs_stage1_5
-rw-r--r-- 1 root root   4649 2009-01-06 15:58 menu.lst
-rw-r--r-- 1 root root   7352 2009-01-06 15:57 minix_stage1_5
-rw-r--r-- 1 root root   9756 2009-01-06 15:57 reiserfs_stage1_5
drwxr-xr-x 2 root root   4096 2008-11-10 04:07 splashimages
-rw-r--r-- 1 root root    512 2009-01-06 15:57 stage1
-rw-r--r-- 1 root root 121460 2009-01-06 15:57 stage2
-rw-r--r-- 1 root root   9556 2009-01-06 15:57 xfs_stage1_5

=============================== StdErr Messages: ===============================

Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.

```

---

### Post by caljohnsmith on 2009-01-09
It looks like your Ubuntu 40 GB sdc drive should be be ready to boot Ubuntu just fine. One small detail that might prevent it though is none of the partitions on the sdc drive are marked as bootable, and some BIOSes won't boot a drive that doesn't have one partition marked as bootable. So I would suggest first doing:
```
sudo sfdisk -A1 /dev/sdc
```
And then set your BIOS to boot the 40 GB sdc drive, and it looks like you should be able to boot into that Ubuntu install with no issues. The Ubuntu install on your 250 GB sdb drive is a different matter though, because for some reason the Ubuntu sdb6 partition couldn't be mounted. I would recommend using Ubuntu's Partition Editor gparted to reformat the sdb6 partition, and then try installing Ubuntu to that drive again. And if you want to avoid booting headaches, I would suggest clicking on the "advanced" button near the end of the installation and specify to have Grub installed to /dev/sdb, or the drive you are installing Ubuntu to. That way if you want to boot that drive, you would just change your BIOS to boot the drive, and you should be able to boot into Ubuntu with no problems if all goes well. Once you get Ubuntu booting OK, I can help you add an entry in your Grub menu to boot Windows if you want. Let me know how it goes or if you run into problems.

---

### Post by TSellers on 2009-01-11
Thanks for that great advice. Due to server being down I couldn't get back with reply on Friday/Saturday.

So partial success. I now see the Grub boot loader and it works and also will boot me into Windows, which is great. However, I see a few different boot choices for Ubuntu, but none will intialize the OS. This is how far it gets:

line 231: cannot open /root/dev/console: no such file
and:
- attempted to kill init!

Is that a straightforward fix?

---

### Post by caljohnsmith on 2009-01-11
That's a really strange error, because it looks like the init service is looking for /root/dev/console, when it should be /dev/console I think. When you boot the Live CD that you used to install Ubuntu, have you tried selecting the option to check the CD for defects? I would do that if you haven't all ready, because I'm wondering how you could get such a strange booting error when its a fresh Ubuntu install. Did you happen to run an MD5 sum on the Ubuntu ISO you downloaded? It would probably be worth checking that your downloaded ISO is OK. Good luck and let me know how that goes.

---

### Post by TSellers on 2009-01-12
Thanks, tried to reinstall, here's what I get now:

[IMG]http://www.mparam.com/images/ubuntu.jpg[/IMG]

---

### Post by caljohnsmith on 2009-01-12
It looks like there might be some sort of hardware compatibility issue going on, because the errors you show make reference to a 8139 rev 10 chip, which the error says is not 8139C compatible chip. To get some clues which hardware element in your setup the error is referring to, how about posting the output of:
```
sudo lshw
```
And we can work from there.

---

### Post by TSellers on 2009-01-12
OK, thanks.

Looks like 8139 is a chip on the Network card. There are 2 Network cards in the system, one is embedded in the MOBO, the other is PCI. One for LAN and one for WAN. Funny, both seem to work OK when booted from the CD:

```
             description: PCI bridge
             product: VT8237/VX700 PCI Bridge
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci pm bus_master cap_list
        *-pci:1
             description: PCI bridge
             product: P4M890 PCI to PCI Bridge Controller
             vendor: VIA Technologies, Inc.
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress pm msi ht bus_master cap_list
             configuration: driver=pcieport-driver
           *-display UNCLAIMED
                description: VGA compatible controller
                product: G70 [GeForce 7300 GT]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: latency=0
        *-pci:2
             description: PCI bridge
             product: P4M890 PCI to PCI Bridge Controller
             vendor: VIA Technologies, Inc.
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress pm msi ht bus_master cap_list
             configuration: driver=pcieport-driver
           *-storage
                description: SATA controller
                product: JMicron 20360/20363 AHCI Controller
                vendor: JMicron Technologies, Inc.
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm pciexpress bus_master cap_list
                configuration: driver=ahci latency=0 module=ahci
           *-ide
                description: IDE interface
                product: JMicron 20360/20363 AHCI Controller
                vendor: JMicron Technologies, Inc.
                physical id: 0.1
                bus info: pci@0000:03:00.1
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: ide pm bus_master cap_list
                configuration: driver=pata_jmicron latency=0 module=pata_jmicron
        *-ide:0
             description: IDE interface
             product: VT8237A SATA 2-Port Controller
             vendor: VIA Technologies, Inc.
             physical id: f
             bus info: pci@0000:00:0f.0
             logical name: scsi5
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=sata_via latency=32 module=sata_via
           *-disk
                description: ATA Disk
                product: SAMSUNG SP2504C
                physical id: 0.0.0
                bus info: scsi@5:0.0.0
                logical name: /dev/sda
                version: VT10
                serial: S09QJ1UYC18573
                size: 232GiB (250GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=13e5233d
              *-volume
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@5:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 4e8f727d-ce7d-a14d-9e54-043ba34318bc
                   size: 232GiB
                   capacity: 232GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2006-01-08 01:01:43 filesystem=ntfs label=250_Backup state=clean
        *-ide:1
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: f.1
             bus info: pci@0000:00:0f.1
             logical name: scsi8
             logical name: scsi9
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=pata_via latency=32 module=pata_via
           *-disk:0
                description: ATA Disk
                product: WDC WD2500JB-00R
                vendor: Western Digital
                physical id: 0
                bus info: scsi@8:0.0.0
                logical name: /dev/sdb
                version: 20.0
                serial: WD-WCANKM420849
                size: 232GiB (250GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=49fdba33
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@8:0.0.0,1
                   logical name: /dev/sdb1
                   version: 3.1
                   serial: 381642b9-09fd-8f4a-841f-f729e78aa591
                   size: 128GiB
                   capacity: 128GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2008-11-11 14:40:22 filesystem=ntfs state=clean
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@8:0.0.0,2
                   logical name: /dev/sdb2
                   size: 87GiB
                   capacity: 87GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: HPFS/NTFS partition
                      physical id: 5
                      logical name: /dev/sdb5
                      capacity: 19GiB
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sdb6
                      capacity: 68GiB
              *-volume:2
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 3
                   bus info: scsi@8:0.0.0,3
                   logical name: /dev/sdb3
                   version: 1.0
                   serial: a50c7092-d098-cbde-be2f-a24732cb73d8
                   size: 16GiB
                   capacity: 16GiB
                   capabilities: primary journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2009-01-09 17:47:57 filesystem=ext3 modified=2009-01-09 17:47:57 mounted=2009-01-09 17:47:57 state=clean
           *-disk:1
                description: ATA Disk
                product: ST340014A
                vendor: Seagate
                physical id: 0.1.0
                bus info: scsi@8:0.1.0
                logical name: /dev/sdc
                version: 3.04
                serial: 3JX0CBC9
                size: 37GiB (40GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000202ff
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@8:0.1.0,1
                   logical name: /dev/sdc1
                   version: 1.0
                   serial: f423891d-002c-4422-8120-12c6a468d95b
                   size: 31GiB
                   capacity: 31GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2009-01-06 15:34:47 filesystem=ext3 modified=2009-01-09 17:33:09 state=clean
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@8:0.1.0,2
                   logical name: /dev/sdc2
                   size: 6204MiB
                   capacity: 6204MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sdc5
                      capacity: 1608MiB
                      capabilities: nofs
                 *-logicalvolume:1
                      description: HPFS/NTFS partition
                      physical id: 6
                      logical name: /dev/sdc6
                      capacity: 4596MiB
           *-cdrom
                description: DVD-RAM writer
                product: DRW-1608P3S
                vendor: ASUS
                physical id: 1
                bus info: scsi@9:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                logical name: /cdrom
                version: 1.24
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,noatime state=mounted status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom
                   logical name: /cdrom
                   configuration: mount.fstype=iso9660 mount.options=ro,noatime state=mounted
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10
             bus info: pci@0000:00:10.0
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.2
             bus info: pci@0000:00:10.2
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.3
             bus info: pci@0000:00:10.3
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: 10.4
             bus info: pci@0000:00:10.4
             version: 86
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ehci_hcd latency=32 module=ehci_hcd
        *-isa
             description: ISA bridge
             product: VT8237A PCI to ISA Bridge
             vendor: VIA Technologies, Inc.
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa pm cap_list
             configuration: latency=0
        *-pci:3
             description: PCI bridge
             product: VT8237A Host Bridge
             vendor: VIA Technologies, Inc.
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci ht bus_master cap_list
           *-multimedia
                description: Audio device
                product: VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller)
                vendor: VIA Technologies, Inc.
                physical id: 1
                bus info: pci@0000:04:01.0
                version: 10
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:4
             description: PCI bridge
             product: VT8237A PCI to PCI Bridge
             vendor: VIA Technologies, Inc.
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci ht bus_master cap_list
           *-network:0
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 5
                bus info: pci@0000:05:05.0
                logical name: eth1
                version: 10
                serial: 00:40:f4:32:5b:37
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.0.121 latency=32 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
           *-network:1
                description: Ethernet interface
                product: RTL-8110SC/8169SC Gigabit Ethernet
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 7
                bus info: pci@0000:05:07.0
                logical name: eth0
                version: 10
                serial: 00:18:f3:bc:26:c1
                size: 100MB/s
                capacity: 1GB/s
                width: 32 bits
                clock: 66MHz
                capabilities: pm bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.100 latency=64 link=yes maxlatency=64 mingnt=32 module=r8169 multicast=yes port=twisted pair speed=100MB/s
     *-pci:1
          description: Host bridge
          product: P4M890 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 101
          bus info: pci@0000:00:00.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: P4M890 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 102
          bus info: pci@0000:00:00.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: P4M890 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 103
          bus info: pci@0000:00:00.3
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: P4M890 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 104
          bus info: pci@0000:00:00.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: P4M890 Security Device
          vendor: VIA Technologies, Inc.
          physical id: 105
          bus info: pci@0000:00:00.6
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: P4M890 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 106
          bus info: pci@0000:00:00.7
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: VT8251 Ultra VLINK Controller
          vendor: VIA Technologies, Inc.
          physical id: 107
          bus info: pci@0000:00:11.7
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: latency=32
     *-scsi:0
          physical id: 2
          bus info: usb@5:4
          logical name: scsi3
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: 2500BEV External
             vendor: WD
             physical id: 0.0.0
             bus info: scsi@3:0.0.0
             logical name: /dev/sdd
             version: 1.05
             serial: WD-WXE408DM8463
             size: 232GiB (250GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=4 signature=9c8160ad
           *-volume
                description: Windows FAT volume
                vendor: HOPPY FS
                physical id: 1
                bus info: scsi@3:0.0.0,1
                logical name: /dev/sdd1
                logical name: /media/SATELLITE
                version: FAT32
                serial: 0000-0000
                size: 232GiB
                capacity: 232GiB
                capabilities: primary bootable fat initialized
                configuration: FATs=2 filesystem=fat label=HOPPY LABEL mount.fstype=vfat mount.options=rw,nosuid,nodev,uid=999,fmask=0077,dmask=0077,codepage=cp437,iocharset=iso8859-1,shortname=mixed,utf8,flush state=mounted
     *-scsi:1
          physical id: 3
          bus info: usb@5:3
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: 2500BEV External
             vendor: WD
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sde
             version: 1.05
             serial: WD-WXE508SZA370
             size: 232GiB (250GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=4 signature=5b6ac646
           *-volume
                description: Windows FAT volume
                vendor: MSWIN4.1
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sde1
                logical name: /media/My Passport
                version: FAT32
                serial: 46f6-8546
                size: 232GiB
                capacity: 232GiB
                capabilities: primary fat initialized
                configuration: FATs=2 filesystem=fat label=My Passport mount.fstype=vfat mount.options=rw,nosuid,nodev,uid=999,fmask=0077,dmask=0077,codepage=cp437,iocharset=iso8859-1,shortname=mixed,utf8,flush state=mounted
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: c2:b7:5e:72:0b:a2
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
             description: PCI bridge
             product: VT8237/VX700 PCI Bridge
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci pm bus_master cap_list
        *-pci:1
             description: PCI bridge
             product: P4M890 PCI to PCI Bridge Controller
             vendor: VIA Technologies, Inc.
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress pm msi ht bus_master cap_list
             configuration: driver=pcieport-driver
           *-display UNCLAIMED
                description: VGA compatible controller
                product: G70 [GeForce 7300 GT]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: latency=0
        *-pci:2
             description: PCI bridge
             product: P4M890 PCI to PCI Bridge Controller
             vendor: VIA Technologies, Inc.
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress pm msi ht bus_master cap_list
             configuration: driver=pcieport-driver
           *-storage
                description: SATA controller
                product: JMicron 20360/20363 AHCI Controller
                vendor: JMicron Technologies, Inc.
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm pciexpress bus_master cap_list
                configuration: driver=ahci latency=0 module=ahci
           *-ide
                description: IDE interface
                product: JMicron 20360/20363 AHCI Controller
                vendor: JMicron Technologies, Inc.
                physical id: 0.1
                bus info: pci@0000:03:00.1
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: ide pm bus_master cap_list
                configuration: driver=pata_jmicron latency=0 module=pata_jmicron
        *-ide:0
             description: IDE interface
             product: VT8237A SATA 2-Port Controller
             vendor: VIA Technologies, Inc.
             physical id: f
             bus info: pci@0000:00:0f.0
             logical name: scsi5
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=sata_via latency=32 module=sata_via
           *-disk
                description: ATA Disk
                product: SAMSUNG SP2504C
                physical id: 0.0.0
                bus info: scsi@5:0.0.0
                logical name: /dev/sda
                version: VT10
                serial: S09QJ1UYC18573
                size: 232GiB (250GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=13e5233d
              *-volume
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@5:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 4e8f727d-ce7d-a14d-9e54-043ba34318bc
                   size: 232GiB
                   capacity: 232GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2006-01-08 01:01:43 filesystem=ntfs label=250_Backup state=clean
        *-ide:1
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: f.1
             bus info: pci@0000:00:0f.1
             logical name: scsi8
             logical name: scsi9
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=pata_via latency=32 module=pata_via
           *-disk:0
                description: ATA Disk
                product: WDC WD2500JB-00R
                vendor: Western Digital
                physical id: 0
                bus info: scsi@8:0.0.0
                logical name: /dev/sdb
                version: 20.0
                serial: WD-WCANKM420849
                size: 232GiB (250GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=49fdba33
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@8:0.0.0,1
                   logical name: /dev/sdb1
                   version: 3.1
                   serial: 381642b9-09fd-8f4a-841f-f729e78aa591
                   size: 128GiB
                   capacity: 128GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2008-11-11 14:40:22 filesystem=ntfs state=clean
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@8:0.0.0,2
                   logical name: /dev/sdb2
                   size: 87GiB
                   capacity: 87GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: HPFS/NTFS partition
                      physical id: 5
                      logical name: /dev/sdb5
                      capacity: 19GiB
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sdb6
                      capacity: 68GiB
              *-volume:2
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 3
                   bus info: scsi@8:0.0.0,3
                   logical name: /dev/sdb3
                   version: 1.0
                   serial: a50c7092-d098-cbde-be2f-a24732cb73d8
                   size: 16GiB
                   capacity: 16GiB
                   capabilities: primary journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2009-01-09 17:47:57 filesystem=ext3 modified=2009-01-09 17:47:57 mounted=2009-01-09 17:47:57 state=clean
           *-disk:1
                description: ATA Disk
                product: ST340014A
                vendor: Seagate
                physical id: 0.1.0
                bus info: scsi@8:0.1.0
                logical name: /dev/sdc
                version: 3.04
                serial: 3JX0CBC9
                size: 37GiB (40GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000202ff
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@8:0.1.0,1
                   logical name: /dev/sdc1
                   version: 1.0
                   serial: f423891d-002c-4422-8120-12c6a468d95b
                   size: 31GiB
                   capacity: 31GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2009-01-06 15:34:47 filesystem=ext3 modified=2009-01-09 17:33:09 state=clean
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@8:0.1.0,2
                   logical name: /dev/sdc2
                   size: 6204MiB
                   capacity: 6204MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sdc5
                      capacity: 1608MiB
                      capabilities: nofs
                 *-logicalvolume:1
                      description: HPFS/NTFS partition
                      physical id: 6
                      logical name: /dev/sdc6
                      capacity: 4596MiB
           *-cdrom
                description: DVD-RAM writer
                product: DRW-1608P3S
                vendor: ASUS
                physical id: 1
                bus info: scsi@9:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                logical name: /cdrom
                version: 1.24
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,noatime state=mounted status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom
                   logical name: /cdrom
                   configuration: mount.fstype=iso9660 mount.options=ro,noatime state=mounted
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10
             bus info: pci@0000:00:10.0
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.2
             bus info: pci@0000:00:10.2
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.3
             bus info: pci@0000:00:10.3
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: 10.4
             bus info: pci@0000:00:10.4
             version: 86
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ehci_hcd latency=32 module=ehci_hcd
        *-isa
             description: ISA bridge
             product: VT8237A PCI to ISA Bridge
             vendor: VIA Technologies, Inc.
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa pm cap_list
             configuration: latency=0
        *-pci:3
             description: PCI bridge
             product: VT8237A Host Bridge
             vendor: VIA Technologies, Inc.
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci ht bus_master cap_list
           *-multimedia
                description: Audio device
                product: VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller)
                vendor: VIA Technologies, Inc.
                physical id: 1
                bus info: pci@0000:04:01.0
                version: 10
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:4
             description: PCI bridge
             product: VT8237A PCI to PCI Bridge
             vendor: VIA Technologies, Inc.
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci ht bus_master cap_list
           *-network:0
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 5
                bus info: pci@0000:05:05.0
                logical name: eth1
                version: 10
                serial: 00:40:f4:32:5b:37
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.0.121 latency=32 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
           *-network:1
                description: Ethernet interface
                product: RTL-8110SC/8169SC Gigabit Ethernet
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 7
                bus info: pci@0000:05:07.0
                logical name: eth0
                version: 10
                serial: 00:18:f3:bc:26:c1
                size: 100MB/s
                capacity: 1GB/s
                width: 32 bits
                clock: 66MHz
                capabilities: pm bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.100 latency=64 link=yes maxlatency=64 mingnt=32 module=r8169 multicast=yes port=twisted pair speed=100MB/s
     *-pci:1
          description: Host bridge
          product: P4M890 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 101
          bus info: pci@0000:00:00.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: P4M890 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 102
          bus info: pci@0000:00:00.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: P4M890 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 103
          bus info: pci@0000:00:00.3
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: P4M890 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 104
          bus info: pci@0000:00:00.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: P4M890 Security Device
          vendor: VIA Technologies, Inc.
          physical id: 105
          bus info: pci@0000:00:00.6
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: P4M890 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 106
          bus info: pci@0000:00:00.7
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: VT8251 Ultra VLINK Controller
          vendor: VIA Technologies, Inc.
          physical id: 107
          bus info: pci@0000:00:11.7
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: latency=32
     *-scsi:0
          physical id: 2
          bus info: usb@5:4
          logical name: scsi3
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: 2500BEV External
             vendor: WD
             physical id: 0.0.0
             bus info: scsi@3:0.0.0
             logical name: /dev/sdd
             version: 1.05
             serial: WD-WXE408DM8463
             size: 232GiB (250GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=4 signature=9c8160ad
           *-volume
                description: Windows FAT volume
                vendor: HOPPY FS
                physical id: 1
                bus info: scsi@3:0.0.0,1
                logical name: /dev/sdd1
                logical name: /media/SATELLITE
                version: FAT32
                serial: 0000-0000
                size: 232GiB
                capacity: 232GiB
                capabilities: primary bootable fat initialized
                configuration: FATs=2 filesystem=fat label=HOPPY LABEL mount.fstype=vfat mount.options=rw,nosuid,nodev,uid=999,fmask=0077,dmask=0077,codepage=cp437,iocharset=iso8859-1,shortname=mixed,utf8,flush state=mounted
     *-scsi:1
          physical id: 3
          bus info: usb@5:3
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: 2500BEV External
             vendor: WD
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sde
             version: 1.05
             serial: WD-WXE508SZA370
             size: 232GiB (250GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=4 signature=5b6ac646
           *-volume
                description: Windows FAT volume
                vendor: MSWIN4.1
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sde1
                logical name: /media/My Passport
                version: FAT32
                serial: 46f6-8546
                size: 232GiB
                capacity: 232GiB
                capabilities: primary fat initialized
                configuration: FATs=2 filesystem=fat label=My Passport mount.fstype=vfat mount.options=rw,nosuid,nodev,uid=999,fmask=0077,dmask=0077,codepage=cp437,iocharset=iso8859-1,shortname=mixed,utf8,flush state=mounted
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: c2:b7:5e:72:0b:a2
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
             description: PCI bridge
             product: VT8237/VX700 PCI Bridge
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci pm bus_master cap_list
        *-pci:1
             description: PCI bridge
             product: P4M890 PCI to PCI Bridge Controller
             vendor: VIA Technologies, Inc.
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress pm msi ht bus_master cap_list
             configuration: driver=pcieport-driver
           *-display UNCLAIMED
                description: VGA compatible controller
                product: G70 [GeForce 7300 GT]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: latency=0
        *-pci:2
             description: PCI bridge
             product: P4M890 PCI to PCI Bridge Controller
             vendor: VIA Technologies, Inc.
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress pm msi ht bus_master cap_list
             configuration: driver=pcieport-driver
           *-storage
                description: SATA controller
                product: JMicron 20360/20363 AHCI Controller
                vendor: JMicron Technologies, Inc.
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm pciexpress bus_master cap_list
                configuration: driver=ahci latency=0 module=ahci
           *-ide
                description: IDE interface
                product: JMicron 20360/20363 AHCI Controller
                vendor: JMicron Technologies, Inc.
                physical id: 0.1
                bus info: pci@0000:03:00.1
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: ide pm bus_master cap_list
                configuration: driver=pata_jmicron latency=0 module=pata_jmicron
        *-ide:0
             description: IDE interface
             product: VT8237A SATA 2-Port Controller
             vendor: VIA Technologies, Inc.
             physical id: f
             bus info: pci@0000:00:0f.0
             logical name: scsi5
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=sata_via latency=32 module=sata_via
           *-disk
                description: ATA Disk
                product: SAMSUNG SP2504C
                physical id: 0.0.0
                bus info: scsi@5:0.0.0
                logical name: /dev/sda
                version: VT10
                serial: S09QJ1UYC18573
                size: 232GiB (250GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=13e5233d
              *-volume
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@5:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 4e8f727d-ce7d-a14d-9e54-043ba34318bc
                   size: 232GiB
                   capacity: 232GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2006-01-08 01:01:43 filesystem=ntfs label=250_Backup state=clean
        *-ide:1
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: f.1
             bus info: pci@0000:00:0f.1
             logical name: scsi8
             logical name: scsi9
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=pata_via latency=32 module=pata_via
           *-disk:0
                description: ATA Disk
                product: WDC WD2500JB-00R
                vendor: Western Digital
                physical id: 0
                bus info: scsi@8:0.0.0
                logical name: /dev/sdb
                version: 20.0
                serial: WD-WCANKM420849
                size: 232GiB (250GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=49fdba33
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@8:0.0.0,1
                   logical name: /dev/sdb1
                   version: 3.1
                   serial: 381642b9-09fd-8f4a-841f-f729e78aa591
                   size: 128GiB
                   capacity: 128GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2008-11-11 14:40:22 filesystem=ntfs state=clean
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@8:0.0.0,2
                   logical name: /dev/sdb2
                   size: 87GiB
                   capacity: 87GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: HPFS/NTFS partition
                      physical id: 5
                      logical name: /dev/sdb5
                      capacity: 19GiB
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sdb6
                      capacity: 68GiB
              *-volume:2
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 3
                   bus info: scsi@8:0.0.0,3
                   logical name: /dev/sdb3
                   version: 1.0
                   serial: a50c7092-d098-cbde-be2f-a24732cb73d8
                   size: 16GiB
                   capacity: 16GiB
                   capabilities: primary journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2009-01-09 17:47:57 filesystem=ext3 modified=2009-01-09 17:47:57 mounted=2009-01-09 17:47:57 state=clean
           *-disk:1
                description: ATA Disk
                product: ST340014A
                vendor: Seagate
                physical id: 0.1.0
                bus info: scsi@8:0.1.0
                logical name: /dev/sdc
                version: 3.04
                serial: 3JX0CBC9
                size: 37GiB (40GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000202ff
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@8:0.1.0,1
                   logical name: /dev/sdc1
                   version: 1.0
                   serial: f423891d-002c-4422-8120-12c6a468d95b
                   size: 31GiB
                   capacity: 31GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2009-01-06 15:34:47 filesystem=ext3 modified=2009-01-09 17:33:09 state=clean
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@8:0.1.0,2
                   logical name: /dev/sdc2
                   size: 6204MiB
                   capacity: 6204MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sdc5
                      capacity: 1608MiB
                      capabilities: nofs
                 *-logicalvolume:1
                      description: HPFS/NTFS partition
                      physical id: 6
                      logical name: /dev/sdc6
                      capacity: 4596MiB
           *-cdrom
                description: DVD-RAM writer
                product: DRW-1608P3S
                vendor: ASUS
                physical id: 1
                bus info: scsi@9:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                logical name: /cdrom
                version: 1.24
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,noatime state=mounted status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom
                   logical name: /cdrom
                   configuration: mount.fstype=iso9660 mount.options=ro,noatime state=mounted
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10
             bus info: pci@0000:00:10.0
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.2
             bus info: pci@0000:00:10.2
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.3
             bus info: pci@0000:00:10.3
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: 10.4
             bus info: pci@0000:00:10.4
             version: 86
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ehci_hcd latency=32 module=ehci_hcd
        *-isa
             description: ISA bridge
             product: VT8237A PCI to ISA Bridge
             vendor: VIA Technologies, Inc.
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa pm cap_list
             configuration: latency=0
        *-pci:3
             description: PCI bridge
             product: VT8237A Host Bridge
             vendor: VIA Technologies, Inc.
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci ht bus_master cap_list
           *-multimedia
                description: Audio device
                product: VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller)
                vendor: VIA Technologies, Inc.
                physical id: 1
                bus info: pci@0000:04:01.0
                version: 10
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:4
             description: PCI bridge
             product: VT8237A PCI to PCI Bridge
             vendor: VIA Technologies, Inc.
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci ht bus_master cap_list
           *-network:0
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 5
                bus info: pci@0000:05:05.0
                logical name: eth1
                version: 10
                serial: 00:40:f4:32:5b:37
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.0.121 latency=32 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
           *-network:1
                description: Ethernet interface
                product: RTL-8110SC/8169SC Gigabit Ethernet
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 7
                bus info: pci@0000:05:07.0
                logical name: eth0
                version: 10
                serial: 00:18:f3:bc:26:c1
                size: 100MB/s
                capacity: 1GB/s
                width: 32 bits
                clock: 66MHz
                capabilities: pm bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.100 latency=64 link=yes maxlatency=64 mingnt=32 module=r8169 multicast=yes port=twisted pair speed=100MB/s
     *-pci:1
          description: Host bridge
          product: P4M890 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 101
          bus info: pci@0000:00:00.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: P4M890 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 102
          bus info: pci@0000:00:00.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: P4M890 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 103
          bus info: pci@0000:00:00.3
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: P4M890 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 104
          bus info: pci@0000:00:00.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: P4M890 Security Device
          vendor: VIA Technologies, Inc.
          physical id: 105
          bus info: pci@0000:00:00.6
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: P4M890 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 106
          bus info: pci@0000:00:00.7
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: VT8251 Ultra VLINK Controller
          vendor: VIA Technologies, Inc.
          physical id: 107
          bus info: pci@0000:00:11.7
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: latency=32
     *-scsi:0
          physical id: 2
          bus info: usb@5:4
          logical name: scsi3
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: 2500BEV External
             vendor: WD
             physical id: 0.0.0
             bus info: scsi@3:0.0.0
             logical name: /dev/sdd
             version: 1.05
             serial: WD-WXE408DM8463
             size: 232GiB (250GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=4 signature=9c8160ad
           *-volume
                description: Windows FAT volume
                vendor: HOPPY FS
                physical id: 1
                bus info: scsi@3:0.0.0,1
                logical name: /dev/sdd1
                logical name: /media/SATELLITE
                version: FAT32
                serial: 0000-0000
                size: 232GiB
                capacity: 232GiB
                capabilities: primary bootable fat initialized
                configuration: FATs=2 filesystem=fat label=HOPPY LABEL mount.fstype=vfat mount.options=rw,nosuid,nodev,uid=999,fmask=0077,dmask=0077,codepage=cp437,iocharset=iso8859-1,shortname=mixed,utf8,flush state=mounted
     *-scsi:1
          physical id: 3
          bus info: usb@5:3
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: 2500BEV External
             vendor: WD
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sde
             version: 1.05
             serial: WD-WXE508SZA370
             size: 232GiB (250GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=4 signature=5b6ac646
           *-volume
                description: Windows FAT volume
                vendor: MSWIN4.1
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sde1
                logical name: /media/My Passport
                version: FAT32
                serial: 46f6-8546
                size: 232GiB
                capacity: 232GiB
                capabilities: primary fat initialized
                configuration: FATs=2 filesystem=fat label=My Passport mount.fstype=vfat mount.options=rw,nosuid,nodev,uid=999,fmask=0077,dmask=0077,codepage=cp437,iocharset=iso8859-1,shortname=mixed,utf8,flush state=mounted
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: c2:b7:5e:72:0b:a2
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
v             description: PCI bridge
             product: VT8237/VX700 PCI Bridge
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci pm bus_master cap_list
        *-pci:1
             description: PCI bridge
             product: P4M890 PCI to PCI Bridge Controller
             vendor: VIA Technologies, Inc.
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress pm msi ht bus_master cap_list
             configuration: driver=pcieport-driver
           *-display UNCLAIMED
                description: VGA compatible controller
                product: G70 [GeForce 7300 GT]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: latency=0
        *-pci:2
             description: PCI bridge
             product: P4M890 PCI to PCI Bridge Controller
             vendor: VIA Technologies, Inc.
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress pm msi ht bus_master cap_list
             configuration: driver=pcieport-driver
           *-storage
                description: SATA controller
                product: JMicron 20360/20363 AHCI Controller
                vendor: JMicron Technologies, Inc.
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm pciexpress bus_master cap_list
                configuration: driver=ahci latency=0 module=ahci
           *-ide
                description: IDE interface
                product: JMicron 20360/20363 AHCI Controller
                vendor: JMicron Technologies, Inc.
                physical id: 0.1
                bus info: pci@0000:03:00.1
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: ide pm bus_master cap_list
                configuration: driver=pata_jmicron latency=0 module=pata_jmicron
        *-ide:0
             description: IDE interface
             product: VT8237A SATA 2-Port Controller
             vendor: VIA Technologies, Inc.
             physical id: f
             bus info: pci@0000:00:0f.0
             logical name: scsi5
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=sata_via latency=32 module=sata_via
           *-disk
                description: ATA Disk
                product: SAMSUNG SP2504C
                physical id: 0.0.0
                bus info: scsi@5:0.0.0
                logical name: /dev/sda
                version: VT10
                serial: S09QJ1UYC18573
                size: 232GiB (250GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=13e5233d
              *-volume
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@5:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 4e8f727d-ce7d-a14d-9e54-043ba34318bc
                   size: 232GiB
                   capacity: 232GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2006-01-08 01:01:43 filesystem=ntfs label=250_Backup state=clean
        *-ide:1
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: f.1
             bus info: pci@0000:00:0f.1
             logical name: scsi8
             logical name: scsi9
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=pata_via latency=32 module=pata_via
           *-disk:0
                description: ATA Disk
                product: WDC WD2500JB-00R
                vendor: Western Digital
                physical id: 0
                bus info: scsi@8:0.0.0
                logical name: /dev/sdb
                version: 20.0
                serial: WD-WCANKM420849
                size: 232GiB (250GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=49fdba33
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@8:0.0.0,1
                   logical name: /dev/sdb1
                   version: 3.1
                   serial: 381642b9-09fd-8f4a-841f-f729e78aa591
                   size: 128GiB
                   capacity: 128GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2008-11-11 14:40:22 filesystem=ntfs state=clean
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@8:0.0.0,2
                   logical name: /dev/sdb2
                   size: 87GiB
                   capacity: 87GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: HPFS/NTFS partition
                      physical id: 5
                      logical name: /dev/sdb5
                      capacity: 19GiB
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sdb6
                      capacity: 68GiB
              *-volume:2
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 3
                   bus info: scsi@8:0.0.0,3
                   logical name: /dev/sdb3
                   version: 1.0
                   serial: a50c7092-d098-cbde-be2f-a24732cb73d8
                   size: 16GiB
                   capacity: 16GiB
                   capabilities: primary journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2009-01-09 17:47:57 filesystem=ext3 modified=2009-01-09 17:47:57 mounted=2009-01-09 17:47:57 state=clean
           *-disk:1
                description: ATA Disk
                product: ST340014A
                vendor: Seagate
                physical id: 0.1.0
                bus info: scsi@8:0.1.0
                logical name: /dev/sdc
                version: 3.04
                serial: 3JX0CBC9
                size: 37GiB (40GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000202ff
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@8:0.1.0,1
                   logical name: /dev/sdc1
                   version: 1.0
                   serial: f423891d-002c-4422-8120-12c6a468d95b
                   size: 31GiB
                   capacity: 31GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2009-01-06 15:34:47 filesystem=ext3 modified=2009-01-09 17:33:09 state=clean
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@8:0.1.0,2
                   logical name: /dev/sdc2
                   size: 6204MiB
                   capacity: 6204MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sdc5
                      capacity: 1608MiB
                      capabilities: nofs
                 *-logicalvolume:1
                      description: HPFS/NTFS partition
                      physical id: 6
                      logical name: /dev/sdc6
                      capacity: 4596MiB
           *-cdrom
                description: DVD-RAM writer
                product: DRW-1608P3S
                vendor: ASUS
                physical id: 1
                bus info: scsi@9:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                logical name: /cdrom
                version: 1.24
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,noatime state=mounted status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom
                   logical name: /cdrom
                   configuration: mount.fstype=iso9660 mount.options=ro,noatime state=mounted
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10
             bus info: pci@0000:00:10.0
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.2
             bus info: pci@0000:00:10.2
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.3
             bus info: pci@0000:00:10.3
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: 10.4
             bus info: pci@0000:00:10.4
             version: 86
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ehci_hcd latency=32 module=ehci_hcd
        *-isa
             description: ISA bridge
             product: VT8237A PCI to ISA Bridge
             vendor: VIA Technologies, Inc.
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa pm cap_list
             configuration: latency=0
        *-pci:3
             description: PCI bridge
             product: VT8237A Host Bridge
             vendor: VIA Technologies, Inc.
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci ht bus_master cap_list
           *-multimedia
                description: Audio device
                product: VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller)
                vendor: VIA Technologies, Inc.
                physical id: 1
                bus info: pci@0000:04:01.0
                version: 10
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:4
             description: PCI bridge
             product: VT8237A PCI to PCI Bridge
             vendor: VIA Technologies, Inc.
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci ht bus_master cap_list
           *-network:0
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 5
                bus info: pci@0000:05:05.0
                logical name: eth1
                version: 10
                serial: 00:40:f4:32:5b:37
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.0.121 latency=32 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
           *-network:1
                description: Ethernet interface
                product: RTL-8110SC/8169SC Gigabit Ethernet
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 7
                bus info: pci@0000:05:07.0
                logical name: eth0
                version: 10
                serial: 00:18:f3:bc:26:c1
                size: 100MB/s
                capacity: 1GB/s
                width: 32 bits
                clock: 66MHz
                capabilities: pm bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.100 latency=64 link=yes maxlatency=64 mingnt=32 module=r8169 multicast=yes port=twisted pair speed=100MB/s
     *-pci:1
          description: Host bridge
          product: P4M890 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 101
          bus info: pci@0000:00:00.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: P4M890 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 102
          bus info: pci@0000:00:00.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: P4M890 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 103
          bus info: pci@0000:00:00.3
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: P4M890 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 104
          bus info: pci@0000:00:00.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: P4M890 Security Device
          vendor: VIA Technologies, Inc.
          physical id: 105
          bus info: pci@0000:00:00.6
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: P4M890 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 106
          bus info: pci@0000:00:00.7
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: VT8251 Ultra VLINK Controller
          vendor: VIA Technologies, Inc.
          physical id: 107
          bus info: pci@0000:00:11.7
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: latency=32
     *-scsi:0
          physical id: 2
          bus info: usb@5:4
          logical name: scsi3
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: 2500BEV External
             vendor: WD
             physical id: 0.0.0
             bus info: scsi@3:0.0.0
             logical name: /dev/sdd
             version: 1.05
             serial: WD-WXE408DM8463
             size: 232GiB (250GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=4 signature=9c8160ad
           *-volume
                description: Windows FAT volume
                vendor: HOPPY FS
                physical id: 1
                bus info: scsi@3:0.0.0,1
                logical name: /dev/sdd1
                logical name: /media/SATELLITE
                version: FAT32
                serial: 0000-0000
                size: 232GiB
                capacity: 232GiB
                capabilities: primary bootable fat initialized
                configuration: FATs=2 filesystem=fat label=HOPPY LABEL mount.fstype=vfat mount.options=rw,nosuid,nodev,uid=999,fmask=0077,dmask=0077,codepage=cp437,iocharset=iso8859-1,shortname=mixed,utf8,flush state=mounted
     *-scsi:1
          physical id: 3
          bus info: usb@5:3
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: 2500BEV External
             vendor: WD
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sde
             version: 1.05
             serial: WD-WXE508SZA370
             size: 232GiB (250GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=4 signature=5b6ac646
           *-volume
                description: Windows FAT volume
                vendor: MSWIN4.1
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sde1
                logical name: /media/My Passport
                version: FAT32
                serial: 46f6-8546
                size: 232GiB
                capacity: 232GiB
                capabilities: primary fat initialized
                configuration: FATs=2 filesystem=fat label=My Passport mount.fstype=vfat mount.options=rw,nosuid,nodev,uid=999,fmask=0077,dmask=0077,codepage=cp437,iocharset=iso8859-1,shortname=mixed,utf8,flush state=mounted
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: c2:b7:5e:72:0b:a2
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


```

---

### Post by caljohnsmith on 2009-01-12
How about before we go any further, I think it would be worth checking to make sure your Ubuntu HDD is in good health, because it seems strange that you are getting different errors with each reinstall. Also, I don't think you mentioned, but did you try the "check CD for defects" option on the Live CD? What did that return?

So to check the Ubuntu HDD's health, how about doing:
```
sudo apt-get install smartmontools
```
First do the following to save the current health status parameters of your HDD to a file on your desktop:
```
sudo smartctl -a /dev/sdc > ~/Desktop/sdc_health_before_test.txt
```
Then run:
```
sudo smartctl -t long /dev/sdc
```
That command will immediately terminate while the HDD begins its self-test, and it could take quite a while. You can monitor the progress with:
```
sudo smartctl -a /dev/sdc | grep -A 1 -i "self-test execution status"
```
Once the above command says the test is done, then do:
```
sudo smartctl -a /dev/sdc > ~/Desktop/sdc_health_after_test.txt
sudo smartctl -H /dev/sdc
```
And please post the contents of the two files on your desktop so I can see the results.

---

### Post by TSellers on 2009-01-12
I don't seem to see the 'check cd' option on the CD that I'm using, maybe I should just download another ISO and reburn/reinstall it.

We already determined that the 250GB SATA Drive was wonky, I placed this intall on the 40GB IDE to be safe. So I'll run the check on that one. THanks.

Update:
Test is presently running. It is having trouble with the PCI Network card. I found there was no internet connectivity. When I switched the cable over to the other network coard, I then had internet connectivity.

---

### Post by TSellers on 2009-01-12
I removed that Network card and tried to reboot, got a different error this time.

Heres the results of the test:

```
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Barracuda 7200.7 and 7200.7 Plus family
Device Model:     ST340014A
Serial Number:    3JX0CBC9
Firmware Version: 3.04
User Capacity:    40,020,664,320 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   6
ATA Standard is:  ATA/ATAPI-6 T13 1410D revision 2
Local Time is:    Mon Jan 12 21:14:41 2009 UTC
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82)	Offline data collection activity
					was completed without error.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		 ( 430) seconds.
Offline data collection
capabilities: 			 (0x5b) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					Offline surface scan supported.
					Self-test supported.
					No Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					No General Purpose Logging support.
Short self-test routine 
recommended polling time: 	 (   1) minutes.
Extended self-test routine
recommended polling time: 	 (  31) minutes.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   059   053   006    Pre-fail  Always       -       109793594
  3 Spin_Up_Time            0x0003   098   097   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       11
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   088   060   030    Pre-fail  Always       -       686463660
  9 Power_On_Hours          0x0032   091   091   000    Old_age   Always       -       8207
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       643
194 Temperature_Celsius     0x0022   041   052   000    Old_age   Always       -       41
195 Hardware_ECC_Recovered  0x001a   059   053   000    Old_age   Always       -       109793594
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   184   000    Old_age   Always       -       18
200 Multi_Zone_Error_Rate   0x0000   100   253   000    Old_age   Offline      -       0
202 TA_Increase_Count       0x0032   100   253   000    Old_age   Always       -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
No self-tests have been logged.  [To run self-tests, use: smartctl -t]


SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.


```

```
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Barracuda 7200.7 and 7200.7 Plus family
Device Model:     ST340014A
Serial Number:    3JX0CBC9
Firmware Version: 3.04
User Capacity:    40,020,664,320 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   6
ATA Standard is:  ATA/ATAPI-6 T13 1410D revision 2
Local Time is:    Mon Jan 12 21:45:58 2009 UTC
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82)	Offline data collection activity
					was completed without error.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		 ( 430) seconds.
Offline data collection
capabilities: 			 (0x5b) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					Offline surface scan supported.
					Self-test supported.
					No Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					No General Purpose Logging support.
Short self-test routine 
recommended polling time: 	 (   1) minutes.
Extended self-test routine
recommended polling time: 	 (  31) minutes.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   060   053   006    Pre-fail  Always       -       198329663
  3 Spin_Up_Time            0x0003   098   097   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       11
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   088   060   030    Pre-fail  Always       -       686574873
  9 Power_On_Hours          0x0032   091   091   000    Old_age   Always       -       8208
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       643
194 Temperature_Celsius     0x0022   043   052   000    Old_age   Always       -       43
195 Hardware_ECC_Recovered  0x001a   060   053   000    Old_age   Always       -       198329663
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   184   000    Old_age   Always       -       18
200 Multi_Zone_Error_Rate   0x0000   100   253   000    Old_age   Offline      -       0
202 TA_Increase_Count       0x0032   100   253   000    Old_age   Always       -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%      8207         -

SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.


```

Here's the error I see now:

[IMG]http://www.mparam.com/images/error2.jpg[/IMG]

---

### Post by caljohnsmith on 2009-01-12
OK, it looks like your 40 GB Ubuntu drive is in good health, so that's good. I like your idea though of downloading another Ubuntu Live CD ISO, burning that (I would use a slow speed like 4X), and seeing if that makes any difference. Also, before you burn it, how about checking its MD5 hash sum by doing:
```
md5sum Ubuntu_Live_CD.ISO
```
Of course replace the name above with the name of the ISO you download. And lastly, once you boot up the new Live CD, how about running the "memtest86+" option for a while and see if it finds anything. Keep an eye on it though to see when it repeats, because it never actually completes, it just continually cycles through its tests. Because your fresh Ubuntu installs are giving strange/inconsistent errors, I would just like to remove as many variables as we can, including hardware-related issues, before we try to troubleshoot your specific problem. Let me know how that goes.

---

### Post by TSellers on 2009-01-12
Thanks, is there a preferred download location for the version that you recommend I try next?

---

### Post by caljohnsmith on 2009-01-12
How about going to the Ubuntu.com [download page]("http://www.ubuntu.com/getubuntu/download"), choose to download the 8.10 desktop version, select a location in the drop down box that is close to you, and then you can download the ISO. Or if you have some experience using bit torrent, there's a link on the download page to get the .torrent file to download the ISO that way. Bit torrent is generally faster, but either way will work. Good luck and keep me posted.

---

### Post by TSellers on 2009-01-17
Thanks for the assistance, it took awhile to get the opportunity but got it done this morning. It now boots properly, and I can now get busy with getting app's installed and setup properly.

I should start a new thread for this, but as I wanted to reply here, in case it's something simple I may as well get started and then can move it perhaps.

It's regarding dual display. Perviously when I installed Xandros in that system it worked so I suspected it may be do-able. The card is an nVidia  GEForce 7800 with dual outputs, DVI and VGA. I can connect to either one and the display will work, but if both are connected at the same time they don't. When I do a hardware test it tells me it cannot connect with the database, and although it will also try to install some restricted nVidia drivers (it recommends version 177), but it also fails with the red circle popping up in a box. Should I start a new topic for this?

Thanks again for all the assistance!

---

### Post by caljohnsmith on 2009-01-17
Glad you at least have Ubuntu booting OK now, but about your dual monitor problem, I think you're better off starting a new thread since I have no experience setting up a dual monitor setup. Good luck and hope you can get it working OK.

---

### Post by TSellers on 2009-01-17
Thanks again. Using the trusty search window found a thread from 22hrs ago that solved the dual display problem for me. I thought I saw somewhere that perhaps you needed to make a topic as solved, but maybe it was another forum.

---

