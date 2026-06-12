---
title: "unable to access NTFS RAID 1 XPx64 drive"
date: 2009-09-11
forum: Installation &amp; Upgrades
---

### Post by gilpster on 2009-09-11
Hi everyone i'm new to ubuntu (and linux for that matter) and I throw myself at your mercy:
 
I had a computer with windows XP x64 on an NTFS RAID 1 (mirror) array, as well as three other fat32 drives (one with windows XP installed on it)
 
Fed up with the lack of support for XP x64 which dried up really as soon as the OS was released I decided to install ubuntu as a dual boot, with the idea of migrating to linux idc (i mainly use my vista laptop nowadays)
 
I tried the CD version and everything worked fine. I was able to browse my NTFS file on my RAID drive, for example.
 
Since then I've installed ubuntu but immediately afterwards i couldn't mount my NTFS RAID drive at all. I also can't boot to windows XP x64 either! I really can't get at the data on this drive.
 
To make matters worse my wife now tells me there are some pictures of our children when they were just born on this drive that we don't have elsewhere... she'd put them on the mirror RAID because she thought that was the safest place for them.:cry:
 
i read the thread below which suggested using the boot info script. please find this attached. the first two 250GB drives are the mirror RAID
 
I've not enjoyed this experience at all: any help appreciated.
 
```
 
============================= Boot Info Summary: ==============================
 => Syslinux is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
 => Windows is installed in the MBR of /dev/sdd
 => Grub0.97 is installed in the MBR of /dev/sde and looks on boot drive #3 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdf
sda1: _________________________________________________________________________
    File system:       
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda1 and 
                       looks at sector 73891919 on boot drive #3 for the 
                       stage2 file. A stage2 file is at this location on 
                       /dev/sdd. Stage2 looks on partition #1 for 
                       /boot/grub/menu.lst.
    Mounting failed:
mount: unknown filesystem type ''
sdb1: _________________________________________________________________________
    File system:       
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sdb1 and 
                       looks at sector 211927103 on boot drive #4 for the 
                       stage2 file. A stage2 file is at this location on 
                       /dev/sdd. Stage2 looks on partition #1 for 
                       /boot/grub/menu.lst.
    Mounting failed:
mount: unknown filesystem type ''
sdc1: _________________________________________________________________________
    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   
sdd1: _________________________________________________________________________
    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab
sdd2: _________________________________________________________________________
    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  
sdd5: _________________________________________________________________________
    File system:       swap
    Boot sector type:  -
    Boot sector info:  
sde1: _________________________________________________________________________
    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   
sdf1: _________________________________________________________________________
    File system:       vfat
    Boot sector type:  MSDOS5.0: Fat 16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   
=========================== Drive/Partition Info: =============================
Drive: sda ___________________ _____________________________________________________
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xffffffff
Partition  Boot         Start           End          Size  Id System
/dev/sda1    *             63   488,375,999   488,375,937   7 HPFS/NTFS
 
Drive: sdb ___________________ _____________________________________________________
Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xffffffff
Partition  Boot         Start           End          Size  Id System
/dev/sdb1    *             63   488,375,999   488,375,937   7 HPFS/NTFS
 
Drive: sdc ___________________ _____________________________________________________
Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x681640bc
Partition  Boot         Start           End          Size  Id System
/dev/sdc1    *             63   312,496,379   312,496,317   7 HPFS/NTFS
 
Drive: sdd ___________________ _____________________________________________________
Disk /dev/sdd: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc1a48f18
Partition  Boot         Start           End          Size  Id System
/dev/sdd1                  63   300,511,889   300,511,827  83 Linux
/dev/sdd2         300,511,890   312,576,704    12,064,815   5 Extended
/dev/sdd5         300,511,953   312,576,704    12,064,752  82 Linux swap / Solaris
 
Drive: sde ___________________ _____________________________________________________
Disk /dev/sde: 20.4 GB, 20404101120 bytes
255 heads, 63 sectors/track, 2480 cylinders, total 39851760 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe03ee03e
Partition  Boot         Start           End          Size  Id System
/dev/sde1    *             63    39,841,199    39,841,137   c W95 FAT32 (LBA)
 
Drive: sdf ___________________ _____________________________________________________
Disk /dev/sdf: 2048 MB, 2048901120 bytes
64 heads, 63 sectors/track, 992 cylinders, total 4001760 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000
Partition  Boot         Start           End          Size  Id System
/dev/sdf1    *             63     3,999,743     3,999,681   6 FAT16
 
blkid -c /dev/null: ____________________________________________________________
/dev/sdc1: UUID="86B8F1A8B8F19741" LABEL="150GB WinXP32" TYPE="ntfs" 
/dev/sdd1: UUID="8e7e6228-7856-4eac-96ec-2de77cb25ed3" TYPE="ext3" 
/dev/sdd5: TYPE="swap" UUID="d7010451-5150-4e67-a2ca-f505f5156333" 
/dev/sde1: LABEL="19GB FAT32" UUID="9C86-A9BD" TYPE="vfat" 
/dev/sdf1: SEC_TYPE="msdos" UUID="3B69-1AFD" TYPE="vfat" 
=============================== "mount" output: ===============================
/dev/sdd1 on / type ext3 (rw,relatime,errors=remount-ro)
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
gvfs-fuse-daemon on /home/kenneth/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=kenneth)
/dev/sr0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,utf8,user=kenneth)
/dev/sdc1 on /media/150GB WinXP32_ type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdf1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
 
=========================== sdd1/boot/grub/menu.lst: ===========================
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
default  0
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout  10
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
# title  Windows 95/98/NT/2000
# root  (hd0,0)
# makeactive
# chainloader +1
#
# title  Linux
# root  (hd0,1)
# kernel /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=8e7e6228-7856-4eac-96ec-2de77cb25ed3 ro
## default grub root device
## e.g. groot=(hd0,0)
# groot=8e7e6228-7856-4eac-96ec-2de77cb25ed3
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
title  Ubuntu 9.04, kernel 2.6.28-11-generic
uuid  8e7e6228-7856-4eac-96ec-2de77cb25ed3
kernel  /boot/vmlinuz-2.6.28-11-generic root=UUID=8e7e6228-7856-4eac-96ec-2de77cb25ed3 ro quiet splash 
initrd  /boot/initrd.img-2.6.28-11-generic
quiet
title  Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid  8e7e6228-7856-4eac-96ec-2de77cb25ed3
kernel  /boot/vmlinuz-2.6.28-11-generic root=UUID=8e7e6228-7856-4eac-96ec-2de77cb25ed3 ro  single
initrd  /boot/initrd.img-2.6.28-11-generic
title  Ubuntu 9.04, memtest86+
uuid  8e7e6228-7856-4eac-96ec-2de77cb25ed3
kernel  /boot/memtest86+.bin
quiet
### END DEBIAN AUTOMAGIC KERNELS LIST
# This is a divider, added to separate the menu items below from the Debian
# ones.
title  Other operating systems:
root
 
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title  Windows XP Professional x64 Edition
rootnoverify (hd1,0)
savedefault
map  (hd0) (hd1)
map  (hd1) (hd0)
chainloader +1
 
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title  Microsoft Windows XP Professional
rootnoverify (hd2,0)
savedefault
map  (hd0) (hd2)
map  (hd2) (hd0)
chainloader +1
 
=============================== sdd1/etc/fstab: ===============================
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdd1 during installation
UUID=8e7e6228-7856-4eac-96ec-2de77cb25ed3 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdd5 during installation
UUID=d7010451-5150-4e67-a2ca-f505f5156333 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda1       /media/NTFSx64   ntfs-3g defaults,locale=en_US.utf8 0 0
=================== sdd1: Location of files loaded by Grub: ===================
 
 108.4GB: boot/grub/menu.lst
 108.5GB: boot/grub/stage2
 108.4GB: boot/initrd.img-2.6.28-11-generic
 108.5GB: boot/vmlinuz-2.6.28-11-generic
 108.4GB: initrd.img
 108.5GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============
sdg sdh sdi sdj 

```

---

### Post by ronparent on 2009-09-11
It appear like you may have inadvertently pretty well mucked up your system. I can't tell for sure, but what are your raid drives - I would guess sda and sdb? You might have a bootable version of windows on sdc if that were set a first drive in bios. Also from menu.lst it appears that you have a bootable ubuntu 9.04 on sde - although there doesn't seem to be a coresponding grub MBR to boot to it. sda and sdb both seem to be out of play. I Suspect that if anything is recoverable from your windows files it would have to be elsewhere from sda, sdb. It would probably be best to start a dialog to recover what can be recovered.

I'm glad you posted the result of the boot info script, because we may have to fall back on that to unravel what can be unraveled.

---

### Post by gilpster on 2009-09-11
thanks for the reply:
 
my raid drives are sda and sdb as you say.  they should be identical of course.
 
sdc is a spare NTFS drive which did have winXP on it (doesn't now)
 
sdd is the ubuntu drive - although is physically identical to sdc is entirely seperate (i.e. not RAID, different format)
 
sde is a spare FAT32 drive
 
It's all very well to say that i've inadvertantly mucked up my system but all I did was install ubuntu!  - something i bitterly regret now.  The only other thing I have done is try to boot to windows through the GRUB bootable CD.
 
I have just tried to re-install windows XPx64 over the old version but the windows CD cannot find _any_ drive on the computer other than the 20GB fat32.  Is it worth installing windows onto that then trying to claim the NTFS raid from within the windows OS?
 
kenneth

---

### Post by ronparent on 2009-09-11
"Is it worth installing windows onto that then trying to claim the NTFS raid from within the windows OS?"

The answer to that is probably no. Now to try to sort things out. Your results.txt indicate ubuntu is installed only to sdd. Although you say a duplicate should exist on sdc, that is not indicated. As a matter of fact no duplicate ubuntu intall is found. Both sdc and sde seem to contain a windows xp install. The one on sdc, if it were first in boot order in bios, might be bootable because there is a windows MBR on that drive. sde does not have a MBR. It is probably safe to say that neither windows on sdc nor sde would recognize any raid drive because you probably didn't set them up as raid! 

What is the best course of action. You could probably boot sdd after setting that first in boot order and doing a grub setup write grub to the MBR of that drive.

As I previously stated you might be able to boot sdc in windows (only) if it retains its integrity and you set that drive first in boot order, but, with no access to a raid (I don't know if raid driver can be added after installation).

If you decide you have to reinstall win xp to sda/sdb, you will be abandoning all chance to ever recover any data from those drives (they probably a wrecked beyond recovery anyway?). To do that you could first examine those drive from gparted in the live cd and determine if there are any partitions with recoverable data (not high hopes but an easy test). If there are no recognizable partitions you might be able to use gparted to clean the drives or create an ntfs partition. There is no way to say what you will find or what you can do with it from results.txt.

I made the staement that you inadvertentl mucked up your system because dmraid is not supported on the live cd unless you installed dmraid while booted for use while the live cd was active. But one of my bones of contention with the ubuntu community there are sufficient ambiguities in the standard install process that you are paractically invited to wipe out anything on the raid drives! So there is no critism of you in this regard. You can't be expected to recognize the pitfalls without raid experience in ubuntu.

I've given you a lot to chew on here. After you digest this for a while, be sure to post back if you need specific help.

ron

---

### Post by gilpster on 2009-09-27
well I rescued the data on my drives by re-installing windows onto a seperate fat32 drive, then running a data rescue program - NTFS advanced file recovery - on one of the RAID drives (unplugging the other).

Despite the drive not being recognised by either windows or ubuntu the program was able to successfully find the entire file structure and I could rescue the pictures of our children (phew)

I then broke the mirror raid in my motherboard bios, then performed a quick format on both.  I can now access both NTFS drives from windows and ubuntu.

Can I sound a note of caution here:

1) having a mirror RAID didn't particular protect my data, as the same file error corrupted both my drives.
2) installing ubuntu royally screwed my RAID drives.  This was unexpected given that they were entirely separate from the drive the OS was installed onto.

**ubuntu should make it clearer that it can damage any RAID system on your computer, even when it isn't the ubuntu install drive**

now i need to get the internet to work.  In comparison it took me about 30mins to install vista.

kenneth

---

