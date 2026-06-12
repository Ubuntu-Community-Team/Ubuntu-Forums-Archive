---
title: "Grub and Dual Boot after upgrading to Karmic"
date: 2009-11-11
forum: Installation &amp; Upgrades
---

### Post by Cdeflon on 2009-11-11
Hello all and thank you for reading.

When up graded from 9.04 to 9.10 it replaced my old menu.lst with a new one, well that's ok, only thing is that last time I tried to get the dual boot to work it took me like 6 hours of messing around to get it to work.

Windows is not installed on the first HD and thus I get "error 13: Invalid or unsupported executable format"
My menu.lst currently looks like this:

title           Microsoft Windows XP Professional
rootnoverify    (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     (hd1,0)+1


However, there is a bit of a curiosity... I've got three hard-drives one of which only shows up when it feels like, there seem to be a 50/50 chance of it actually being identified when starting the computer, well anyways. fdisk -l gives me:

Disk /dev/sda: 300.1 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4f2f1539

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10942    87891583+   7  HPFS/NTFS
/dev/sda2           10943       15805    39062047+   c  W95 FAT32 (LBA)
/dev/sda3           15806       33920   145508737+   c  W95 FAT32 (LBA)
/dev/sda4           33921       36483    20587297+  83  Linux

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00075133

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       18236   146480638+  83  Linux
/dev/sdb2           18237       21275    24410767+  83  Linux
/dev/sdb3           21276       30401    73304595   83  Linux

Disk /dev/sdc: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3ac23ac2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        3075    24699906    7  HPFS/NTFS
/dev/sdc2            3076        7684    37021792+  83  Linux
/dev/sdc3            7685       19865    97843882+  83  Linux
/dev/sdc4           19866       19929      514080   82  Linux swap / Solaris



I have obviously tried swapping around all and everything regarding the "map" options, using hd1 and hd2 and so on, but nothing seems to work.

If someone else who has a better insight in to grubs workings could take a look at this, highly annoying, problem I would be much grateful.

Best regards
/C

---

### Post by Mark Phelps on 2009-11-11
MS Windows always wants to be launched from the "first" drive, which is by default, the boot drive.  So, if you're not booting from the drive containing MS Windows, you have to fake it out using MAP commands to believe it IS the first drive.

Thus, presume the following:
-- Booting from drive #1 -- not containing MS Windows
-- Drive #2 has MS Windows on it

In this case, your menu.lst entries would have:
rootnoverify (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

Tricky part is that in a three-drive system, it may be difficult to figure out what drive GRUB believes is #2 and which one GRUB believes is #3.

But, you can experiment with the menu.lst entries above, changing "hd1" to "hd2" if necessary. Also, change chainloader to +2 if MS Windows is on the "third" drive.

---

### Post by oldfred on 2009-11-11
It concerns me that you say one of your drives only shows up some of the time. Is this a mixed sata & pata configuration?

Since you have two windows partitions flagged as boot and a variety of linux partitions it may be best to fully document your boot configuration:

Boot Info Script 0.32 courtesy of forum member meierfra
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)
Instructions
[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)
cd to directory saved to:
chmod 755 boot_info_script032.sh
sudo ./boot_info_script032.sh
or as example if on desktop
sudo bash ~/Desktop/boot_info_script*.sh
This will create a RESULTS.txt file in the same directory. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by Cdeflon on 2009-11-11
Thank you very much for your time and attention guys, it's much appriciated.

I past the information requested below:

```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on boot drive #2 in 
    partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdc and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdc2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdc3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: Stale NFS file handle

sdc4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 300.1 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders, total 586114704 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4f2f1539

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   175,783,229   175,783,167   7 HPFS/NTFS
/dev/sda2         175,783,230   253,907,324    78,124,095   c W95 FAT32 (LBA)
/dev/sda3         253,907,325   544,924,799   291,017,475   c W95 FAT32 (LBA)
/dev/sda4         544,924,800   586,099,394    41,174,595  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00075133

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   292,961,339   292,961,277  83 Linux
/dev/sdb2         292,961,340   341,782,874    48,821,535  83 Linux
/dev/sdb3         341,782,875   488,392,064   146,609,190  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders, total 320173056 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3ac23ac2

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63    49,399,874    49,399,812   7 HPFS/NTFS
/dev/sdc2          49,399,875   123,443,459    74,043,585  83 Linux
/dev/sdc3         123,443,460   319,131,224   195,687,765  83 Linux
/dev/sdc4         319,131,225   320,159,384     1,028,160  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="754552bb-cb71-4fc9-8506-832db2dbdefb" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda2: LABEL="MUSIC" UUID="88CC-AE3A" TYPE="vfat" 
/dev/sda3: UUID="CD33-055D" TYPE="vfat" 
/dev/sda4: UUID="b2940501-77cf-49e6-847e-c765838d05ae" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb1: LABEL="Series1" UUID="8d20d1fe-c5ad-4f03-9cff-fd032484c2a2" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb2: UUID="dbfab641-e48c-4cd7-a4d6-3950b1c3badd" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb3: LABEL="Movies1" UUID="fcb6b7c8-600c-46af-8068-3f4059070a5d" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc1: UUID="D6B8004AB8002B95" TYPE="ntfs" 
/dev/sdc2: UUID="d51299f6-502f-412f-a5b9-ea198b73f728" TYPE="ext3" 
/dev/sdc3: UUID="0e6dd767-b004-4d77-bd95-0813f88fc487" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc4: UUID="115d65b7-a0f0-4ac5-9007-9085fbf258b2" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sdc2 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sdc1 on /media/windows type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/carl/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=carl)


================================ sdc1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

=========================== sdc2/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=d51299f6-502f-412f-a5b9-ea198b73f728 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=d51299f6-502f-412f-a5b9-ea198b73f728

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

title		Ubuntu 9.10, kernel 2.6.31-15-generic
uuid		d51299f6-502f-412f-a5b9-ea198b73f728
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=d51299f6-502f-412f-a5b9-ea198b73f728 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-15-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode)
uuid		d51299f6-502f-412f-a5b9-ea198b73f728
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=d51299f6-502f-412f-a5b9-ea198b73f728 ro  single
initrd		/boot/initrd.img-2.6.31-15-generic

title		Ubuntu 9.10, kernel 2.6.31-14-generic
uuid		d51299f6-502f-412f-a5b9-ea198b73f728
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=d51299f6-502f-412f-a5b9-ea198b73f728 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-14-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid		d51299f6-502f-412f-a5b9-ea198b73f728
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=d51299f6-502f-412f-a5b9-ea198b73f728 ro  single
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 9.10, kernel 2.6.28-11-generic
uuid		d51299f6-502f-412f-a5b9-ea198b73f728
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=d51299f6-502f-412f-a5b9-ea198b73f728 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.10, kernel 2.6.28-11-generic (recovery mode)
uuid		d51299f6-502f-412f-a5b9-ea198b73f728
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=d51299f6-502f-412f-a5b9-ea198b73f728 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.10, memtest86+
uuid		d51299f6-502f-412f-a5b9-ea198b73f728
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
rootnoverify	(hd0,0)
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1


title           Microsoft Windows XP Professional2
rootnoverify    (hd0,0)
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1


title           Microsoft Windows XP Professional3
rootnoverify    (hd1,0)
makeactive
map             (hd0) (hd2)
map             (hd2) (hd0)
chainloader     +1


=============================== sdc2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb2 during installation
UUID=d51299f6-502f-412f-a5b9-ea198b73f728 /               ext3    relatime,errors=remount-ro 0       1
# /media/windows was on /dev/sdb1 during installation
UUID=D6B8004AB8002B95 /media/windows  ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
# swap was on /dev/sdb4 during installation
UUID=115d65b7-a0f0-4ac5-9007-9085fbf258b2 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdc2: Location of files loaded by Grub: ===================


  25.2GB: boot/grub/menu.lst
  25.2GB: boot/grub/stage2
  25.2GB: boot/initrd.img-2.6.28-11-generic
  25.2GB: boot/initrd.img-2.6.31-14-generic
  25.2GB: boot/initrd.img-2.6.31-15-generic
  25.2GB: boot/vmlinuz-2.6.28-11-generic
  25.2GB: boot/vmlinuz-2.6.31-14-generic
  25.2GB: boot/vmlinuz-2.6.31-15-generic
  25.2GB: initrd.img
  25.2GB: initrd.img.old
  25.2GB: vmlinuz
  25.2GB: vmlinuz.old
```

I've been messing the the settings for ages now... However I haven't tried chainloader +2 yet.
What does that option even do?

Best Regards
/Carl

---

### Post by Cdeflon on 2009-11-11
Just for the sheer hell of it I just tried these alternations and none of them worked:

```

title           Microsoft Windows XP Professional3
rootnoverify    (hd0,0)
makeactive
map             (hd0) (hd2)
map             (hd2) (hd0)
chainloader     +2

title           Microsoft Windows XP Professional4
rootnoverify    (hd1,0)
makeactive
map             (hd0) (hd2)
map             (hd2) (hd0)
chainloader     +2


title           Microsoft Windows XP Professional5
rootnoverify    (hd0,0)
makeactive
map             (hd0) (hd2)
map             (hd2) (hd0)
chainloader     +1

```

---

### Post by oldfred on 2009-11-11
BIOS, grub and Ubuntu do not always agree on drive order. The only way you can boot ubuntu is if sdc is first as that has grub legacy which points to the only menu.lst on sdc2. If that is correct then windows is also on the first drive and no mapping commands are required. If the partition is flagged as boot the makeactive command is not required.

I would try:

title           Microsoft Windows XP Professional
rootnoverify    (hd0,0)
savedefault
chainloader     +1

---

### Post by Mark Phelps on 2009-11-11
> **Cdeflon said:**
> Just for the sheer hell of it I just tried these alternations and none of them worked:

```

title           Microsoft Windows XP Professional3
rootnoverify    (hd0,0)
makeactive
map             (hd0) (hd2)
map             (hd2) (hd0)
chainloader     +2

title           Microsoft Windows XP Professional4
rootnoverify    (hd1,0)
makeactive
map             (hd0) (hd2)
map             (hd2) (hd0)
chainloader     +2


title           Microsoft Windows XP Professional5
rootnoverify    (hd0,0)
makeactive
map             (hd0) (hd2)
map             (hd2) (hd0)
chainloader     +1

```

Sorry, should have been more specific -- the settings have to match in a specific way.

If you have rootnoverify (hd2,0) you must then have map (hd0) (hd2) and map (hd2) (hd0) commands.

So, basically, one of the map options has to match the hd# in the root noverify command, the other has to be hd0.

If the rootnoverify has hd0, you do not need MAP commands as it is already pointing to drive "0".

---

