---
title: "Urgent! Booting problem after resizing partitions"
date: 2009-04-04
forum: Installation &amp; Upgrades
---

### Post by Tryfon on 2009-04-04
Hello,

I decided to shrink my windows ntfs partition to give some more air to my linux one, and used Partition Magic from within windows to do so. After the operation was done I got an Error 17 from Grub. I tried to reinstall using the instructions [here]("http://ubuntuforums.org/showthread.php?t=224351") but on the "setup (hd0)" step I got the following message:
```
Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,5)/boot/grub/stage2
/boot/grub/menu.lst"... failed

Error 12: Invalid device requested
```

I run a [boot info script]("http://sourceforge.net/projects/bootinfoscript/") for diagnostic purposes, below is the output of that script:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #256 for /boot/grub/stage2.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda1 sda1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda1 sda1 ntfs-3g force 0 0
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda1 sda1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda1 sda1 ntfs-3g force 0 0

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub is installed in the boot sector of sda5 and looks 
                       at sector 295318119 of the same hard drive for the 
                       stage2 file, but no stage2 files can be found at this 
                       location.
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x58152c43

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   122,881,184   122,881,122   7 HPFS/NTFS
/dev/sda2         158,722,200   312,576,704   153,854,505   5 Extended
/dev/sda5         158,722,263   308,672,909   149,950,647  83 Linux
/dev/sda6         308,672,973   312,576,704     3,903,732  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="38F486D8F48697B0" TYPE="ntfs" 
/dev/sda5: LABEL="Linux" UUID="de3847b1-42ee-40b9-bd72-ca587127f199" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: TYPE="swap" UUID="8c34d899-3109-4dcc-8525-d4daeccfd139" 
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


=========================== sda5/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=de3847b1-42ee-40b9-bd72-ca587127f199 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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
# howmany=1

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
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=de3847b1-42ee-40b9-bd72-ca587127f199 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=de3847b1-42ee-40b9-bd72-ca587127f199 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows XP (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config --
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda5 :
UUID=de3847b1-42ee-40b9-bd72-ca587127f199 / ext3 defaults,errors=remount-ro,relatime 0 1
# Entry for /dev/sda1 :
UUID=6ED29A68D29A33F5 /media/sda1 ntfs-3g defaults,locale=en_US.UTF-8 0 1
# Entry for /dev/sda2 :
UUID=3E7C9CAF7C9C6385 /media/sda2 ntfs-3g defaults,locale=en_US.UTF-8 0 1
# Entry for /dev/ !! UNKNOW DEVICE !! :
UUID=6AACBAD9ACBA9ECF /media/sda3 ntfs-3g defaults,locale=en_US.UTF-8 0 1
# Entry for /dev/sda6 :
UUID=8c34d899-3109-4dcc-8525-d4daeccfd139 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0

#ISU Masters 09
//172.16.101.10/Masters09/ /mnt/ISU smbfs username=tryfon.farmakakis,password=yarisaur,noauto,rw,users,exec,uid=1000,gid=1000 0 0

=================== sda5: Location of files loaded by Grub: ===================


  97.8GB: boot/grub/menu.lst
  97.5GB: boot/grub/stage2
  98.6GB: boot/initrd.img-2.6.22-14-generic
  98.2GB: boot/initrd.img-2.6.22-14-generic.bak
  87.6GB: boot/initrd.img-2.6.27-11-generic
  92.4GB: boot/initrd.img-2.6.27-7-generic
 108.5GB: boot/initrd.img-2.6.27-9-generic
  98.1GB: boot/vmlinuz-2.6.22-14-generic
  87.6GB: boot/vmlinuz-2.6.27-11-generic
  86.9GB: boot/vmlinuz-2.6.27-7-generic
 147.1GB: boot/vmlinuz-2.6.27-9-generic
  87.6GB: initrd.img
 108.5GB: initrd.img.old
  87.6GB: vmlinuz
 147.1GB: vmlinuz.old
```

Help please!

---

### Post by ronparent on 2009-04-04
From your boot info script above:

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub is installed in the boot sector of sda5 and looks 
                       at sector 295318119 of the same hard drive for the 
                       stage2 file, but no stage2 files can be found at this 
                       location.
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

It look like you may need a filesystem per following site : [http://users.bigpond.net.au/hermanzone/p10.htm#](http://users.bigpond.net.au/hermanzone/p10.htm#) - filesystem_check_on_an_ext3_filesystem

You need to find or restore your /boot/grub/stage2 to proceed.

---

### Post by Tryfon on 2009-04-04
Thanks for the reply but it didnt help much. I could use some more specific instructions or links. What do you mean restore my /boot/grub/stage2? How do I do that?

---

### Post by meierfra. on 2009-04-04
It sounds like your partition table is slightly corrupt.
Please post the output of 

```
sudo fdisk -lu
sudo sfdisk -d
```

---

### Post by Tryfon on 2009-04-05
sudo fdisk -lu :
```
omitting empty partition (5)

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x58152c43

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   122881184    61440561    7  HPFS/NTFS
/dev/sda2       158722200   312576704    76927252+   5  Extended
/dev/sda5       158722263   308672909    74975323+  83  Linux
/dev/sda6       308672973   312576704     1951866   82  Linux swap / Solaris
```

sudo sfdisk -d :
```
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size=122881122, Id= 7, bootable
/dev/sda2 : start=158722200, size=153854505, Id= 5
/dev/sda3 : start=        0, size=        0, Id= 0
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start=158722263, size=149950647, Id=83
/dev/sda6 : start=308672973, size=  3903732, Id=82
ubuntu@ubuntu:~$ sudo sfdisk -d
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size=122881122, Id= 7, bootable
/dev/sda2 : start=158722200, size=153854505, Id= 5
/dev/sda3 : start=        0, size=        0, Id= 0
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start=158722263, size=149950647, Id=83
/dev/sda6 : start=308672973, size=  3903732, Id=82
```

---

### Post by Tryfon on 2009-04-05
Bumb!

---

### Post by slick1a on 2009-04-05
ubuntu@ubuntu:~$ sudo fsck /dev/sda1
fsck 1.40.2 (12-Jul-2007)
e2fsck 1.40.2 (12-Jul-2007)
/dev/sda1 contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Inodes that were part of a corrupted orphan linked list found.  Fix<y>? yes

Inode 1819011 was part of the orphaned inode list.  FIXED.
Inode 1819021 was part of the orphaned inode list.  FIXED.
Inode 1819044 was part of the orphaned inode list.  FIXED.
Inode 1819061 was part of the orphaned inode list.  FIXED.
Inode 1819067 was part of the orphaned inode list.  FIXED.
Inode 1819090 was part of the orphaned inode list.  FIXED.
Deleted inode 1819169 has zero dtime.  Fix<y>? yes

Inode 1819178 was part of the orphaned inode list.  FIXED.
sudo fix
exit
Inode 8471892 has illegal block(s).  Clear<y>? yes

Illegal block #0 (3087370993) in inode 8471892.  CLEARED.
Inode 8471892, i_blocks is 56, should be 48.  Fix<y>? yes

Inode 8475761 has illegal block(s).  Clear<y>? yes

Illegal block #0 (4261766383) in inode 8475761.  CLEARED.
Inode 8475761, i_blocks is 16, should be 8.  Fix<y>? yes

Inode 8475771 has illegal block(s).  Clear<y>? yes

Illegal block #0 (3137692930) in inode 8475771.  CLEARED.
Inode 8475771, i_blocks is 16, should be 8.  Fix<y>? yes

Inode 8475821 has illegal block(s).  Clear<y>? yes

Illegal block #0 (4261766510) in inode 8475821.  CLEARED.
Inode 8475821, i_blocks is 8, should be 0.  Fix<y>? yes

Inode 8475840 has illegal block(s).  Clear<y>? yes

Illegal block #0 (3087361425) in inode 8475840.  CLEARED.
Inode 8475840, i_blocks is 8, should be 0.  Fix<y>? yes

Inode 8476087 has illegal block(s).  Clear<y>? yes

Illegal block #0 (4261769272) in inode 8476087.  CLEARED.
Inode 8476087, i_blocks is 8, should be 0.  Fix<y>? yes

yyInode 8476080 has illegal block(s).  Clear<y>? yes

Illegal block #0 (4261769193) in inode 8476080.  CLEARED.
Inode 8476080, i_blocks is 120, should be 112.  Fix<y>? yes

Inode 8594830 has illegal block(s).  Clear<y>? yes

Illegal block #2 (3992977408) in inode 8594830.  CLEARED.
Inode 8635078 has illegal block(s).  Clear<y>? yes

Illegal block #0 (3138335485) in inode 8635078.  CLEARED.
Inode 8635078 is a zero-length directory.  Clear<y>? yes

Inode 8635223 has illegal block(s).  Clear<y>? 


what the heck is this ?

---

### Post by slick1a on 2009-04-05
Dont know what the above did , but when complete , resolved my missing Appl, places , system..stopped the machine (when booting) from doing routine disk check...etc ..but still have a box /window appearing saying i do not have permissions over 600 needed..

need further info let me know.

---

### Post by ronparent on 2009-04-05
Tryfon: to my eyes your partition table seems intact. If that the case, error 17 says: "Cannot mount selected partition
    This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB."

You have probably gone back to basics, but induldge me. Have you tried the following sequence of commands in a live cd terminal?

sudo grub
grub> find /boot/gtub/stage2

If there is output from this command we know that an intact file structure exist and it's grubroot; enter that root in

grub> root (hd?,?)
setup (hd0)

If Stage2 is not found then we will have to find out if the file structure is intact and if grub is installed?

---

### Post by meierfra. on 2009-04-05
> omitting empty partition (5)

This is one of  your problems. It means that there is a bogus entry in your partition table. Ubuntu ignores it, but Grub  doesn't.  Luckily it can be fixed very easily:


Boot from the LiveCD and open a terminal.

```
sudo fdisk /dev/sda
w
```

Now  you should be able to reinstall grub:

```
sudo grub
root (hd0,4)
setup (hd0)
quit
```

Reboot and you should get the grub menu.

---

### Post by Tryfon on 2009-04-06
Thanks a lot for the help everyone, but after all I decided to format everything, remake the partitions and reinstall my Ubuntu system. It was something that had to be done anyway for various reasons. Unfortunately I didn't get the chance to try the last solution, but thanks anyway!

---

