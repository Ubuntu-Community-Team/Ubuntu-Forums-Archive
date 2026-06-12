---
title: "Windows entry not showing in Grub menu"
date: 2009-04-28
forum: Installation &amp; Upgrades
---

### Post by UberMetaller on 2009-04-28
Basically, I deleted my partition with 8.04 and created a new partition for 9.04, ran into an error 17 problem with grub, so I had reinstalled it. Now I have two problems:

The entry for my Windows XP partition is not showing up on the boot menu, and the Windows entry that does show (the recovery partition) won't load.

Here's the information from menu.lst:

```
title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		7d13db34-62db-4ac2-bfef-2cacb22707f2
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=7d13db34-62db-4ac2-bfef-2cacb22707f2 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		7d13db34-62db-4ac2-bfef-2cacb22707f2
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=7d13db34-62db-4ac2-bfef-2cacb22707f2 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		7d13db34-62db-4ac2-bfef-2cacb22707f2
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb2
title		Windows NT/2000/XP
rootnoverify	(hd1,1)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
```

And here's a screenshot of my partitions in GParted

[http://bayimg.com/image/lapdiaabf.jpg](http://bayimg.com/image/lapdiaabf.jpg)

Any advice would be greatly appreciated :)

---

### Post by Elfy on 2009-04-28
Try changing it to (hd1,0)

```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by UberMetaller on 2009-04-28
Seems to have made a little progress. Instead of getting "Error 22: No such partition" on the windows recovery partition I get an error to the effect of "No NTLDR."

---

### Post by Elfy on 2009-04-29
Can you follow the instruction here and post the results.
[http://ubuntuforums.org/showpost.php?p=6740172&postcount=5](http://ubuntuforums.org/showpost.php?p=6740172&postcount=5)

---

### Post by UberMetaller on 2009-04-29
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       
    Boot sector type:  Grub
    Boot sector info:  Grub is installed in the boot sector of sdb1 and looks 
                       at sector 256890113 of the same hard drive for the 
                       stage2 file, but no stage2 files can be found at this 
                       location.
    Mounting failed:
mount: unknown filesystem type ''

sdb2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  HP Recovery
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ntldr /NTLDR /NTDETECT.COM /ntdetect.com

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x14de6cca

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63 1,953,520,064 1,953,520,002   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x14cb14cb

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *      8,675,100   218,387,609   209,712,510   7 HPFS/NTFS
/dev/sdb2                  63     8,675,099     8,675,037   b W95 FAT32
/dev/sdb3         218,387,610   378,395,009   160,007,400   5 Extended
/dev/sdb5         218,387,673   298,391,309    80,003,637  83 Linux
/dev/sdb6         298,391,373   378,395,009    80,003,637  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="8A30C3DB30C3CBFF" LABEL="TerraTerror" TYPE="ntfs" 
/dev/sdb2: LABEL="RECOVERY" UUID="423B-2BDF" TYPE="vfat" 
/dev/sdb5: UUID="7d13db34-62db-4ac2-bfef-2cacb22707f2" TYPE="ext3" 
/dev/sdb6: UUID="7c2836a1-a422-4df5-8827-d778a6f2e6cc" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sdb5 on / type ext3 (rw,relatime,errors=remount-ro)
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
gvfs-fuse-daemon on /home/headbanger/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=headbanger)


=========================== sdb5/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=7d13db34-62db-4ac2-bfef-2cacb22707f2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=7d13db34-62db-4ac2-bfef-2cacb22707f2

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
uuid		7d13db34-62db-4ac2-bfef-2cacb22707f2
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=7d13db34-62db-4ac2-bfef-2cacb22707f2 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		7d13db34-62db-4ac2-bfef-2cacb22707f2
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=7d13db34-62db-4ac2-bfef-2cacb22707f2 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		7d13db34-62db-4ac2-bfef-2cacb22707f2
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb2
title		Windows NT/2000/XP
rootnoverify	(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb5 during installation
UUID=7d13db34-62db-4ac2-bfef-2cacb22707f2 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=7c2836a1-a422-4df5-8827-d778a6f2e6cc none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


 125.3GB: boot/grub/menu.lst
 125.2GB: boot/grub/stage2
 125.2GB: boot/initrd.img-2.6.28-11-generic
 125.2GB: boot/vmlinuz-2.6.28-11-generic
 125.2GB: initrd.img
 125.2GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 
```

---

### Post by Elfy on 2009-04-29
try adding this to the menu list

```
title		Windows 95/98/NT/2000
root		(hd0,0)
makeactive
chainloader	+1
```

---

### Post by UberMetaller on 2009-04-29
All I get when I try that boot option is a message on the screen saying "Grub" with a blinking cursor after it. Nothing loads from it. Could it possibly need more tags added to it like the "rootnoverify" on the recovery partition?

---

### Post by meierfra. on 2009-04-30
> sdb1: _________________________________________________________________________

    Boot sector info:  Grub is installed in the boot sector of sdb1 

It seems you installed Grub to the boot sector of the Windows partition. This erases some of the information necessary to boot Windows. To fix your problem:


Download the [testdisk package ](http://www.cgsecurity.org/testdisk-6.11.1.linux26.tar.bz2) to your desktop, and then do:

```

cd ~/Desktop
tar xvf testdisk-6.11.1.linux26.tar.bz2
sudo testdisk-6.11/linux/testdisk_static /dev/sdb

```

 Choose "proceed" on the first screen, then
"intel"
"advanced",
Select the Windows partition (although it should be selected already) and choose
"boot"
"RebuildBS"
"Write"  

then press "q" a few times to quit  testdisk.

Also from the error messages you got, it seem that you are booting from the Windows drive (/dev/sdb). So use

title Windows XP
rootnoverify (hd0,0)
chainloader +1

in menu.lst

---

### Post by UberMetaller on 2009-05-01
After following those steps for both my recovery partition and my windows xp partition, I still am returned with a "NTLDR is Missing" error for the recovery drive, and now when I try the windows XP partition, I get a "GRUB: HARD DRIVE ERROR".

---

### Post by meierfra. on 2009-05-01
Sorry. I gave you the wrong set of  instructions.  (You needed to do "BackUp BS" and not "Rebuild BS". Unfortunately, "Backup BS" does not works anymore after "Rebuild BS".  But you can  also fix the boot sector with you Windows CD:

Boot from the Windows CD, "press r" to get to the repair console.

Type 

```
map
```

to determine the drive letter for your Windows partitions. Then

```
fixboot C:
```

but replace "C" by the actual drive letter of your  Windows partition.

If this does not work, or you don't have a Windows CD, let me know, there is one more method to fix the boot sector.

---

### Post by UberMetaller on 2009-05-02
I'm afraid my computer didn't come with a Windows XP disk.

---

### Post by meierfra. on 2009-05-02
Maybe, RebuildBS didn't actually  rewrote the boot sector, in which case "BackupBS"  should  works. So  try this



```

cd ~/Desktop
sudo testdisk-6.11/linux/testdisk_static /dev/sdb

```

(this assumes that you didn't deleted tesdisk from the desktop. Otherwise use the instructions from my previous post to download and install testdisk again)

Choose "proceed" on the first screen, then
"intel"
"advanced",
Select the Windows partition (although it should be selected already) and choose
"boot"
"BackupBS"
Type "Y" to confirm.
  
then press "q" a few times to quit  testdisk, reboot and see whether you can boot into Windows.


**If you did not get the "BackupBS" option, try this instead:**

Download the attached file "XP_nine.txt" to your desktop. Open a terminal
and type


```
 sudo dd if=~/Desktop/XP_nine.txt of=/dev/sdb1 bs=1 seek=80 skip=80

```

Be very careful with the "dd" command. If it runs for more than just a couple of seconds, stop the process with "ctrl+C".

---

### Post by UberMetaller on 2009-05-02
Yar, I got no Backup_BS option, however, your second suggestion did the trick :) Thank you very much for your help and patience, I greatly appreciate it.

---

### Post by meierfra. on 2009-05-02
> your second suggestion did the trick

Great. Have fun with XP and Ubuntu.

---

