---
title: "Ubuntu 8.10 / Vista Grub error"
date: 2009-01-31
forum: Installation &amp; Upgrades
---

### Post by pedrogent on 2009-01-31
Hello all. I have a similar problem. I have had Vista installed for some time but today I installed Ubuntu 8.10. Now when I power up the computer it doesn't reach the GRUB stage. Instead, it stalls and says something like 'Missing OS'.

I can get in to either Windows or Ubuntu by using a SuperGRUB disk but this is far from ideal.

When I was installing Ubuntu this morning, at the end I was asked if I should over-write the MBR of the 'first' hard disc. I said yes.

The output of

```
cat /boot/grub/menu.lst
```

is as follows:

```
title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		cf55c583-5d86-4a20-adb6-fa952b44b396
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=cf55c583-5d86-4a20-adb6-fa952b44b396 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		cf55c583-5d86-4a20-adb6-fa952b44b396
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=cf55c583-5d86-4a20-adb6-fa952b44b396 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		cf55c583-5d86-4a20-adb6-fa952b44b396
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows Vista/Longhorn (loader)
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```
The output of

```
sudo fdisk -l
```

is as follows:

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e106e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       43913   352729084    7  HPFS/NTFS
/dev/sda2   *       43914       60314   131741032+  83  Linux
/dev/sda3           60315       60801     3911827+  82  Linux swap / Solaris

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0004552d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2       77825   625121280    7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a3325

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           2       60801   488376000    7  HPFS/NTFS

```
I suspect I have a problem with my bootable flags but I'm far from certain. In fact, I'm very confused about what exactly bootable flags are...

Can anyone help me with this?

Thanks a lot!

---

### Post by ugm6hr on 2009-01-31
> Hello all. I have a similar problem.

Not similar at all.

Hence moved to a separate thread.

---

### Post by pedrogent on 2009-01-31
hello all. i replied to this thread with much the same issues however it looks like my post has disappeared.

here is the output for:

```
cat /boot/grub/menu.lst
```

```
title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		cf55c583-5d86-4a20-adb6-fa952b44b396
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=cf55c583-5d86-4a20-adb6-fa952b44b396 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		cf55c583-5d86-4a20-adb6-fa952b44b396
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=cf55c583-5d86-4a20-adb6-fa952b44b396 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		cf55c583-5d86-4a20-adb6-fa952b44b396
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows Vista/Longhorn (loader)
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
```

And then for:

```
sudo fdisk -l
```

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e106e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       43913   352729084    7  HPFS/NTFS
/dev/sda2   *       43914       60314   131741032+  83  Linux
/dev/sda3           60315       60801     3911827+  82  Linux swap / Solaris

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0004552d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2       77825   625121280    7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a3325

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           2       60801   488376000    7  HPFS/NTFS

```
Then again for:

```
sudo mount /dev/sda1 /mnt && ls -l /mnt
```

```
total 7643621
drwxrwx--- 1 root plugdev          0 2008-12-17 21:08 ATI
-rwxrwx--- 1 root plugdev         24 2006-09-19 07:13 autoexec.bat
drwxrwx--- 1 root plugdev       4096 2008-12-18 14:23 Boot
-rwxrwx--- 1 root plugdev     333203 2008-01-21 12:54 bootmgr
-rwxrwx--- 1 root plugdev       8192 2008-12-18 14:23 BOOTSECT.BAK
-rwxrwx--- 2 root plugdev         10 2006-09-19 07:13 config.sys
drwxrwx--- 1 root plugdev          0 2006-11-02 23:32 Documents and Settings
-rwxrwx--- 1 root plugdev 3756515328 2009-02-01 10:34 hiberfil.sys
drwxrwx--- 1 root plugdev          0 2008-12-17 20:44 Intel
-rwxrwx--- 1 root plugdev 4070129664 2009-02-01 10:34 pagefile.sys
drwxrwx--- 1 root plugdev          0 2008-01-21 13:02 PerfLogs
drwxrwx--- 1 root plugdev       4096 2009-01-31 13:00 ProgramData
drwxrwx--- 1 root plugdev      12288 2009-02-01 02:15 Program Files
drwxrwx--- 1 root plugdev          0 2008-12-30 19:40 $Recycle.Bin
drwxrwx--- 1 root plugdev      28672 2009-02-01 05:24 System Volume Information
drwxrwx--- 1 root plugdev       4096 2008-12-17 20:35 Users
drwxrwx--- 1 root plugdev      24576 2009-01-31 19:17 Windows
```

anyone have any idea how I can fix this up?

i can boot into windows or ubuntu easy enough using a supergrub disk but this is far from ideal.

thanks in advance.

---

### Post by pedrogent on 2009-01-31
> **ugm6hr said:**
> Not similar at all.

Hence moved to a separate thread.

really? ok...

anyway, any help on this matter would be greatly appreciated.

sorry for hijacking the other thread.

---

### Post by caljohnsmith on 2009-01-31
Pedrogent, in order to get a clearer picture of your setup, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop (can be the Live CD), open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by pedrogent on 2009-01-31
thanks caljohnsmith. here it is:

```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
 => Grub0.97 is installed in the MBR of /dev/sdc and looks on boot drive #2 in 
    partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr

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

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000e106e

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048   705,460,215   705,458,168   7 HPFS/NTFS
/dev/sda2    *    705,462,345   968,944,409   263,482,065  83 Linux
/dev/sda3         968,944,410   976,768,064     7,823,655  82 Linux swap / Solaris


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0004552d

Partition  Boot         Start           End          Size  Id System

/dev/sdb1              16,065 1,250,258,624 1,250,242,560   7 HPFS/NTFS


Drive sdc: _____________________________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000a3325

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *         16,065   976,768,064   976,752,000   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="749236D892369F14" TYPE="ntfs" 
/dev/sda2: UUID="cf55c583-5d86-4a20-adb6-fa952b44b396" TYPE="ext3" 
/dev/sda3: TYPE="swap" UUID="b009026e-5c64-4160-86ed-b56733fcba8d" 
/dev/sdb1: UUID="5D5AB0864C4975A7" LABEL="motherlode" TYPE="ntfs" 
/dev/sdc1: UUID="3629E3943D68E98B" LABEL="tunes" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda2 on / type ext3 (rw,relatime,errors=remount-ro)
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
/dev/sdc1 on /media/audio type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdb1 on /media/storage type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda1 on /media/vista type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/frank/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=frank)
/dev/scd0 on /media/cdrom0 type udf (ro,nosuid,nodev,utf8,user=frank)

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
# kopt=root=UUID=cf55c583-5d86-4a20-adb6-fa952b44b396 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=cf55c583-5d86-4a20-adb6-fa952b44b396

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
uuid		cf55c583-5d86-4a20-adb6-fa952b44b396
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=cf55c583-5d86-4a20-adb6-fa952b44b396 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		cf55c583-5d86-4a20-adb6-fa952b44b396
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=cf55c583-5d86-4a20-adb6-fa952b44b396 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		cf55c583-5d86-4a20-adb6-fa952b44b396
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows Vista/Longhorn (loader)
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb2
UUID=cf55c583-5d86-4a20-adb6-fa952b44b396 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda1
UUID=3629E3943D68E98B /media/audio    ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdc1
UUID=5D5AB0864C4975A7 /media/storage  ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb1
UUID=749236D892369F14 /media/vista    ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb3
UUID=b009026e-5c64-4160-86ed-b56733fcba8d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda2: Location  of files loaded by Grub: ===================


 424.0GB: boot/grub/menu.lst
 424.0GB: boot/grub/stage2
 424.1GB: boot/initrd.img-2.6.27-7-generic
 424.0GB: boot/vmlinuz-2.6.27-7-generic
 424.1GB: initrd.img
 424.0GB: vmlinuz

```

hope this means something to someone.

:D

---

### Post by caljohnsmith on 2009-01-31
It looks like at some point the order of your drives changed, or at least in Ubuntu's eyes they changed order, because somehow Grub got installed to the MBR (Master Boot Record) of what is currently your sdc drive, not the sda drive that has Vista and Ubuntu. So to install Grub to the MBR of your sda drive, how about doing:
```
sudo grub
grub> root (hd0,0)
grub> makeactive
grub> root (hd0,1)
grub> setup (hd0)
grub> quit
```
Then reboot, make sure your BIOS is set to boot the Vista/Ubuntu drive before the other drives, and let me know how far you get. We can work from there.

---

### Post by pedrogent on 2009-01-31
> **caljohnsmith said:**
> It looks like at some point the order of your drives changed, or at least in Ubuntu's eyes they changed order, because somehow Grub got installed to the MBR (Master Boot Record) of what is currently your sdc drive, not the sda drive that has Vista and Ubuntu. So to install Grub to the MBR of your sda drive, how about doing:
```
sudo grub
grub> root (hd0,0)
grub> makeactive
grub> root (hd0,1)
grub> setup (hd0)
grub> quit
```
Then reboot, make sure your BIOS is set to boot the Vista/Ubuntu drive before the other drives, and let me know how far you get. We can work from there.

ok, i'll reboot and be back with you soon. much appreciated!

EDIT: solved! thank you very much!

just wondering now on one last thing - which partitions should be assigned a 'bootable flag'? what does it mean if a partition has a 'bootable flag'?

---

### Post by caljohnsmith on 2009-01-31
> **pedrogent said:**
> ok, i'll reboot and be back with you soon. much appreciated!

EDIT: solved! thank you very much!

just wondering now on one last thing - which partitions should be assigned a 'bootable flag'? what does it mean if a partition has a 'bootable flag'?
You're welcome, glad that worked OK. About the "boot flag", the boot flag is only used by brainless boot loaders like a Windows MBR that simply boots whichever partition has the boot flag set. For more sophisticated boot loaders like Grub, Grub couldn't care less about which partition has the boot flag set when it comes to booting a partition. But it is important that one primary partition have the boot flag set, even if you are using Grub, because there are some BIOSes that will refuse to boot a drive that doesn't have the boot flag set on one partition. But if you use Grub, it is entirely arbitrary which primary partition you want to set the boot flag on. Anyway, cheers and enjoy Windows and Ubuntu. :)

---

### Post by pedrogent on 2009-01-31
thank you once again.

---

### Post by pedrogent on 2009-01-31
hmmm... perhaps i spoke too soon.

now i get thru' to grub and i can boot ubuntu but if i try to boot vista/longhorn all i get is a message saying my BOOTMGR is missing.

any ideas anyone?

for info, i've run that script again and here is the output:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => Grub0.97 is installed in the MBR of /dev/sdc and looks on boot drive #2 in 
    partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr

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

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000e106e

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   705,460,215   705,458,168   7 HPFS/NTFS
/dev/sda2         705,462,345   968,944,409   263,482,065  83 Linux
/dev/sda3         968,944,410   976,768,064     7,823,655  82 Linux swap / Solaris


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0004552d

Partition  Boot         Start           End          Size  Id System

/dev/sdb1              16,065 1,250,258,624 1,250,242,560   7 HPFS/NTFS


Drive sdc: _____________________________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000a3325

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *         16,065   976,768,064   976,752,000   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="749236D892369F14" LABEL="vista" TYPE="ntfs" 
/dev/sda2: UUID="cf55c583-5d86-4a20-adb6-fa952b44b396" TYPE="ext3" 
/dev/sda3: TYPE="swap" UUID="b009026e-5c64-4160-86ed-b56733fcba8d" 
/dev/sdb1: UUID="5D5AB0864C4975A7" LABEL="motherlode" TYPE="ntfs" 
/dev/sdc1: UUID="3629E3943D68E98B" LABEL="tunes" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda2 on / type ext3 (rw,relatime,errors=remount-ro)
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
/dev/sdc1 on /media/audio type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdb1 on /media/storage type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/frank/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=frank)
/dev/sdb1 on /mnt type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda1 on /mnt type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

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
# kopt=root=UUID=cf55c583-5d86-4a20-adb6-fa952b44b396 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=cf55c583-5d86-4a20-adb6-fa952b44b396

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
uuid		cf55c583-5d86-4a20-adb6-fa952b44b396
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=cf55c583-5d86-4a20-adb6-fa952b44b396 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		cf55c583-5d86-4a20-adb6-fa952b44b396
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=cf55c583-5d86-4a20-adb6-fa952b44b396 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		cf55c583-5d86-4a20-adb6-fa952b44b396
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=cf55c583-5d86-4a20-adb6-fa952b44b396 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		cf55c583-5d86-4a20-adb6-fa952b44b396
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=cf55c583-5d86-4a20-adb6-fa952b44b396 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		cf55c583-5d86-4a20-adb6-fa952b44b396
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows Vista/Longhorn (loader)
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb2
UUID=cf55c583-5d86-4a20-adb6-fa952b44b396 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda1
UUID=3629E3943D68E98B /media/audio    ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdc1
UUID=5D5AB0864C4975A7 /media/storage  ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb1
UUID=749236D892369F14 /media/vista    ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb3
UUID=b009026e-5c64-4160-86ed-b56733fcba8d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda2: Location  of files loaded by Grub: ===================


 424.0GB: boot/grub/menu.lst
 424.0GB: boot/grub/stage2
 424.0GB: boot/initrd.img-2.6.27-11-generic
 424.1GB: boot/initrd.img-2.6.27-7-generic
 424.0GB: boot/vmlinuz-2.6.27-11-generic
 424.0GB: boot/vmlinuz-2.6.27-7-generic
 424.0GB: initrd.img
 424.1GB: initrd.img.old
 424.0GB: vmlinuz
 424.0GB: vmlinuz.old

=============================== StdErr Messages: ===============================

/home/frank/Desktop/boot_info_script023.sh: line 1060: cd: /media/storage type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdb1 on /mnt: No such file or directory
```

---

### Post by pedrogent on 2009-02-01
i installed ubuntu 8.10 again this morning. it's a dual boot set-up with vista. unfortunately it all got to be a huge mess and despite my best efforts reading around, i can't seem to work out how to fix it.

i can boot into ubuntu via grub but not into vista. if i try to boot into vista i get a message to the effect that 'BOOTMGR' is missing and then i'm asked to give the 'three finger salute'.

if i use the supergrub cd i can boot into vista.

i thought my problems had been solved in [this thread]("http://ubuntuforums.org/showthread.php?t=1056468"). the suggestions there did help me get grub up and running again but now i'm stuck where i can't boot vista using grub.

please, anyone?

there has to be an easier way!

---

### Post by cariboo on 2009-02-01
You somehow managed to remove some of the files that Vista needs in order to be able to boot from the first partition of the first hard drive. You will need to use you Vista install cd to repair the problem. Just boot from the cd and choose repair. After doing this you will have to reinstall grub.

To repair grub, boot from the LiveCD and once at the desktop, go to Applications-->Accessories-->Terminal and type:

```
sudo grub
```

this will start grub in root mode. Next at the prompt type:

```
find /boot/grub/stage1
```

this should result in something like this:

```
(hd0,0)
```

Next at the prompt type:

```
root (hd0,0)
```

substitute the result from the find command in the above command. you're almost there, at the prompt type:

```
setup (hd0)
```

again use the result of the find command without the partition (second) number. Now all you have to do is type:

```
quit
```

and reboot.

Jim

---

### Post by pedrogent on 2009-02-01
> **cariboo907 said:**
> You somehow managed to remove some of the files that Vista needs in order to be able to boot from the first partition of the first hard drive. You will need to use you Vista install cd to repair the problem. Just boot from the cd and choose repair.

hey jim, thanks for your tips. one problem tho': when i boot from the vista cd there's no 'repair' option so far as i can see. just an 'install option'.

am i missing something here?

EDIT: yes i was missing something. one needs to 'install' before one can 'repair' - go figure.

in any event, both gui and command line i'm struggling to repair this thing.

12 hours... there MUST be an easier way of dual booting...

---

### Post by caljohnsmith on 2009-02-01
OK, I believe I see the problem with your Vista Grub entry, so how about first opening your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And change your Vista entry to:
```
title		Windows Vista
root		(hd0,0)
chainloader	+1

```
Reboot, and let me know what happens when you choose Vista from Grub. We can work from there if necessary.

---

### Post by pedrogent on 2009-02-02
> **caljohnsmith said:**
> OK, I believe I see the problem with your Vista Grub entry, so how about first opening your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And change your Vista entry to:
```
title		Windows Vista
root		(hd0,0)
chainloader	+1

```
Reboot, and let me know what happens when you choose Vista from Grub. We can work from there if necessary.

ok, i've done this. but now grub seems to have gone missing. (i should point out that earlier i 'fixed' windows bootmgr using easybcd - i think this is why grub has gone away.)

so now windows boots up normally and i can boot ubuntu, but only if i use a supergrub cd.

now my question is: how do i best get grub back in my life?

---

### Post by zAlbee on 2009-02-02
Look above you at post #13 ;-)

---

### Post by pedrogent on 2009-02-02
OK, I followed the advice in #15 and then in #13 again and now guess what? I have GRUB and from there I can boot into **BOTH** Ubuntu **AND** Vista.

Thank you very much to all involved in getting this sorted.

:D

I think the whole process broke down something like this:

[LIST]
[*]Resizing my defragmented Vista partition somehow mucked up Vista's bootmgr - bootmgr was still there to see but I think it got corrupted in the process.
[*]Installing GRUB into the MBR when I installed Ubuntu somehow mucked up things, sending the message 'Missing operating system' when I next tried to boot.
[*]I booted into Vista using a SuperGRUB disk and fixed the bootmgr problem using EasyBCD (nice program that).
[*]This borked GRUB.
[*]I booted into Ubuntu using a SuperGRUB disk and followed the instructions in #15.
[*]I used a live CD to do what was recommended in #13 - i.e fix GRUB.
[*]I came on here to post my thanks.
[/LIST]

Couldn't be easier really!

---

