---
title: "Windows Bootloader Refuses to Die"
date: 2009-09-15
forum: Installation &amp; Upgrades
---

### Post by HuoMaKe on 2009-09-15
I'm at the end of my rope.

Today, I've wiped my hard drives, installed Windows three times, installed Linux Mint at least 4, and moved my drives around more than I care to count.

My problem started out simply enough: I installed Windows over an Ubuntu partition, and it wiped out GRUB. Fine, I said, I'll fix it. I did sudo grub (find /boot/grub/stage1; root (hd0); setup (hd0)) and it said it finished. I restarted, and it started Windows.

I tried removing the Windows hard drive (I'd installed it on a separate drive from the 'buntu one, the Linux drive being the second HD), to no avail. It gave me an error, telling me that hal.dll was missing or corrupted...which was right, because I was booting to Linux. It wouldn't go further. I deduced that the Windows bootloader had survived, and after several attempts to eradicate it, I gave up and wiped the Linux drive.

I used Linux Mint. It didn't work. The same error. I decided to wipe it off again and install Windows. Works fine. Put Linux Mint back on. hal.dll is missing, still.

Finally I try formatting everything off with gparted. Destroyed both drives, made sure nothing was left. Reinstalled Windows, giving it half of the 160GB hard drive, and making sure that the 160 was the first drive. Works fine. Installed Mint on the other partition. Windows boots. *rage*

I just thought of something, I'm going to try installing Mint again, this time with the 80GB drive unplugged...if it works, I'll thank anyone who posts for their time, but in the meantime, if you see any problems with my processes, please help! I want to have Linux for my media/schoolwork, and use Windows for games...the plan isn't working so far :P

Thanks in advance for your responses,
MarkTraceur (the username is outdated)

---

### Post by presence1960 on 2009-09-16
your commands for restoring GRUB are incorrect. We need to see exactly what you have on your machine & it's boot process.

Let's get a better look at your setup. Boot the Ubuntu Live CD. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by HuoMaKe on 2009-09-16
Here it is...the SDC drive and the SDD drive work fine, they're both media drives. SDC does not have a bootloader on it, at least to my knowledge...maybe it did at one point? Anyway, let me know if you derive anything from this.

Also, I did move the drives around a bit to get this and attempted a CrunchBang install in the interim period. Thanks again.

```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdc
 => No boot loader is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
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

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdd1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdd1 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x23213b72

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   312,560,639   312,560,577   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x43a38314

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   149,790,059   149,789,997  83 Linux
/dev/sdb2         149,790,060   156,248,189     6,458,130   5 Extended
/dev/sdb5         149,790,123   156,248,189     6,458,067  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x40440555

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   976,768,064   976,768,002   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000ae516

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63 1,953,520,064 1,953,520,002   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="94E40EA2E40E8728" TYPE="ntfs" 
/dev/sdb1: UUID="7fb8e1a3-1998-41d9-8618-e978dba017d8" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: UUID="405a9825-a5d2-493b-865e-c912ad61af44" TYPE="swap" 
/dev/sdc1: UUID="14142FAA142F8E34" LABEL="Media" TYPE="ntfs" 
/dev/sdd1: LABEL="Media2" UUID="6E6D-3CE2" TYPE="vfat" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
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
gvfs-fuse-daemon on /home/mint/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=mint)
/dev/sr1 on /media/F5D7050v3 type iso9660 (ro,nosuid,nodev,uhelper=hal,uid=999,utf8)
/dev/sdd1 on /media/Media2 type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)
/dev/sdc1 on /media/Media type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


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
# kopt=root=UUID=7fb8e1a3-1998-41d9-8618-e978dba017d8 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=7fb8e1a3-1998-41d9-8618-e978dba017d8

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

title		CrunchBang, kernel 2.6.28-13-generic
uuid		7fb8e1a3-1998-41d9-8618-e978dba017d8
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=7fb8e1a3-1998-41d9-8618-e978dba017d8 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		CrunchBang, kernel 2.6.28-13-generic (recovery mode)
uuid		7fb8e1a3-1998-41d9-8618-e978dba017d8
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=7fb8e1a3-1998-41d9-8618-e978dba017d8 ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		CrunchBang, memtest86+
uuid		7fb8e1a3-1998-41d9-8618-e978dba017d8
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Windows NT/2000/XP (loader)
rootnoverify	(hd2,0)
savedefault
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=7fb8e1a3-1998-41d9-8618-e978dba017d8 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=405a9825-a5d2-493b-865e-c912ad61af44 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


   1.8GB: boot/grub/menu.lst
   1.8GB: boot/grub/stage2
   1.8GB: boot/initrd.img-2.6.28-13-generic
   1.7GB: boot/vmlinuz-2.6.28-13-generic
   1.8GB: initrd.img
   1.7GB: vmlinuz
```

---

### Post by presence1960 on 2009-09-16
Ok GRUB is installed on MBR of sdb. You need to make that disk (sdb) first in the hard disk boot order in BIOS. Reboot Go into BIOS and set sdb as first boot disk and sda as second in the order. sdc and sdd can be in any order after sdb & sda since they have no OS on them. Save changes to CMOS. Continue booting machine.

GRUB should come up. Boot into Ubuntu. Open a terminal and run this command ```
gksu gedit /boot/grub/menu.lst
```
that is a lowercase L in .lst

scroll down to windows entry and change this:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Windows NT/2000/XP (loader)
rootnoverify	(hd2,0)
savedefault
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1
```
To:
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP 
rootnoverify	(hd1,0)
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```

Click Save on toolbar, close file & reboot. Try selecting windows from GRUB. 

The above info is based on windows being installed on sda1. Please note in the boot info script output there are no boot files/dir listed for windows. But you say windows boots fine when you start your machine. If windows doesn't boot from GRUB there is a fix for that too. But let's do one thing at a time.

FYI: which ever disk is first in the hard disk boot order in BIOS will take over when you start your machine. So if sda is first in BIOS hard disk boot order that is why windows is coming up because windows bootloader is in MBR of sda. When using (hdx,y) in GRUB numbering starts at 0 for devices (x) and partitions (y). But device (x) numbering is determined by the order of the hard disk boot order in BIOS because that is the actual order of the disks when you boot, in spite of what Ubuntu and fdisk report. Since you are setting sda as second boot and sdb as first disk to boot sdb is (hd0) and sda is (hd1) for device (x) numbering in GRUB (hdx,y)

You need the map lines in the windows entry in menu.lst whenever windows is not on the first disk to boot in BIOS. Windows needs to be on the first disk that boots and the map lines "entice" or "trick" windows into thinking it is on the first disk to boot. had you put windowws and Ubuntu on the same disk the map lines would be unnecessary.

---

### Post by HuoMaKe on 2009-09-16
*facepalm*

I tried changing the boot order again, and it worked. I guess I had assumed that the drive that Ubuntu called sda would be the first drive to boot...guess not. Thanks for all your help, though!

---

