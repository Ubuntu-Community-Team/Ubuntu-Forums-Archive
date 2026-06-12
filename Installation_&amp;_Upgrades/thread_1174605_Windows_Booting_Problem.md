---
title: "Windows Booting Problem"
date: 2009-05-31
forum: Installation &amp; Upgrades
---

### Post by Jodelman on 2009-05-31
I have just done a new installation of Jaunty to replace Gutsy Gibbon and whilst I have been using Ubuntu for a couple of years, I still regard myself as very much a beginner.

I run a system with three hard disks, one for Ubuntu, one for Windows and one for my data.

The fresh installation of Jaunty went well until I came to reboot and then I didn't even get to the boot menu but it stalled at stage 1.5. Searching the forums I came up with the following suggestion which I used from the live cd.

> sudo grub
device (hd0)
root (hd0,0)
setup (hd0)
quit


This made the grub menu display and enabled me to use Ubuntu but when I try to boot windows I get the message - "Error 13: Invalid or unsupported executable format".

Output of fdisk is:-

> 
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc516c516

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4992    40098208+   7  HPFS/NTFS
/dev/sda2            4993        9729    38049952+   f  W95 Ext'd (LBA)
/dev/sda5            4993        9729    38049921    7  HPFS/NTFS

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xace22e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4864    39070048+   c  W95 FAT32 (LBA)
/dev/sdb2            4865        4865        8032+   f  W95 Ext'd (LBA)

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x023da47a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        9379    75336786   83  Linux
/dev/sdc2            9380        9729     2811375    5  Extended
/dev/sdc5            9380        9729     2811343+  82  Linux swap / Solaris


My menu.1st looks like:-

> 
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
# kopt=root=UUID=2e1bdd5b-9f52-48f6-af9a-6820ad8203dd ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=2e1bdd5b-9f52-48f6-af9a-6820ad8203dd

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
uuid		2e1bdd5b-9f52-48f6-af9a-6820ad8203dd
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=2e1bdd5b-9f52-48f6-af9a-6820ad8203dd ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		2e1bdd5b-9f52-48f6-af9a-6820ad8203dd
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=2e1bdd5b-9f52-48f6-af9a-6820ad8203dd ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		2e1bdd5b-9f52-48f6-af9a-6820ad8203dd
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


Can anyone help me get back to being able to boot windows, please?

---

### Post by presence1960 on 2009-05-31
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Microsoft Windows XP Professional
rootnoverify (hd0,0)
map          (hd0) (hd2)
map          (hd2) (hd0)
chainloader  +1 
```

Open a terminal and run>  gksu gedit /boot/grub/menu.lst
Scroll down to the bottom and change your windows entry to the above.

---

### Post by Jodelman on 2009-05-31
I have altered the menu.1st file as suggested but still get the same message (Error 13: Invalid or unsupported executable format) when I try to boot windows from the boot menu. Is there anything else I could do?

---

### Post by mhgsys on 2009-05-31
try 
```

rootnoverify (hd0,0)
map          (hd0) (hd1)
map          (hd1) (hd0)
chainloader  +1

```

---

### Post by Jodelman on 2009-05-31
I have just tried that but still get the same error message.

---

### Post by Mark Phelps on 2009-05-31
I think we're all trying to guess the partition containing GRUB.

Try the following:
1) sudo -i
2) grub
3) find /boot/grub/stage1
4) quit

Command 3) should return something like (hd1,0) or (hd2,0) or whichever "drives" have GRUB installed.

---

### Post by Jodelman on 2009-05-31
Command 3) returned (hd2,0)

Does this help?

---

### Post by presence1960 on 2009-05-31
(hd0) is sda. Windows is on partition 1 thus (hd0,0)
(hd1) is sdb. This drive is not bootable and has all windows partitions
(hd2) is sdc. Ubuntu is on the first partition thus (hd2,0)

The map lines should be for the bootable Linux partition and the windows partition (hd0) & (hd2). The rootnoverify line should be > rootnoverify  (hd0,0)

Everything else looks in order. Maybe you should wait until someone else comes along who can look at this with a fresh set of eyes.

---

### Post by presence1960 on 2009-05-31
This is from a GRUB Error web page. Error  13 says this...13 : "Inconsistent filesystem structure"

This error is returned by the filesystem code to denote an internal error caused by the sanity checks of the filesystem structure on disk not matching what it expects. This is usually caused by a corrupt filesystem or bugs in the code handling it in GRUB.

Why don't you try changing your boot disk order in BIOS to the disk with Windows installed as first boot. See if Windows will boot. If Windows will not boot then something may be wrong with your Windows install.

---

### Post by Jodelman on 2009-05-31
> **presence1960 said:**
> Why don't you try changing your boot disk order in BIOS to the disk with Windows installed as first boot. See if Windows will boot. 

Thanks for your help Presence1960. Windows boots just fine when I do this and for the few times I need it, altering the disk boot order temporarily will suffice. It would be good, however, to know how to solve the problem properly.

---

### Post by presence1960 on 2009-05-31
why don't you download the Boot Info Script to your Desktop from : [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)
Then open a terminal and run ```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a RESULTS.txt file on your Desktop. This will contain a lot of info about your setup & boot process. I know you posted your menu.lst and sudo fdisk -l, but this will contain way more info. Paste the contents of the file here and place code tags around it by highlighting the text and clicking # on the toolbar.

---

### Post by Jodelman on 2009-06-01
Here is the output from the RESULTS.txt file.

```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Lilo is installed in the MBR of /dev/sdb
 => Grub0.97 is installed in the MBR of /dev/sdc and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

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

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc516c516

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    80,196,479    80,196,417   7 HPFS/NTFS
/dev/sda2          80,196,480   156,296,384    76,099,905   f W95 Ext d (LBA)
/dev/sda5          80,196,543   156,296,384    76,099,842   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xace22e9e

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    78,140,159    78,140,097   c W95 FAT32 (LBA)
/dev/sdb2          78,140,160    78,156,224        16,065   f W95 Ext d (LBA)
Empty Partition


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x023da47a

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   150,673,634   150,673,572  83 Linux
/dev/sdc2         150,673,635   156,296,384     5,622,750   5 Extended
/dev/sdc5         150,673,698   156,296,384     5,622,687  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="A61069381069111B" TYPE="ntfs" 
/dev/sda5: UUID="CE88DA8C88DA7307" TYPE="ntfs" 
/dev/sdb1: LABEL="DATA" UUID="4646-EDD1" TYPE="vfat" 
/dev/sdc1: UUID="2e1bdd5b-9f52-48f6-af9a-6820ad8203dd" TYPE="ext3" 
/dev/sdc5: TYPE="swap" UUID="5d4a6ecf-8365-40d1-ad8d-d4271aa7220d" 

=============================== "mount" output: ===============================

/dev/sdc1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=755)
/dev/sda1 on /windows type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/john/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=john)
/dev/sdb1 on /media/DATA type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn


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
# kopt=root=UUID=2e1bdd5b-9f52-48f6-af9a-6820ad8203dd ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=2e1bdd5b-9f52-48f6-af9a-6820ad8203dd

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
uuid		2e1bdd5b-9f52-48f6-af9a-6820ad8203dd
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=2e1bdd5b-9f52-48f6-af9a-6820ad8203dd ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		2e1bdd5b-9f52-48f6-af9a-6820ad8203dd
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=2e1bdd5b-9f52-48f6-af9a-6820ad8203dd ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		2e1bdd5b-9f52-48f6-af9a-6820ad8203dd
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1

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
UUID=2e1bdd5b-9f52-48f6-af9a-6820ad8203dd /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=5d4a6ecf-8365-40d1-ad8d-d4271aa7220d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sda1	/windows	ntfs-3g	defaults,locale=en_uk.utf-8	0	0

=================== sdc1: Location of files loaded by Grub: ===================


  22.8GB: boot/grub/menu.lst
  22.9GB: boot/grub/stage2
  22.9GB: boot/initrd.img-2.6.28-11-generic
  22.9GB: boot/vmlinuz-2.6.28-11-generic
  22.9GB: initrd.img
  22.9GB: vmlinuz
```

---

### Post by presence1960 on 2009-06-01
I see you now added lilo to sdb since your original post. But after looking it over this is what should work for Windows in your menu.lst:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
rootnoverify    (hd0,0)
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1
```

your GRUB is on (hd2,0) and Windows bootloader is on (hd0,0). If it doesn't work, I can't explain it. Maybe sit tight and wait until someone else can get a peek at the results of your Boot Info Script.

P.S. I would uninstall lilo.

---

### Post by pwc on 2009-06-01
I've been following this thread since I have very similar setup as Jodelman and get the same Error 13 message when I try to boot up Windows 7 RC. Ubuntu and Kubuntu are on other 2 hds. I've tried every combinations of (hd0,0) to (hd2,1) and nothing has worked yet. What I'm doing now as a work around is poping SGD(Super Grub Disk) in disk drive to boot up Windows 7. This only takes a few extra seconds and since I rarely use Windows anymore(thank God for linux!) I'm going to continue this way until someone solves problem. I also use Ext 4 with linux and wonder if that could be a common to problem? 

Thanks presence1960 for your input, I,m going to post my RESULTS.txt file you recommended and would appreciate a read on it. 

[HTML]= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #3 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on boot drive #2 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdc and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x088d7950

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   957,024,179   957,024,117  83 Linux
/dev/sda2         957,024,180   976,768,064    19,743,885   5 Extended
/dev/sda5         957,024,243   976,768,064    19,743,822  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcbb84531

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *        206,848   625,139,711   624,932,864   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x088d7954

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63 1,447,263,719 1,447,263,657  83 Linux
/dev/sdc2       1,447,263,720 1,465,144,064    17,880,345   5 Extended
/dev/sdc5       1,447,263,783 1,465,144,064    17,880,282  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="c2cd40d6-caf3-4ab9-a283-1462a64d8bec" TYPE="ext4" 
/dev/sda5: UUID="cb27fa13-e719-4adf-b6e3-fb5eef637ec7" TYPE="swap" 
/dev/sdb1: UUID="10DCF248DCF2281C" TYPE="ntfs" 
/dev/sdc1: UUID="a3df62e4-c433-4025-9493-75c3f53db6eb" TYPE="ext4" 
/dev/sdc5: UUID="2b6c2466-52b0-40bf-8e1a-c4fe8d9040b7" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sdc1 on / type ext4 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/wayne/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=wayne)


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
# kopt=root=UUID=c2cd40d6-caf3-4ab9-a283-1462a64d8bec ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=c2cd40d6-caf3-4ab9-a283-1462a64d8bec

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
uuid		c2cd40d6-caf3-4ab9-a283-1462a64d8bec
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=c2cd40d6-caf3-4ab9-a283-1462a64d8bec ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		c2cd40d6-caf3-4ab9-a283-1462a64d8bec
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=c2cd40d6-caf3-4ab9-a283-1462a64d8bec ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		c2cd40d6-caf3-4ab9-a283-1462a64d8bec
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows Vista (loader)
rootnoverify	(hd1,0)
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=a3df62e4-c433-4025-9493-75c3f53db6eb ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=a3df62e4-c433-4025-9493-75c3f53db6eb ro single 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
title		Ubuntu 9.04, memtest86+ (on /dev/sdc1)
root		(hd2,0)
kernel		/boot/memtest86+.bin  
savedefault
boot


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
UUID=c2cd40d6-caf3-4ab9-a283-1462a64d8bec /               ext4    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=cb27fa13-e719-4adf-b6e3-fb5eef637ec7 none            swap    sw              0       0
# swap was on /dev/sdc5 during installation
UUID=2b6c2466-52b0-40bf-8e1a-c4fe8d9040b7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


   2.4GB: boot/grub/menu.lst
    .4GB: boot/grub/stage2
   6.6GB: boot/initrd.img-2.6.28-11-generic
   2.5GB: boot/vmlinuz-2.6.28-11-generic
   6.6GB: initrd.img
   2.5GB: vmlinuz

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
# kopt=root=UUID=a3df62e4-c433-4025-9493-75c3f53db6eb ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=a3df62e4-c433-4025-9493-75c3f53db6eb

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
uuid		a3df62e4-c433-4025-9493-75c3f53db6eb
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=a3df62e4-c433-4025-9493-75c3f53db6eb ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		a3df62e4-c433-4025-9493-75c3f53db6eb
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=a3df62e4-c433-4025-9493-75c3f53db6eb ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		a3df62e4-c433-4025-9493-75c3f53db6eb
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
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=efe660ae-c1ab-480c-a8f0-df28f2d28c49 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=efe660ae-c1ab-480c-a8f0-df28f2d28c49 ro single 
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


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title windows 7 beta (Loader)
root (hd1,0)
map (hd0) (hd2)
map (hd2) (hd0)
savedefault
makeactive
chainloader +1

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
UUID=a3df62e4-c433-4025-9493-75c3f53db6eb /               ext4    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=af6f2fe8-17af-4f10-927e-a8b8c05c60d6 none            swap    sw              0       0
# swap was on /dev/sdc5 during installation
UUID=2b6c2466-52b0-40bf-8e1a-c4fe8d9040b7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdc1: Location of files loaded by Grub: ===================


   5.1GB: boot/grub/menu.lst
   2.4GB: boot/grub/stage2
   3.7GB: boot/initrd.img-2.6.28-11-generic
   4.3GB: boot/vmlinuz-2.6.28-11-generic
   3.7GB: initrd.img
   4.3GB: vmlinuz
[/HTML]

---

### Post by Jodelman on 2009-06-01
Sorry presence1960, but that doesn't work either. Thanks for your efforts however.

The lilo dates from a much earlier attempt at another distro. Not sure how I would delete it.

---

### Post by presence1960 on 2009-06-01
pwc, your menu.lst on sdc looks OK. I would suggest chainloading the second Ubuntu installation on which ever menu.lst shows up at boot. I will post my sudo fdisk -l and my menu.lst from my boot drive so you can see how it is done. This way when each version of Ubuntu upgrades the kernel you won't have to keep editing the menu.lst to use the new kernels.
```

raz@raz-desktop:~$ sudo fdisk -l
[sudo] password for raz: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000d179

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2611    20972826    7  HPFS/NTFS
/dev/sda2            2612        4569    15727635   83  Linux
/dev/sda3            4570       29879   203302575   83  Linux
/dev/sda4           29880       30401     4192965   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa7a57e45

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       16477   132351471   83  Linux
/dev/sdb2   *       16478       18389    15358140   83  Linux
/dev/sdb3           18390       19457     8578710    7  HPFS/NTFS
```

sda1 is Windows XP, sda2 is Jaunty, sdb2 is Hardy

menu.lst:
```
## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-12-generic
uuid		8319981e-03bb-4bd9-9d2e-276da66b4f1c
kernel		/boot/vmlinuz-2.6.28-12-generic root=UUID=8319981e-03bb-4bd9-9d2e-276da66b4f1c ro splash vga=789 
initrd		/boot/initrd.img-2.6.28-12-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-12-generic (recovery mode)
uuid		8319981e-03bb-4bd9-9d2e-276da66b4f1c
kernel		/boot/vmlinuz-2.6.28-12-generic root=UUID=8319981e-03bb-4bd9-9d2e-276da66b4f1c ro  single
initrd		/boot/initrd.img-2.6.28-12-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		8319981e-03bb-4bd9-9d2e-276da66b4f1c
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=8319981e-03bb-4bd9-9d2e-276da66b4f1c ro splash vga=789 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		8319981e-03bb-4bd9-9d2e-276da66b4f1c
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=8319981e-03bb-4bd9-9d2e-276da66b4f1c ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		8319981e-03bb-4bd9-9d2e-276da66b4f1c
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

title           Ubuntu Hardy 8.04
rootnoverify    (hd1,1)
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
rootnoverify	(hd0,0)
chainloader	+1

```
 When I choose Hardy it brings up the menu.lst on sdb2 which is Hardy's. This way when Hardy upgrades the kernel I don't have to edit Jaunty's menu.lst to run the new kernel for hardy.

Hardy is on my second boot drive and GRUB is installed to the partition sdb2. Windows and Jaunty are on my first boot drive so GRUB is installed to MBR on sda.

P.S.  I just noticed that you have GRUB installed to the MBR of your Windows drive, which jogged my memory. It has been a while since I had Windows on a separate drive, but I seem to remember not having GRUB in the MBR of the Windows drive. I believe it was the Windows bootloader. I am not 100% certain on this but I think that is how I had it set up with Windows on it's own drive. Maybe someone else can confirm or deny whether this is true. I don't want to tell you to do something if I am not sure.

---

### Post by pwc on 2009-06-02
Thanks presence1960 for looking at that and I appreciate your input. I vaguely remember installing Ubuntu and being asked about putting GRUB somewhere and clicking yes(of course not knowing what I was doing). Do you know if I can undo that at this stage or do I have to reinstall? I think if I redid all I could get it right this time, however about 2 weeks of work down the drain! ugh

Thanks again, pwc

---

### Post by presence1960 on 2009-06-02
> **pwc said:**
> Thanks presence1960 for looking at that and I appreciate your input. I vaguely remember installing Ubuntu and being asked about putting GRUB somewhere and clicking yes(of course not knowing what I was doing). Do you know if I can undo that at this stage or do I have to reinstall? I think if I redid all I could get it right this time, however about 2 weeks of work down the drain! ugh

Thanks again, pwc
Here is what I am thinking, Windows is installed on it's own hard disk with no linux partitions. if you were to restore Windows bootloader to the MBR it may work. It shouldn't effect your Linux installs because they are on separate physical drives. here is the guide : [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
 But you have Win 7, I am not sure of the process to do that in Win 7. Maybe you can see if someone else knows how to restore the bootloader in Win 7 or maybe can shed some light on how to solve your problem. Or you can always reinstall win 7.
 When I reinstalled XP when it was on it's own hard drive I went into BIOS and made that drive first in hard drive boot order and all went well. After install I put the Linux drive back to first in hard drive order.

For Win 7 bootloader : [http://www.neowin.net/forum/lofiversion/index.php/t720866.html](http://www.neowin.net/forum/lofiversion/index.php/t720866.html)

P.S. Don't feel bad about the 2 weeks work. We learn the most by making mistakes. When I first tried Ubuntu I messed up at the partitioner and wiped all my data. I was so mad, but it taught me to read up on what I was going to try and have a plan with all my ducks in a row. No pain no gain!

---

### Post by pwc on 2009-06-02
hey presence1960, you da man! I got it! Here's what I did. First I tried the guide to restore Windows bootloader, it went smooth with no trouble, but still Error 13. I don't really think that did anything. Then followed your suggestion and went into BIOS and made my Ubuntu drive(sdc) first instead of the Windows drive(sdb). Still Error 13. Then followed the "Restore Grub from live cd" guide and wham-o it's fixed. I nearly fell over after 99 or so fails. I'm not exactly sure what fixed it but I can live with that.
Also I'm not sure how to do the chainlinking thing. I will post my sudo fdisk -l and menu.lst and if you can guide me, I'll hail your name throughout the Ubuntu forums.

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x088d7950

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       59572   478512058+  83  Linux
/dev/sda2           59573       60801     9871942+   5  Extended
/dev/sda5           59573       60801     9871911   82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcbb84531

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          13       38914   312466432    7  HPFS/NTFS

Disk /dev/sdc: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x088d7954

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       90088   723631828+  83  Linux
/dev/sdc2           90089       91201     8940172+   5  Extended
/dev/sdc5           90089       91201     8940141   82  Linux swap / Solaris
wayne@cosmos:~$ 

```

```
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
# kopt=root=UUID=a3df62e4-c433-4025-9493-75c3f53db6eb ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=a3df62e4-c433-4025-9493-75c3f53db6eb

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
uuid		a3df62e4-c433-4025-9493-75c3f53db6eb
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=a3df62e4-c433-4025-9493-75c3f53db6eb ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		a3df62e4-c433-4025-9493-75c3f53db6eb
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=a3df62e4-c433-4025-9493-75c3f53db6eb ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		a3df62e4-c433-4025-9493-75c3f53db6eb
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
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=efe660ae-c1ab-480c-a8f0-df28f2d28c49 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=efe660ae-c1ab-480c-a8f0-df28f2d28c49 ro single 
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


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title windows 7 beta (Loader)
root (hd2,0)
savedefault
makeactive
chainloader +1
```



Thanks so much, pwc

---

### Post by presence1960 on 2009-06-02
I would change this :
```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=efe660ae-c1ab-480c-a8f0-df28f2d28c49 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=efe660ae-c1ab-480c-a8f0-df28f2d28c49 ro single 
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
```

to:
```
title           Ubuntu 9.04
rootnoverify    (hd0,0)
chainloader     +1
```

Leave the divider in there. Change the title to fit your needs such as Kubuntu 9.04, Jaunty 9.04, etc.
Glad you got it working.

P.S. make a backup of your menu.lst file first!

---

### Post by pwc on 2009-06-03
OK, presence1960 I think I did what you advised, I'll post menu.lst just to be sure I followed correctly. After doing that, Ubuntu(sdc) and Windows(sdb) boot up, but Kubuntu((sda) gives me the dreaded Error 13.

```

## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		a3df62e4-c433-4025-9493-75c3f53db6eb
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=a3df62e4-c433-4025-9493-75c3f53db6eb ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		a3df62e4-c433-4025-9493-75c3f53db6eb
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=a3df62e4-c433-4025-9493-75c3f53db6eb ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		a3df62e4-c433-4025-9493-75c3f53db6eb
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Kubuntu 9.04
rootnoverify    (hd0,0)
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title windows 7 beta (Loader)
root (hd2,0)
savedefault
makeactive
chainloader +1
```

See anything that stands out, I think this is what you suggested.
Thanks for sticking with this!

pwc

---

### Post by presence1960 on 2009-06-03
Ok, thinking it is one of two things that can be the problem. Even though fdisk -l is reporting sda, sdb and sdc- that is not the order of your drives. Windows is on sdb1 which would be (hd1,0) but yet it boots from root (hd2,0). The reason is it is reading the order of your boot drives in BIOS. So take a look in BIOS to be sure then change the root (hdx,0) in the Kubuntu chainloader accordingly. I think it should be (hd1,0) but look to be certain.

I think you have your sdc disk booting first, followed by your sda disk then lastly sdb.

See if that works then we'll look at #2 if that doesn't fix it. I won't be back till 930pm EST, my daughter has tae kwon do tonight.

---

### Post by pwc on 2009-06-03
OK, for Kubuntu chainloader it started as (hd0,0) giving Error 13. Then I tried with (hd1,0) and got Error 13. Then I tried (hd2,0) and it booted into Windows 7. It is now set at (hd1,0) which seems logical to me, but still Error 13. You say change the root(hdx,0) in Kubuntu chainloader, I assume that is the rootnoverify line.

In the BIOS:  1st Drive WDC 750GB Ubuntu 9.04 seen as sdc

              2nd Drive Hitachi 500GB Kubuntu 9.04 seen as sda

              3rd Drive WDC 320GB Windows 7 seen as sdb

Also Boot Priority set as 1st - DVD Drive
                          2nd - WDC 750(Ubuntu-sdc)
                          3rd - Disabled

Thanks, pwc

---

### Post by presence1960 on 2009-06-03
> **pwc said:**
> OK, for Kubuntu chainloader it started as (hd0,0) giving Error 13. Then I tried with (hd1,0) and got Error 13. Then I tried (hd2,0) and it booted into Windows 7. It is now set at (hd1,0) which seems logical to me, but still Error 13. You say change the root(hdx,0) in Kubuntu chainloader, I assume that is the rootnoverify line.

In the BIOS:  1st Drive WDC 750GB Ubuntu 9.04 seen as sdc

              2nd Drive Hitachi 500GB Kubuntu 9.04 seen as sda

              3rd Drive WDC 320GB Windows 7 seen as sdb

Also Boot Priority set as 1st - DVD Drive
                          2nd - WDC 750(Ubuntu-sdc)
                          3rd - Disabled

Thanks, pwc

Well 2 out of 3 ain't bad, but obviously we want all 3 to boot. You could try restoring GRUB to the Kubuntu partition.
```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or 
   whatever your hard disk + partition # is, to install GRUB to a 
   partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.
```

make note of what # 4 spits out. You want to use Kubuntu's partition. In #5 use root (hdx,y) where x,y are Kubuntu's disk & partition. In # 6 you want to set it up on Kubuntu's partition : setup (hdx,y). 


In the worst case scenario you can reinstall Kubuntu.

---

### Post by pwc on 2009-06-04
OK, this is interesting. Now I can boot into all three, however with Kubuntu there is a extra step. When I reboot I get the Ubuntu menu.lst which is:

Ubuntu 9.04, kernal 2.6.28-11-generic
Ubuntu 9.04, kernal 2.6.28-11-generic(recovory mode)
Ubuntu 9.04, memtest86+
Other operating systems:
Kubuntu 9.04
windows 7 beta(Loader)

With this I can boot into Ubuntu or windows 7 normally. If I highlight Kubuntu 9.04 > Enter then I get this:

Ubuntu 9.04, kernal 2.6.28-11-generic
Ubuntu 9.04, kernal 2.6.28-11-generic(recovery mode)
Ubuntu 9.04, memtest86+
Windows Vista(loader)
Ubuntu 9.04, kernal 2.6.28-11-generic(on /dev/sdc1)
Ubuntu 9.04, kernal 2.6.28-11-generic(recovery mode(on /dev/sdc1)
Ubuntu 9.04, memtest86+(on /dev/sdc1)

Top line(default) is actually Kubuntu, so with another Enter(or wait 10 sec) I boot into Kubuntu.
This is apparently  Kubuntu's menu.lst.
Not perfect but what the heck, an extra Enter "ain't nuttin". 

OK presence1960, if you want to play with this some more, I'm game. Actually I'm enjoying it and even starting to understand what's going on here, so it's a learning experience. However, if you are tired or bored with it, no problem. 
By the way, this is a new computer I put together which has Intel's new 4 core i7 CPU, I don't think that has anything to do with it, just had to brag some, she's a beauty! The point being, my old one has almost the same setup and I never had this happen before. I always installed Windows first, but in this case for some reason, I had reinstalled Windows after the linux installs. Oh, now I remember, I had Windows 7 Beta and then Windows 7 RC was released.
I'll keep my eyes on this tread and thanks for all your help,

pwc

---

### Post by presence1960 on 2009-06-04
that my friend is chainloading Kubuntu. When you choose the Kubuntu chainloading entry on sdc's menu.lst (which boots first) you actually get Kubuntu's GRUB menu from the menu.lst on Kubuntu's partition. It works just like your Windows chainloader. When you choose your windows chainload entry you get the bootloader on that disk (windows bootloader). When you choose your Kubuntu chainload entry you get the bootloader on that partition (which is Kubuntu's GRUB). The advantage is that when Kubuntu upgrades it's kernel it will be on it's menu.lst. The other way not chainloading you would always have to manually edit the menu.lst from Ubuntu's partition sdc1 to have Kubuntu's new kernel in that menu.lst. This is because when Kubuntu upgrades it's kernel it only upgrades the Kubuntu menu.lst entries on Kubuntu's partition. So now you can boot all 3 and your menu.lst's will be taken care of with each kernel upgrade for you. I would say this is SOLVED.

BTW good luck with your system. I built mine in Feb 2008. Dual core Athlon 2.8 GHz, Biostar TF7050-M2 motherboard, 4 GB dual channel PC 6400 RAM, EVGA GeForce 8600GT, DVD-RAM, 250 GB & 160 GB Seagate HDDs, Ultra modular 550W PSU. Still running strong.

---

### Post by pwc on 2009-06-05
Thanks for the enlightenment and a final thanks for your help. And may your rig run linux forever more! I figure mine should last for life since I'm 70.

pwc

---

### Post by presence1960 on 2009-06-05
Glad you got it working. Enjoy Ubuntu & your new rig!

---

