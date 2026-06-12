---
title: "Each Login changes GRUB"
date: 2009-02-08
forum: Installation &amp; Upgrades
---

### Post by kunks112 on 2009-02-08
I have Ubuntu 8.04 install on one SATA drive. Vista on another SATA drive, and XP Pro on a back up IDE drive. When I first installed Ubuntu correctly everything was fine, however a couple days later when I turned on my computer my GRUB menus was changed. 

For instance, my GRUB menu looks as the following

```


1. Ubuntu 8.04.2, kernel 2.6.24-23-generic
2. Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
3. Ubuntu 8.04.2, memtest86+
4. XP Pro (loader)
5. Vista (hd2)


```
At fisrt this was the case, now when I load GRUB and choose Vista I get XP Pro. If I try XP Pro I get an error, and when I load Ubuntu somtimes I get Ubuntu sometime I get an error.

Other times When I would select Vista it would load XP Pro, choose XP pro I would load Ubuntu, choose Ubuntu it would load Vista.

I ran boot_info_script and get the following

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.2
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders, total 586072368 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1bf61bf5

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   586,051,199   586,051,137   7 HPFS/NTFS


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0009aac1

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   955,498,004   955,497,942  83 Linux
/dev/sdb2         955,498,005   976,768,064    21,270,060   5 Extended
/dev/sdb5         955,498,068   976,768,064    21,269,997  82 Linux swap / Solaris


Drive sdc: _____________________________________________________________________

Disk /dev/sdc: 4102 MB, 4102887936 bytes
255 heads, 63 sectors/track, 498 cylinders, total 8013453 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0009305c

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             34     7,984,304     7,984,271   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="40BC2AF2BC2AE1E0" TYPE="ntfs" 
/dev/sdb1: UUID="83e5bd57-791c-45da-a814-5ac0bf6b4a08" TYPE="ext3" 
/dev/sdb5: TYPE="swap" UUID="62132145-d060-460c-afeb-3d7dd27bfadc" 
/dev/sdc1: UUID="200D-D515" TYPE="vfat" 

=============================== "mount" output: ===============================

/dev/sdb1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/mike/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=mike)
/dev/sdc1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)

=========================== sdb1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=83e5bd57-791c-45da-a814-5ac0bf6b4a08 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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
# defoptions=quiet splash xforcevesa

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

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=83e5bd57-791c-45da-a814-5ac0bf6b4a08 ro quiet splash xforcevesa
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=83e5bd57-791c-45da-a814-5ac0bf6b4a08 ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.2, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.



# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		XP Pro (loader)
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

title Vista (hd2)
rootnoverify     (hd2,0)
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader +1


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc1
UUID=83e5bd57-791c-45da-a814-5ac0bf6b4a08 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdc5
UUID=62132145-d060-460c-afeb-3d7dd27bfadc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


 466.9GB: boot/grub/menu.lst
 467.0GB: boot/grub/stage2
 466.9GB: boot/initrd.img-2.6.24-16-generic
 466.9GB: boot/initrd.img-2.6.24-16-generic.bak
 467.0GB: boot/initrd.img-2.6.24-23-generic
 466.9GB: boot/initrd.img-2.6.24-23-generic.bak
 466.9GB: boot/vmlinuz-2.6.24-16-generic
 466.9GB: boot/vmlinuz-2.6.24-23-generic
 467.0GB: initrd.img
 466.9GB: initrd.img.old
 466.9GB: vmlinuz
 466.9GB: vmlinuz.old

```

help please

Thanks
 Mike

---

### Post by caljohnsmith on 2009-02-08
Hi kunks112, because you have Grub installed to the MBR of both your sda and sdb drives, the type of behavior you describe could be due to changing which drive boots first on start up. It looks like that could be due to your Windows XP drive not being detected, because the Boot Info Script results do not show your 100 GB Windows XP drive that was present a couple weeks ago when I helped you in [this thread]("http://ubuntuforums.org/showthread.php?t=1045706"). First I would recommend restoring a Windows MBR to your sda Windows drive since Ubuntu is on your sdb drive, so how about doing:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
Then reboot, set your BIOS boot order to boot the sdb Ubuntu drive before your other drives, and you should be OK. When you reboot, if you end up booting straight into Windows, you will know you are booting a different drive than the Ubuntu drive. But I think the root of your problem is that your 100 GB Windows XP drive is not being consistently detected, so you may have a hardware issue. Let me know how it goes.

---

### Post by kunks112 on 2009-02-08
Thank you for the reply. I thought it might be a hardware issue. Im thinking the easiest thing to do will be to transfer all the IDE drive data to a 3rd SATA and forget about using my 100GB IDE drive.

Im not sure what installing lilo was meant for.

However thank you for confirming my thoughts.

---

### Post by kunks112 on 2009-02-15
Update:

To confirm previous diagnosis, I have been watching my bios start-up screen to check whether each drive is recognized. Upon each time one of the drives is not recognized at start-up, I get into GRUB very quickly but have the same issue stated above.

Upon each time every drive is recognized, GRUB loads in very slowly (approximately 3'20") and am able to load any OS.

Is there a reason GRUB is so slow when all drives are detected?

---

