---
title: "Dual boot installation advice needed"
date: 2009-03-05
forum: Installation &amp; Upgrades
---

### Post by Roob on 2009-03-05
Hi all,

Last week I tried to install Xubuntu on a system with WinXP installed, but this went [horribly wrong]("http://ubuntuforums.org/showthread.php?t=1084528"); after installing Xubuntu my XP partition was gone. So today I'm going to do a second attempt installing both OS-es, and I could surely use some advice.

System:
- Abit BX133 (with integrated Highpoint 370 RAID controller)
- Intel P3 1 GHz CPU
- 768 kB Mem
- CDrom drive on IDE-1 as prim. master
- 1 200 GB HDD connected to RAID-IDE-controller (already partitioned on another system):
* part. 1 (prim, NTFS): 12 GB, empty for WinXP, 
* part. 2 (prim, NTFS): 10 GB, empty for Xubuntu
* part. 3 (logical, NTFS): 178 GB Data
- (There were 2 different HDD's, 160 GB resp. 20 GB) in this system, but I'll start by disconnecting them)
- (System is mainly used for browsing the internet, mail and watching movies, so I reckon partition sizes are okay)


In the light of my recent experience installing Xubuntu on the system with XP allready installed, I'm now thinking of reversing the order (I think Xubuntu has problems with the Highpoint controller, I found a simular case on the Internet [here]("http://www.linuxquestions.org/questions/linux-software-2/grub-problem-loading-stage-1.5-in-infinited-loop-654104/")).

So this is my plan:
1. Install Xubuntu in the second partition. Check if it works.
2. Install WinXP in the first partition. Check if it works.
3. [Reinstall Grub]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")
4. If both OS-es are allright and accesible through Grub: reconnect old HD's and boot into either OS. Move the data from the old "DATA"-partition of the old 160 GB drive to the new one. (Remove this drive and take it home)
5. Format the 20 GB drive. Use this drive to store images of both OS-partitions and a back-up of most important document.

Your thoughts or suggestions are more than welcome!

---

### Post by Roob on 2009-03-06
This again was not as straightforward as I hoped it to be. Long story short: I couldn't get Xubuntu to install in the second partition.

So I adapted my plan, and first installed WinXP in the first partition. I booted into XP, installed Partition Magic and merged the second and third partitions. Then I booted into the LiveCD again and installed Xubuntu at the end of the second partition.

I booted from my HD again and - surprise, surprise - as soon as "Grub Loading stage 1.5" appeared, system rebooted into an endless loop.

It probably would have been pretty straightforward to solve this, but I didn't have the time to boot into the LiveCD again and browse the internet for a solution. Furthermore getting XP to work again is my friend's first priority, so I reinstalled WinXP in the same partition (didn't bother trying "fixmbr", although that probably would have done the trick in this case). Of course now when booting from my HD I could only get into WinXP.

So I booted from the LiveCD to find out where I stand:

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0cea4b45

   Device Boot      Start      End      Blocks    Id   System
/dev/sda1   *          1      1785    14337981     7   HPFS/NTFS
/dev/sda2           1786     24321   181020420     f   W95 Ext'd (LBA)
/dev/sda5           1786     22955   170047993+    7   HPFS/NTFS
/dev/sda6          22956     24257    10458283+   83   Linux
/dev/sda7          24258     24321      514048+   82   Linux swap / Solaris

Disk /dev/sdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9e369e36

   Device Boot      Start        End       Blocks    Id   System
/dev/sdb1   *           1       2327      18691596    83   Linux
/dev/sdb2            2328       2434        859477+   5   Extended
/dev/sdb5            2328       2434        859446    82   Linux swap / Solaris

Disk /dev/sdc: 8019 MB, 8019509248 bytes
16 heads, 32 sectors/track, 30592 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0xdfa4a156

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       30592     7831536    b  W95 FAT32
```

sda is my 200 GB harddisk with WinXP installed in the first partition, followed by a NTFS data partition, Xubuntu partition and the SWAP partition.
sdb contains the remainders of my first failed Xubuntu install and can be ignored (I'll wipe the disk and 'll use it as a backup drive as explained in my previous post).
sdc is a USB stick


"sudo bash ~/Desktop/boot_info_script*.sh":
```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb
 => No boot loader? is installed in the MBR of /dev/sdc

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
    Boot sector info:  According to the info in the boot sector, sda5 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
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
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0cea4b45

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *                  63     28,676,024     28,675,962   7 HPFS/NTFS
/dev/sda2           28,676,025   390,716,864   362,040,840   f W95 Ext d (LBA)
/dev/sda5           28,676,088   368,772,074   340,095,987   7 HPFS/NTFS
/dev/sda6         368,772,138   389,688,704     20,916,567  83 Linux
/dev/sda7         389,688,768   390,716,864       1,028,097  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders, total 39102336 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9e369e36

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *                 63    37,383,254    37,383,192  83 Linux
/dev/sdb2          37,383,255    39,102,209     1,718,955    5 Extended
/dev/sdb5          37,383,318    39,102,209     1,718,892  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 8019 MB, 8019509248 bytes
16 heads, 32 sectors/track, 30592 cylinders, total 15663104 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xdfa4a156

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  32    15,663,103    15,663,072   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="1535319E481E6089" TYPE="ntfs" 
/dev/sda5: UUID="BEDEBE9AE5A88189" TYPE="ntfs" 
/dev/sda6: UUID="54f744e1-80f2-4369-bee9-f89208d0c9d9" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: TYPE="swap" UUID="221a5e9e-84ca-4c8e-ad5e-a47a774760e4" 
/dev/sdb1: UUID="d7414e7f-58fb-4d29-b93b-a6ad9a7033e4" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: TYPE="swap" UUID="4d062ec7-7f94-4665-88eb-cad3b870a043" 
/dev/loop0: TYPE="squashfs" 
/dev/sdc1: LABEL="USB" UUID="8E35-50FE" TYPE="vfat" 

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
/dev/sdc1 on /media/USB type vfat (rw,nosuid,nodev,uhelper=hal,utf8,shortname=winnt,uid=999)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

=========================== sda6/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=54f744e1-80f2-4369-bee9-f89208d0c9d9 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=54f744e1-80f2-4369-bee9-f89208d0c9d9

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
uuid		54f744e1-80f2-4369-bee9-f89208d0c9d9
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=54f744e1-80f2-4369-bee9-f89208d0c9d9 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		54f744e1-80f2-4369-bee9-f89208d0c9d9
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=54f744e1-80f2-4369-bee9-f89208d0c9d9 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		54f744e1-80f2-4369-bee9-f89208d0c9d9
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
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=54f744e1-80f2-4369-bee9-f89208d0c9d9 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=221a5e9e-84ca-4c8e-ad5e-a47a774760e4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 197.5GB: boot/grub/menu.lst
 197.6GB: boot/grub/stage2
 197.5GB: boot/initrd.img-2.6.27-7-generic
 197.6GB: boot/vmlinuz-2.6.27-7-generic
 197.5GB: initrd.img
 197.6GB: vmlinuz

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
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# kopt=root=UUID=d7414e7f-58fb-4d29-b93b-a6ad9a7033e4 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=d7414e7f-58fb-4d29-b93b-a6ad9a7033e4

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
uuid		d7414e7f-58fb-4d29-b93b-a6ad9a7033e4
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=d7414e7f-58fb-4d29-b93b-a6ad9a7033e4 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		d7414e7f-58fb-4d29-b93b-a6ad9a7033e4
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=d7414e7f-58fb-4d29-b93b-a6ad9a7033e4 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		d7414e7f-58fb-4d29-b93b-a6ad9a7033e4
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=d7414e7f-58fb-4d29-b93b-a6ad9a7033e4 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=4d062ec7-7f94-4665-88eb-cad3b870a043 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


  18.4GB: boot/grub/menu.lst
  18.4GB: boot/grub/stage2
  18.4GB: boot/initrd.img-2.6.27-7-generic
  18.4GB: boot/vmlinuz-2.6.27-7-generic
  18.4GB: initrd.img
  18.4GB: vmlinuz
```

I have only two questions: how can I get the system to dual-boot? Will it suffice to reinstall Grub by following the procedure described [here]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")? Second question is whether this involves any danger of loosing my WinXP partition again.


I hope one of you guys or girls find some time to answer. Thanks for reading!

---

### Post by cfree220 on 2009-03-06
Hmmm
I have my laptop set up in dual boot, although my configuration is different (I use the Media Direct button as a second power button). I'm not sure if there are any major differences between dual booting Ubuntu and Vista vs Ubuntu and XP... I think I read somewhere that you need to make some sort of change to XP to prevent it from seeing your Linux partition.

My hard drive looks like this:
/dev/sda1  ext3  47.03MiB - Boot Partition (Windows)
/dev/sda2  ntfs  45.00GiB - Windows Vista Ultimate
/dev/sda3  ext3  12.00GiB - Ubuntu 8.10
/dev/sda4  extended 241.05GiB - extended partition containing swap and data files
    /dev/sda5 linux-swap 8.00GiB
    /dev/sda6 ntfs 233.05GiB - Storage volume

In retrospect, I probably could have placed the Ubuntu partition at the beginning of the disk to make it faster (as it is my primary operating system). However, I believe that, in order for Windows to boot, it must start within the first 8GiB of the HDD. For me, that might not have been practical size-wise. However, I'd say that 10GB is probably more than you need for a lightweight OS like Xubuntu. Of my allocated 12, I'm only using 8.1 with Ubuntu. This includes, I believe, some large files that I mistakenly placed in the home folder, as opposed to on the storage volume. You would probably be able to put Xubuntu on 6-7GiB without any problems.

Hopefully the above will be useful to you in some way, shape or form. As for the actual installation, I would always start with Windows, and then do the linux install. My experience with dual booting using one boot loader for multiple OS's is limited to the time I installed Ubuntu on an external hard drive and overwrote the windows MBR with Grub (the result being that the system could not boot unless the external HDD was attached with no other storage devices attached during boot). For the record, at least with Vista, fixmbr is NOT able to save you from an overwritten MBR. Nor is fixboot, or any of the other tools offered by bootrec.exe. I've had this problem twice and, not being a wizard when it comes to boot, I have had to reinstall Windows each time on account of this.

One thing that you might try is Supergrub. If I recall correctly, an attempt to fix the mbr using this resulted in the use of the windows boot loader (which can be used, I believe, for both OS's). You might try installing Xubuntu and opt not install GRUB and see if you can use the windows boot loader.

You might also want to check out this [tutorial]("http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm?page=1") on how to dual boot XP and Linux with XP already installed. The article assumes that the XP partition takes up the entire disk, but from the looks of your posts, you shouldn't have any problems adjusting for your own configuration.

---

### Post by cfree220 on 2009-03-06
Actually, I just looked at the last page of that tutorial. Apparently GRUB is better at booting non-windows OS's than is the XP bootloader. Also, I apologize for not thoroughly reading your second post and focusing on those questions. I would say that following the instruction in that article is unlikely to cause any problems.I say this not because I am familiar with the procedure or, necessarily, the code used. Rather, I speak from my own confidence in the accuracy of the information available through Ubunut's documentation. That said, you should not need to follow those instructions, unless you installed you linux OS before XP (Which from my understanding is not the case). If you already have XP installed, and you wish to use GRUB to load Xubuntu and XP, then all you should have to do is install GRUB to it's default location, overwriting the existing Windows MBR. You noted that this did not work for you the first time. You might want to try creating a new install disk and be sure to check it for errors before actually installing.

---

### Post by Whorehay on 2009-03-06
[**_[COLOR="Red"]This wiki[/COLOR]_**]("http://wiki.archlinux.org/index.php/Windows_and_Arch_Dual_Boot") was made for Arch Linux, but it can help explain why GRUB can't "see" your XP partition.  Unless you formatted over it, XP is still there... but you have to tell GRUB where!  Make sure you install GRUB on **sda**, not sda1, sda2, etc.

If you scroll down a bit you will see an installation guide with screenshots [**_[COLOR="Red"]here[/COLOR]_**]("http://mywebsite.bigpond.net.au/dfelderh/linuxmaniac/p24.html").
> *Ubuntu will automatically scan my hard disks for other operating systems and add them to the boot loader's menu so I'll be able to boot any of my operating systems when I reboot without any manual configuring needed, it works perfectly in 999/1000 computers. Sometimes we might need to do some fiddling to get things right, but it's normally pretty simple.*

I don't know how the RAID setup complicates things for you since I have never had to deal with it.   Personally, I'd wipe the Ubuntu partition and start fresh.  Do your backups and keep your Windows CD handy in case you need to boot into the Recovery Console to repair your MBR.  Worst case scenario you will still be able to boot into Windows and not be left without access to your system.

---

### Post by cfree220 on 2009-03-06
Just an update on my comment about the size of your Xubuntu partition:
I went through and cleaned up most of the files from my home folder that should not have been there. My system size is about 5 GiB, and is by no means lightweight or lacking in features.

---

### Post by Roob on 2009-03-07
I'm really stuck here, and could use some help. I carefully followed the instructions [here]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows").

```
sudo grub
find /boot/grub/stage1
```

This last command rendered:
```
(hd0,5)
```

So I entered at the Grub-prompt:
```
root (hd0,5)
setup
quit
```

After this the system rebooted into an endless loop after displaying "Grub Loading Stage1.5

I booted into the LiveCD once more, opened a terminal and tried
```
gksu gedit /boot/grub/menu.lst
```

The terminal really had to "think" about this one, and took its time to contemplate, but then the prompt returned w/o anything happening (as far as I could notice).

After this I tried:
```
sudo grub
root (hd0,6)
setup (hd0)
```

This rendered "Cannot mount selected partition"

This is where I'm at:
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0cea4b45

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1785    14337981    7  HPFS/NTFS
/dev/sda2            1786       24321   181020420    f  W95 Ext'd (LBA)
/dev/sda5            1786       22955   170047993+   7  HPFS/NTFS
/dev/sda6           22956       24257    10458283+  83  Linux
/dev/sda7           24258       24321      514048+  82  Linux swap / Solaris

Disk /dev/sdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9e369e36

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2        2434    19543072+   f  W95 Ext'd (LBA)
/dev/sdb5               2        2434    19543041    7  HPFS/NTFS

Disk /dev/sdc: 8019 MB, 8019509248 bytes
16 heads, 32 sectors/track, 30592 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0xdfa4a156

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       30592     7831536    b  W95 FAT32
```

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Syslinux is installed in the MBR of /dev/sdb
 => No boot loader? is installed in the MBR of /dev/sdc

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

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0cea4b45

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    28,676,024    28,675,962   7 HPFS/NTFS
/dev/sda2          28,676,025   390,716,864   362,040,840   f W95 Ext d (LBA)
/dev/sda5          28,676,088   368,772,074   340,095,987   7 HPFS/NTFS
/dev/sda6         368,772,138   389,688,704    20,916,567  83 Linux
/dev/sda7         389,688,768   390,716,864     1,028,097  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders, total 39102336 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9e369e36

Partition  Boot         Start           End          Size  Id System

/dev/sdb1              16,065    39,102,209    39,086,145   f W95 Ext d (LBA)
/dev/sdb5              16,128    39,102,209    39,086,082   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 8019 MB, 8019509248 bytes
16 heads, 32 sectors/track, 30592 cylinders, total 15663104 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xdfa4a156

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  32    15,663,103    15,663,072   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="1535319E481E6089" LABEL="WinXP" TYPE="ntfs" 
/dev/sda5: UUID="BEDEBE9AE5A88189" LABEL="DATA" TYPE="ntfs" 
/dev/sda6: UUID="54f744e1-80f2-4369-bee9-f89208d0c9d9" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: UUID="221a5e9e-84ca-4c8e-ad5e-a47a774760e4" TYPE="swap" 
/dev/sdb5: UUID="6874037F74034F6E" LABEL="BackUp" TYPE="ntfs" 
/dev/sdc1: LABEL="USB" UUID="8E35-50FE" TYPE="vfat" 
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
/dev/sdc1 on /media/USB type vfat (rw,nosuid,nodev,uhelper=hal,utf8,shortname=winnt,uid=999)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

=========================== sda6/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=54f744e1-80f2-4369-bee9-f89208d0c9d9 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=54f744e1-80f2-4369-bee9-f89208d0c9d9

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
uuid		54f744e1-80f2-4369-bee9-f89208d0c9d9
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=54f744e1-80f2-4369-bee9-f89208d0c9d9 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		54f744e1-80f2-4369-bee9-f89208d0c9d9
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=54f744e1-80f2-4369-bee9-f89208d0c9d9 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		54f744e1-80f2-4369-bee9-f89208d0c9d9
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
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=54f744e1-80f2-4369-bee9-f89208d0c9d9 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=221a5e9e-84ca-4c8e-ad5e-a47a774760e4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 197.5GB: boot/grub/menu.lst
 197.6GB: boot/grub/stage2
 197.5GB: boot/initrd.img-2.6.27-7-generic
 197.6GB: boot/vmlinuz-2.6.27-7-generic
 197.5GB: initrd.img
 197.6GB: vmlinuz
```

Please help, I'm desperate and close on giving up on (X)Ubuntu!

---

### Post by T.J. on 2009-03-07
The problem is that the LiveCD install disc defaults to erasing the first disc.  It also installs the boot loader on the first disc, assuming that Windows install that you have will accept that.  Windows XP Pro and Vista will not work if you do.  

You should configure your discs manually if you are dual booting.  If you let the installer do its own thing, it will erase the first hard disc.  When it asks about the bootloader during the install, use the "advanced" button to pick the second disc.  After that, set your BIOS to start from the second hard drive and you should be all set.


If you are using Vista, it gets messy, and you should probably use Windows' bootloader and the EasyBCD program.

---

### Post by Roob on 2009-03-07
T.J.,

I don't understand what you're saying. Are you aware I have both OS'es installed on one (my 'first') disk (from which I boot if I'm not booting from the LiveCD)? WinXP is on "sda1" and Xubuntu on "sda6".


Whorehay,

I'll read the Wiki for sure! I'm a bit (to) short of time on this, Reinstalling WinXP and all the apps, settings and codecs costed me tons of time and my my girl friend is getting pissed the PC is getting all the attention,so I havn't got to it yet.

Everybody: thanks for posting, hope you'll stay with me.

---

### Post by T.J. on 2009-03-07
I'm very sorry.  I should have paid more attention. I will try to make more sense.  

What I was trying to say is that if you installed from the normal Ubuntu disc, you have configure your partitions carefully during the install process or the Ubuntu installer might remove them including Windows. If you are using Windows XP Professional, XP64, or plan to use Vista, you will need to place the Linux bootloader in the Linux partition, not the Master boot record (what Ubuntu does by default).  The easiest way to boot then is to use EasyBCD (freeware configurator for the Windows Bootloader).

I'd be happy to help walk you through the process you need. Sometimes being clear on a message board isn't easy.

---

### Post by Roob on 2009-03-08
T.J.,

Thanks! I want to give Grub one more chance. It should be able to load both OS-es, and I'll carefully retrace my steps, I probably just made some stupid mistake/typo somewhere.

If this fails again, I'll try out EasyBCD, probably this will be next tuesday (I'll have to download and burn the image on my own system), and I sure could use your help there.

---

### Post by Roob on 2009-03-08
So I repeated all the steps I described in #7, careful not to make any mistakes (the instructions I got [here]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")).

```
sudo grub
find /boot/grub/stage1
```

Outcome was "(hd0,5)", so:
```
root (hd0,5)
setup (hd0)
quit
```

I once again executed
```
sudo bash ~/Desktop/boot_info_script*.sh
```

I won't post the Results.txt here, because I just carefully compared it to the one posted in post #7, and I did not find any differences.

I tried to edit menu1.lst:
```
gksu gedit /boot/grub/menu.lst
```

Once again, the terminal really had to think things over, but after a while it just returned the prompt, w/o anything happening:
```
ubuntu@ubuntu:~$ gksu gedit /boot/grub/menu.lst
ubuntu@ubuntu:~$ 
```
I guess this only works after booting into Ubuntu from a HDD (?).

I booted from the HDD, and found myself in the same endless boot-loop (system rebooted after displaying "Grub Loading Stage1.5").

So I booted into the LiveCD once more and executed the following code:
```
sudo mkdir /mnt/root
sudo mount -t ext3 /dev/sda6 /mnt/root
sudo mount -t ext3 /dev/sda1 /mnt/root/boot
ls /mnt/root
ls /mnt/root/boot
sudo grub-install --root-directory=/mnt/root /dev/sda
```

This is what the terminal looked like:
```
ubuntu@ubuntu:~$ sudo mkdir /mnt/root
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sda6 /mnt/root
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sda1 /mnt/root/boot
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ubuntu@ubuntu:~$ ls /mnt/root
bin   cdrom  etc   initrd.img  lost+found  mnt  proc  sbin  sys  usr  vmlinuz
boot  dev    home  lib         media       opt  root  srv   tmp  var
ubuntu@ubuntu:~$ ls /mnt/root/boot
abi-2.6.27-7-generic         memtest86+.bin
config-2.6.27-7-generic      System.map-2.6.27-7-generic
grub                         vmcoreinfo-2.6.27-7-generic
initrd.img-2.6.27-7-generic  vmlinuz-2.6.27-7-generic
ubuntu@ubuntu:~$ 
```

So it gave me an error when mounting /dev/sda1 (in retrospect I guess because of the "ext3"-option), but the result from the list command looked [as to be expected]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows"), so I proceeded:

```
sudo grub-install --root-directory=/mnt/root /dev/sda
```
Which let to:
```
Due to a bug in xfs_freeze, the following command might produce a segmentation
fault when /mnt/root/boot/grub is not in an XFS filesystem. This error is harmless and
can be ignored.
xfs_freeze: specified file ["/mnt/root/boot/grub"] is not on an XFS filesystem
Installing GRUB to /dev/sda as (hd0)...
Installation finished. No error reported.
This is the contents of the device map /mnt/root/boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)	/dev/sda
```

Finally I ran the Boot_info_script once more. I analyzed it, and it only differed from my previous result (post #7) under "mount output". Don't think this has any importance, but the two final lines which used to read:
```
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
/dev/sdc1 on /media/USB type vfat (rw,nosuid,nodev,uhelper=hal,utf8,shortname=winnt,uid=999)
```
now read:
```
/dev/sdc1 on /media/USB type vfat (rw,nosuid,nodev,uhelper=hal,utf8,shortname=winnt,uid=999)
/dev/sda6 on /mnt/root type ext3 (rw)
```

This is what the entire file looked like:
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Syslinux is installed in the MBR of /dev/sdb
 => No boot loader? is installed in the MBR of /dev/sdc

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

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0cea4b45

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    28,676,024    28,675,962   7 HPFS/NTFS
/dev/sda2          28,676,025   390,716,864   362,040,840   f W95 Ext d (LBA)
/dev/sda5          28,676,088   368,772,074   340,095,987   7 HPFS/NTFS
/dev/sda6         368,772,138   389,688,704    20,916,567  83 Linux
/dev/sda7         389,688,768   390,716,864     1,028,097  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders, total 39102336 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9e369e36

Partition  Boot         Start           End          Size  Id System

/dev/sdb1              16,065    39,102,209    39,086,145   f W95 Ext d (LBA)
/dev/sdb5              16,128    39,102,209    39,086,082   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 8019 MB, 8019509248 bytes
16 heads, 32 sectors/track, 30592 cylinders, total 15663104 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xdfa4a156

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  32    15,663,103    15,663,072   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="1535319E481E6089" LABEL="WinXP" TYPE="ntfs" 
/dev/sda5: UUID="BEDEBE9AE5A88189" LABEL="DATA" TYPE="ntfs" 
/dev/sda6: UUID="54f744e1-80f2-4369-bee9-f89208d0c9d9" TYPE="ext3" 
/dev/sda7: UUID="221a5e9e-84ca-4c8e-ad5e-a47a774760e4" TYPE="swap" 
/dev/sdb5: UUID="6874037F74034F6E" LABEL="BackUp" TYPE="ntfs" 
/dev/sdc1: LABEL="USB" UUID="8E35-50FE" TYPE="vfat" 
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
/dev/sdc1 on /media/USB type vfat (rw,nosuid,nodev,uhelper=hal,utf8,shortname=winnt,uid=999)
/dev/sda6 on /mnt/root type ext3 (rw)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

=========================== sda6/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=54f744e1-80f2-4369-bee9-f89208d0c9d9 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=54f744e1-80f2-4369-bee9-f89208d0c9d9

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
uuid		54f744e1-80f2-4369-bee9-f89208d0c9d9
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=54f744e1-80f2-4369-bee9-f89208d0c9d9 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		54f744e1-80f2-4369-bee9-f89208d0c9d9
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=54f744e1-80f2-4369-bee9-f89208d0c9d9 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		54f744e1-80f2-4369-bee9-f89208d0c9d9
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
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=54f744e1-80f2-4369-bee9-f89208d0c9d9 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=221a5e9e-84ca-4c8e-ad5e-a47a774760e4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 197.5GB: boot/grub/menu.lst
 197.6GB: boot/grub/stage2
 197.5GB: boot/initrd.img-2.6.27-7-generic
 197.6GB: boot/vmlinuz-2.6.27-7-generic
 197.5GB: initrd.img
 197.6GB: vmlinuz


```


I rebooted from my HDD and found myself in the same endless loop as before. Please help me with this if you feel you can. I feel like I'm allmost there. Maybe if I change "ext3" to "ntfs-3g", e.g.:

```
sudo mount -t **ntfs-3g** /dev/sda1 /mnt/root/boot
```

Would this make any difference? By the way: what does "3g" stand for, and should I add this here?

---

### Post by Roob on 2009-03-08
> **T.J. said:**
> The easiest way to boot then is to use EasyBCD (freeware configurator for the Windows Bootloader).

T.J.,

Just found out this isn't possible w/o Vista (or at least its boot loader) installed: [see here]("http://neosmart.net/forums/showthread.php?t=2797"). I have XP...

---

### Post by Roob on 2009-03-09
One other thing I just thought of:

The BIOS of this mainboard lists a LOT of boot-devices. Except for floppy, LS120, CD-rom en LAN there are 6 HDD related options:  HDD-0, HDD-1, HDD-2, HDD-3, SCSI and ATA-100.

The mainboard has 4 IDE connectors: 2 'standard' IDE-0 and -1 (prim., sec.) and two more attached to the Highpoint 370 RAID-controler: IDE-2 and 3. The HDD in question is connected to IDE-2 as master (with the 20 GB drive as slave; no RAID enabled), because the Highpoint controler allows for higher speeds.

So the BIOS is configured to boot from HDD-2. I know for a fact that I can boot from the same disk by choosing 'SCSI' and configure the RAID BIOS as such that the boot flag is set to this device. I don't know about ATA-100, but my guess is that I can boot from the same drive using this option.

Maybe a long shot, but is it possible that choosing another option could solve my problem? (seems unlikely, as I know I boot from the right drive, but still...)

---

### Post by jocheem67 on 2009-03-09
If /dev/sda6 is your xubuntu partition, you can specify it to be the bootpartition..you can do that easily with gparted from the livecd..

Sudo gparted

It'll also give you a good graphical presentation of your drives.
Make it ofcourse the only bootpartition.

If /dev/sda6 is the 4th partition, you have to specify it as sda(0,3) and install grub there...however this is always some tricky advice as it is not easy to do a count when one's not there.

Putting grub on the xubuntupart. has the advantage that you can bypass any windows bootloader, as vista doesn't like other bootloaders.
If needed one can add windows later to /boot/grub/menu.lst

I remember by the way how painful grub can be....looking at your posts you're in that "complicated thinking thingie" that grub can do to anyone.;)

Here's a screenie of my dualboot configuration.

Pretty straightforward.

[http://imgcash6.imageshack.us/img24/9454/91227067.png](http://imgcash6.imageshack.us/img24/9454/91227067.png)

I only use primary partitions, 'cause I find it easier to use regarding the numbers.
As you can see I boot from ubuntu, the xp partition is untouched...

Windows is the first OS installed, grub added it automatically..that's the easy way.

[https://help.ubuntu.com/search.html?cof=FORID%3A9&cx=003883529982892832976%3Ae2vwumte3fq&ie=UTF-8&q=restore+grub&sa=Search](https://help.ubuntu.com/search.html?cof=FORID%3A9&cx=003883529982892832976%3Ae2vwumte3fq&ie=UTF-8&q=restore+grub&sa=Search)

This helped me in the past..

Suc6 to you;)

---

### Post by Roob on 2009-03-09
> **jocheem67 said:**
> 
If /dev/sda6 is the 4th partition, you have to specify it as sda(0,3) and install grub there...however this is always some tricky advice as it is not easy to do a count when one's not there.

"Dank je", Jochem,

for this suggestion. I really like the idea of preserving the Windows boatloader, as this is not my system I'm working on, and my girl friend is going to be really pissed if she's going to be w/o Windows for a couple of days once more. I don't see how it would solve my problem however, because as far as I can see from the Boot Info Script's results-file, everything looked just fine as it was, and the damned thing still wouldn't (dual-)boot. But it's something I didn't try yet, so I will sure give it a shot!

You need to help me out with the code though, as you're dealing with a newby here. Won't this do the job? :
```
sudo mkdir /mnt/root
sudo mount -t ext3 /dev/sda6 /mnt/root
sudo grub-install --root-directory=/mnt/root /dev/sda6
```

By the way:
```
find /boot/grub/stage1
```
in Grub returns (hd0,5). Doesn't this mean I can also install Grub like this?:
```
sudo grub
root (hd0,5)
setup (hd0,5)
quit
```

Really a bit confused here :confused: For one it is confusing to have both "(hdX,Y)" and "sdaZ" used as a syntax to refer to identical partitions by different programs in one and the same OS. And it gets even more confusing to see I have sda1, -2, -5, 6 & 7: where did sda4 and -5 go? (same thing on sdb, my HDD's really don't seem to like numbers 3 and 4 ;) ). I like your partitions better for its simplicity, although I couldn't live w/o a seperate partition for data (docs, pictures, movies, music, email, ...) anymore: it makes reinstalling/messing with an OS so much easier and less riskyer, you should really consider creating one. Guess the first thing I'm going to do once I've got the dual-boot working is to create a seperate /home partition.

---

### Post by jocheem67 on 2009-03-09
Actually that looks okay to me....
You created a mountpoint for your root partition,using the live-cd....that's the 1st command.
Next you put grub on it.That's the second one:

sda(0,5)= sda6 = (x)ubuntu

( where I said it should be (0,3) forget that.)

You may be a newbie, but you don't give up, so that's pretty okay...I had exactly the same troubles when I started using ubuntu, grub can be a pain.
Moreover, when new to linux, one doesn't really know what the commands mean...

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

This is another very helpful page.

---

### Post by Roob on 2009-03-10
Tried to install Grub in the Ubuntu partition in stead of the Windows mbr as described. Now the system just hung after displaying "Verifying DMI poll Data" in stead of rebooting.

One thing I found out is interesting though, to me at least (probably most of you guys realized this after seeing my "fdisk -l"-outcome). In GParted I realized that my Linux- and swap-partitions are part of my extended (Windows) partition. Isn't this scr*wing things up? If so, what's the best and safest way to restore this (would surely like to keep my DATA-partition in tact).

---

### Post by Roob on 2009-03-10
> **Roob said:**
> The BIOS of this mainboard lists a LOT of boot-devices. Except for floppy, LS120, CD-rom en LAN there are 6 HDD related options:  HDD-0, HDD-1, HDD-2, HDD-3, SCSI and ATA-100.

(First time I'm quoting myself, I think and hope) Reinstalled Grub to mbr through LiveCD and rebooted into the same old endless loop. Tried all the HDD related booting options in the BIOS: neither one made any difference. Checked the Highpoint BIOS: boot was set to the right (200 GB) drive.

Also tried booting into Ubuntu through the Super Grub CD in a variaty of ways (better documented [here]("http://www.supergrubdisk.org/forum/index.php?topic=259.0")) but this once resulted in error 17 ("Cannot mount selected partition") and numerous times in error 15 ("File not found").

Edit: One more thing worth noticing perhaps is that when I use the super Grub CD it locates Grub in hda5/sda5/hd(0,4), but Grub in the LiveCD tells me it is installed in sda6/hd(0,5). Has this got to do with the Ubuntu partition being nestled in the extended partition?

---

### Post by meierfra. on 2009-03-10
> Edit: One more thing worth noticing perhaps is that when I use the super Grub CD it locates Grub in hda5/sda5/hd(0,4).

Are you sure?  If yes, that sounds like a bug in the SuperGrub CD. Just for double checking could you post the output of

```
sudo sfdisk -xluS /dev/sda
```

> In GParted I realized that my Linux- and swap-partitions are part of my extended (Windows) partition. Isn't this scr*wing things up? 

Nope, that should not cause any problems.

> Tried to install Grub in the Ubuntu partition in stead of the Windows mbr as described. Now the system just hang after displaying "Verifying DMI poll Data" in stead of rebooting.

A regular Windows MBR is not able to boot a logical partition.   To install an MBR which is able to boot a logical partition, do

```
sudo lilo -M /dev/sda ext
sudo lilo -A /dev/sda 6
```

(depending on your LiveCD you might have to first install "lilo" via "sudo apt-get install lilo" for this to work.)
You can skip the second line of code, if the boot flag is still set to the Ubuntu partition.

---

### Post by jocheem67 on 2009-03-11
The only advice I can give you now is to let go of your current installation....
I know I did when I got in this kind of mess;) when I installed ubuntu being new to the OS..

You can revert back to xp/vista with a "fixmbr" and "fixboot" command from the recovery console on your Windows installation disks..
If you google these commands you'll find the tutorials for these steps.

Ofcourse you can, with help from others then, try other stuff...
However this is not beginners-stuff, so think about it.

I'll keep on checking your adventures though and cincerely hope you can still get to a working configuration.

Cheers.;)

---

### Post by Roob on 2009-03-11
> **meierfra. said:**
> Are you sure [the super Grub CD locates Grub in hda5/sda5/hd(0,4)]?
Yes, I made a "screenshot" of this with my camara, see attachment.

> **meierfra. said:**
> Just for double checking could you post the output of ```
sudo sfdisk -xluS /dev/sda
```
What does this code do? I could try tomorrow when I'm at my friend's place again.

> **meierfra. said:**
> A regular Windows MBR is not able to boot a logical partition.
I followed official Ubuntu documentation listed [here]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") (see paragraph "Preserving Windows Bootloader"). I also followed the advice from jocheem67 to use GParted to set my boot to the Ubuntu partition. The Boot Info Script's Result-file looks okay to me, although I don't understand why it says Syslinux is installed in the mbr in stead of Windows, probably my mistake:

```
============================= Boot Info Summary: ==============================

 => Syslinux is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb
 => No boot loader? is installed in the MBR of /dev/sdc

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

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda6 and 
                       looks at sector 385963874 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #6 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0cea4b45

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    28,676,024    28,675,962   7 HPFS/NTFS
/dev/sda2          28,676,025   390,716,864   362,040,840   f W95 Ext d (LBA)
/dev/sda5          28,676,088   368,772,074   340,095,987   7 HPFS/NTFS
/dev/sda6    *    368,772,138   389,688,704    20,916,567  83 Linux
/dev/sda7         389,688,768   390,716,864     1,028,097  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders, total 39102336 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9e369e36

Partition  Boot         Start           End          Size  Id System

/dev/sdb1              16,065    39,102,209    39,086,145   f W95 Ext d (LBA)
/dev/sdb5              16,128    39,102,209    39,086,082   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 8019 MB, 8019509248 bytes
16 heads, 32 sectors/track, 30592 cylinders, total 15663104 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xdfa4a156

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  32    15,663,103    15,663,072   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="1535319E481E6089" LABEL="WinXP" TYPE="ntfs" 
/dev/sda5: UUID="BEDEBE9AE5A88189" LABEL="DATA" TYPE="ntfs" 
/dev/sda6: UUID="54f744e1-80f2-4369-bee9-f89208d0c9d9" TYPE="ext3" 
/dev/sda7: UUID="221a5e9e-84ca-4c8e-ad5e-a47a774760e4" TYPE="swap" 
/dev/sdb5: UUID="6874037F74034F6E" LABEL="BackUp" TYPE="ntfs" 
/dev/sdc1: LABEL="USB" UUID="8E35-50FE" TYPE="vfat" 
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
/dev/sda6 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sda5 on /media/DATA type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda1 on /media/WinXP type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdc1 on /media/USB type vfat (rw,nosuid,nodev,uhelper=hal,utf8,shortname=winnt,uid=999)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

=========================== sda6/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=54f744e1-80f2-4369-bee9-f89208d0c9d9 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=54f744e1-80f2-4369-bee9-f89208d0c9d9

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
uuid		54f744e1-80f2-4369-bee9-f89208d0c9d9
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=54f744e1-80f2-4369-bee9-f89208d0c9d9 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		54f744e1-80f2-4369-bee9-f89208d0c9d9
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=54f744e1-80f2-4369-bee9-f89208d0c9d9 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		54f744e1-80f2-4369-bee9-f89208d0c9d9
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
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=54f744e1-80f2-4369-bee9-f89208d0c9d9 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=221a5e9e-84ca-4c8e-ad5e-a47a774760e4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 197.5GB: boot/grub/menu.lst
 197.6GB: boot/grub/stage2
 197.5GB: boot/initrd.img-2.6.27-7-generic
 197.6GB: boot/vmlinuz-2.6.27-7-generic
 197.5GB: initrd.img
 197.6GB: vmlinuz
```

One thing worth (?) mentioning: Grub displayed two (non fatal) errors during install:
```
grub> setup (hd0,5)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,5)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,5)"... failed (this is not fatal)
 Running "install /boot/grub/stage1 (hd0,5) /boot/grub/stage2 p /boot/grub/menu
.lst "... succeeded
Done.
```


> **meierfra. said:**
> To install an MBR which is able to boot a logical partition, do
```
sudo lilo -M /dev/sda ext
sudo lilo -A /dev/sda 6
```
You think I have a chance succeeding whit Lilo where Grub failed? 

One more thing: I can lend BootIt NG from a friend. Is this worth a shot? Has anyone got experience with this prog?

Everyone: thanks for posting, thanks for reading!

---

### Post by Roob on 2009-03-11
> **jocheem67 said:**
> The only advice I can give you now is to let go of your current installation....

Are you crazy? No, really, thanks for your concern, but I want to get this dual-boot working. Apart from the 'honour-and-pride-thing' I think the system is really going to benefit from Xubuntu, and that it can last for at least another four or five years for the tasks hat it is used for (email, internet, word-processing, watching movies). My friend hasn't got the money to replace it, so I think I can help her here. Besides I'm *very *curious to see this system performs on Xubuntu.

I'm not afraid of data-loss either. I've put an image of the brand new fine-tuned (and rather lean and fast) XP partition on the 20 GB HDD, and all the data are on a seperate HDD which is disconnected from the mainboard.

Concernig 'reverting back to Windows': I use the Super Grub Disk for this. Do this every time after another (failed) mission to get the dual-boot working. Works like a charm!

Thanks for your support and compassion on my quest, I really appreciate it!

---

### Post by meierfra. on 2009-03-11
> Yes, I made a "screenshot" of this with my camara, see attachment.


That only says that  the grub name for "/dev/sda5" is (hd0,4). It does not say that grub is installed in /dev/sda5.

>  
[QUOTE]Just for double checking could you post the output of
```


sudo sfdisk -xluS /dev/sda
```

What does this code do? I could try tomorrow when I'm at my friend's place again.[/QUOTE]

No more need for this.

> One thing worth (?) mentioning: Grub displayed two (non fatal) errors during install:

That's normal. It always happens when grub is installed to the boot sector of a partition, rather than to the MBR.


> I don't understand why it says Syslinux is installed in the mbr in stead of Windows, 

There are various  different codes which can be used in the MBR to load  the boot sector of the active partition. One of them is the regular Windows code. Syslinux and Lilo use  a different code.  When you tell Supergrub to fix the MBR , it uses the  "syslinux" code.


> You think I have a chance succeeding whith Lilo where Grub failed? 

The actually booting will be done by the Grub.  Lilo will only be installed in the MBR   to  load Grub's stage1, which is installed in the boot sector of the Ubuntu partition. 


> I can lend BootIt NG from a friend. Is this worth a shot?

BootItNG is only a boot manager and not a boot loader. That is, BootItNG will rely on Grub  for  the actual booting. So I don't think BootItNG will help.

---

### Post by Roob on 2009-03-11
> **meierfra. said:**
> That only says that  the grub name for "/dev/sda5" is (hd0,4). It does not say that grub is installed in /dev/sda5.


I got to this screen (of the screenshot) when following the procedure described [here]("http://www.supergrubdisk.org/wiki/SuperGrubDiskProblems"), after choosing "Select your Linux partition" (step 8 of the procedure). Doesn't this at least mean that the SGD thinks that sda5/(hd0,4) contains Linux? Why isn't my 'real' Linux partition (sda6/(hd0,5)) listed? :confused:

---

### Post by meierfra. on 2009-03-11
> Doesn't this at least mean that the SGD thinks that sda5/(hd0,4) contains Linux? Why isn't my 'real' Linux partition (sda6/(hd0,5)) listed?
One would think that sda6 should be listed. Maybe SGD is not able to read the  new 256 bs/inode ext3 filesystem ubuntu is using. But I'm  not familiar enough with SGD  to tell you exactly how to interpret that screen.

---

### Post by jocheem67 on 2009-03-11
Ofcourse I didn't mean to scare you away...persistence is a good thing..

Me? I did have seen a couple of "NTLDR is missing" warnings passing by in the past, after a lot of playing around with my MBR..;)

And that does mean trouble, I can assure you:D

Well, if you make it, I'll drink a nice beer on your behalf.

---

### Post by mcloser on 2009-03-11
[QUOTE=Roob;6878050]Are you crazy? No, really, thanks for your concern, but I want to get this dual-boot working. Apart from the 'honour-and-pride-thing' I think the system is really going to benefit from Xubuntu, and that it can last for at least another four or five years for the tasks hat it is used for (email, internet, word-processing, watching movies). My friend hasn't got the money to replace it, so I think I can help her here. Besides I'm *very *curious to see this system performs on Xubuntu.


Hoi! 

getting kinda crowded with all the wooden heads around here !!  ( I'm a wooden head from Canada ! )

Roob I hate to tell you this but I do agree with jocheem, you really should start fresh with a new install of XP first and then ubu.  myself I have NEVER got Xubu to dual boot !  regular Ubu 8.04 works fine with both XP and Vista, but I can't Xubu to load with anything else on any machine, that's why I'm on this thread.  I've got Xubu loaded very stable on a 6 year old IBM Thinkpad T21 !  but thats the only thing that's on the harddrive.  I recently got a Phenom 9550 system and was drooling to load Xubu on it. ( I like Xubu much more than regular ubu )  but if I wanted to keep the base install of Vista 64 on it, forget it !  I loaded regular 8.04 with no problems and it duals boots with no issues at all, very stable.  but I really want Xubu on it.

so my final advice to you is forget about Xubu until they fix the dual boot issue, load regular ubu on it for a dual boot and spend some time with your girlfriend, if I wasn't in Canada I'd offer to help with the last part...

PS my dad is from Bussum !

---

### Post by Roob on 2009-03-12
> **mcloser said:**
> ...myself I have NEVER got Xubu to dual boot !  regular Ubu 8.04 works fine with both XP and Vista, but I can't Xubu to load with anything else on any machine, that's why I'm on this thread.
That's the first time I hear Xubuntu has booting isues that regular Ubuntu has not, I'm really surprised to hear that, but I take it to be true.

EDIT: By the Way: did you ever come across some (- official -) documentation on this 'Xubooting' issue or other useful links on the internet?  If so, please point me there!

EDIT2: Did you ever try install Ubuntu first, make sure system is dual booting and then [replace the Ubuntu desktop with the Xfce4 desktop]("http://ubuntuforums.org/showthread.php?t=1090621&highlight=xubuntu+boot")?:
```
sudo apt-get install xubuntu-desktop
```
(Check dual boot again) If this works you at least have the Xubuntu desktop back. [Then you can try to remove the Ubuntu packages that were added to a default Xubuntu installation]("http://www.psychocats.net/ubuntu/purexfce")
```

sudo apt-get remove alacarte binfmt-support brltty brltty-x11 capplets-data cdrdao cli-common compiz compiz-core compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-gnome compiz-plugins compiz-wrapper compizconfig-backend-gconf contact-lookup-applet dcraw deskbar-applet ekiga eog evolution evolution-common evolution-data-server evolution-data-server-common evolution-exchange evolution-plugins evolution-webcal example-content f-spot fast-user-switch-applet firefox-3.0-gnome-support firefox-gnome-support gconf-editor gdm-guest-session gedit gedit-common gnome-about gnome-applets gnome-applets-data gnome-control-center gnome-desktop-data gnome-menus gnome-netstatus-applet gnome-nettool gnome-panel gnome-panel-data gnome-pilot gnome-pilot-conduits gnome-session gnome-settings-daemon gnome-spell gnome-terminal gnome-terminal-data gnome-themes gnome-user-guide gnome-utils gstreamer0.10-plugins-base-apps gstreamer0.10-pulseaudio gstreamer0.10-schroedinger gstreamer0.10-tools gvfs-bin gvfs-fuse human-icon-theme human-theme hwtest hwtest-gtk libao2 libart2.0-cil libasound2-plugins libcanberra-gnome libcanberra-gtk-module libcanberra-gtk0 libcanberra0 libcompizconfig0 libdecoration0 libdeskbar-tracker libdirectfb-1.0-0 libebackend1.2-0 libedata-book1.2-2 libedata-cal1.2-6 libedataserverui1.2-8 libeel2-2 libeel2-data libegroupwise1.2-13 libexchange-storage1.2-3 libexempi3 libflickrnet2.1.5-cil libgconf2.0-cil libgdata-google1.2-1 libgdata1.2-1 libgdiplus libgif4 libglade2.0-cil libglib2.0-cil libglitz-glx1 libglitz1 libgmime-2.0-2a libgmime2.2-cil libgnome-keyring1.0-cil libgnome-pilot2 libgnome-vfs2.0-cil libgnome-window-settings1 libgnome2.0-cil libgnomevfs2-bin libgpod-common libgpod3 libgtk2.0-cil libgtkhtml-editor-common libgtkhtml-editor0 libgtkhtml3.14-19 libhyphen0 libicu38 liblpint-bonobo0 libmono-addins-gui0.2-cil libmono-addins0.2-cil libmono-cairo1.0-cil libmono-cairo2.0-cil libmono-corlib1.0-cil libmono-corlib2.0-cil libmono-data-tds1.0-cil libmono-data-tds2.0-cil libmono-i18n1.0-cil libmono-i18n2.0-cil libmono-security1.0-cil libmono-security2.0-cil libmono-sharpzip0.84-cil libmono-sharpzip2.84-cil libmono-sqlite2.0-cil libmono-system-data1.0-cil libmono-system-data2.0-cil libmono-system-web1.0-cil libmono-system-web2.0-cil libmono-system1.0-cil libmono-system2.0-cil libmono0 libmono1.0-cil libmono2.0-cil libmtp8 libndesk-dbus-glib1.0-cil libndesk-dbus1.0-cil libneon27 libopal-2.2 libpisock9 libpisync1 libpt-1.10.10 libpt-1.10.10-plugins-alsa libpt-1.10.10-plugins-v4l libpt-1.10.10-plugins-v4l2 libpulsecore5 libsamplerate0 libschroedinger-1.0-0 libsdl1.2debian libsdl1.2debian-alsa libsgutils1 libspeexdsp1 libsqlite0 libtracker-gtk0 libts-0.0-0 libwps-0.1-1 libx11-xcb1 mesa-utils metacity mono-common mono-gac mono-jit mono-runtime mousetweaks mtools nautilus nautilus-cd-burner nautilus-data nautilus-sendto nautilus-share openoffice.org-base-core openoffice.org-calc openoffice.org-common openoffice.org-core openoffice.org-draw openoffice.org-emailmerge openoffice.org-gnome openoffice.org-gtk openoffice.org-impress openoffice.org-math openoffice.org-style-human openoffice.org-writer pkg-config pulseaudio pulseaudio-esound-compat pulseaudio-module-gconf pulseaudio-module-hal pulseaudio-module-x11 python-beagle python-gmenu python-gtksourceview2 python-uno rarian-compat rdesktop rhythmbox screen-resolution-extra sg3-utils sqlite sqlite3 syslinux tangerine-icon-theme tomboy tracker tracker-search-tool tracker-utils tsclient ubuntu-artwork ubuntu-desktop ubuntu-docs ubuntu-gdm-themes ubuntu-system-service ubuntu-wallpapers untex usb-creator usplash-theme-ubuntu vino whois wv xdg-user-dirs xdg-user-dirs-gtk xulrunner-1.9-gnome-support && sudo apt-get install xubuntu-desktop
```

If I understand correctly now you are effectively running Xubuntu. Additional benefit of this approach is that you can locate the problem. If you start with an Ubuntu/Windows working dual boot, and you end up with Xubuntu not dual booting, you can start over and execute the code in step2 in smaller truncs until system no longer dual-boots. Might try this myself. /EDIT2


Guess I'll delete the Xubuntu partition then, ... and stubbornly try installing one more time in the unpartioned space (pointing to SCSI in the BIOS as the HDD to boot from, as this makes the most sense to me). If it works: great! If not, I'll remove it and install regular Ubuntu (8.04 or 8.10). Then we'll just have to wait for a Xubuntu version that hasn't got these problems. In the meantime my friend can get familiar with Ubuntu. If she really likes it, we might 'even' decide to ditch Windows and install (X)Ubuntu as only OS.

> **mcloser said:**
> PS my dad is from Bussum ! That's a very nice part of the Netherlands! (I 'get' the move to Canada though).

---

### Post by meierfra. on 2009-03-12
> Guess I'll delete the Xubuntu partition then,
Please don't.  I'm pretty sure that reinstalling won't accomplish anything. Also your problem occurs before grub tries to load the kernel. So it has nothing to do with Ubuntu/Xubuntu. 

Did you try installing Lilo to the MBR yet?  Even if that does not work, there are a couple of more things one can try. So don't give up yet.

---

### Post by Roob on 2009-03-12
> **meierfra. said:**
> Please don't.  I'm pretty sure that reinstalling won't accomplish anything. Also your problem occurs before grub tries to load the kernel. So it has nothing to do with Ubuntu/Xubuntu.
I already did uninstall. You're right there's probably nothing wrong with the kernel, but couldn't there be something wrong with the Grub-version packaged with the installer? Anyway, reinstallation was a snap and gave me a chance to manually partition the drive, so I made a seperate /home-partition, which will be nice once I've got things working ;)

After reinstallation same endless boot-loop. Tried all the HDD boot-options in the BIOS once more. Then I tried installing Ubuntu 8.10, but the CD contained (I/O-)errors. I'm downing Ubuntu 8.04 right now, so maybe I will try that later (have to burn this at home anyway).

> **meierfra. said:**
> Did you try installing Lilo to the MBR yet?  Even if that does not work, there are a couple of more things one can try. So don't give up yet.
I'm going to do that right now in my brand-new Ubuntu install. And then I'll run Boot Info Script once more.

I'll report right back. Thanks for bearing with me!!

---

### Post by meierfra. on 2009-03-12
> I'm going to do that right now in my brand-new Ubuntu install


Just remember that grub has to be installed to the Ubuntu partition for this to work: 

sudo grub
root (hd0,5)
setup (hd0,5)
quit

(but the numbers  might have to be changed, use "find /boot/grub/menu.lst" to get the correct numbers)

---

### Post by Roob on 2009-03-12
> **meierfra. said:**
> Did you try installing Lilo to the MBR yet?  Even if that does not work, there are a couple of more things one can try. So don't give up yet.

I did (although I did quite a detour. I also installed Grub in sda6 - which is still my Ubuntu-partition. I can elaborate on the detour I did (documented every step I took) 'though I'm quite sure that I didn't mess things up). 

In short: after installing Grub to sda6 and Lilo to the mbr, and the boot set to sda6 I got this (in DOS - or whatever):
```
disk read eror
disk read error
Starting...

Microsoft (R) Windows Millenium
   (C)Copyright Microsoft Corp.

A:\>
```

I also tried to set the boot to sda1, but then Windows was booted.

This is how my HDD looks now:
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0cea4b45

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1785    14337981    7  HPFS/NTFS
/dev/sda2            1786       24321   181020420    f  W95 Ext'd (LBA)
/dev/sda5            1786       22955   170047993+   7  HPFS/NTFS
/dev/sda6   *       22956       23684     5855661   83  Linux
/dev/sda7           23685       24170     3903763+  83  Linux
/dev/sda8           24171       24321     1212876   82  Linux swap / Solaris

Disk /dev/sdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9e369e36

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2        2434    19543072+   f  W95 Ext'd (LBA)
/dev/sdb5               2        2434    19543041    7  HPFS/NTFS

Disk /dev/sdc: 8019 MB, 8019509248 bytes
16 heads, 32 sectors/track, 30592 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0xdfa4a156

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       30592     7831536    b  W95 FAT32
```
(sda6 is my Xubuntu root-partition, sda7 my /home partition, the only thing new here)

And these are the results from the Boot Info Script:
```
============================= Boot Info Summary: ==============================

 => Lilo is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb
 => No boot loader? is installed in the MBR of /dev/sdc

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

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda6 and 
                       looks at sector 371491882 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #6 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0cea4b45

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    28,676,024    28,675,962   7 HPFS/NTFS
/dev/sda2          28,676,025   390,716,864   362,040,840   f W95 Ext d (LBA)
/dev/sda5          28,676,088   368,772,074   340,095,987   7 HPFS/NTFS
/dev/sda6    *    368,772,138   380,483,459    11,711,322  83 Linux
/dev/sda7         380,483,523   388,291,049     7,807,527  83 Linux
/dev/sda8         388,291,113   390,716,864     2,425,752  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders, total 39102336 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9e369e36

Partition  Boot         Start           End          Size  Id System

/dev/sdb1              16,065    39,102,209    39,086,145   f W95 Ext d (LBA)
/dev/sdb5              16,128    39,102,209    39,086,082   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 8019 MB, 8019509248 bytes
16 heads, 32 sectors/track, 30592 cylinders, total 15663104 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xdfa4a156

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  32    15,663,103    15,663,072   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="1535319E481E6089" LABEL="WinXP" TYPE="ntfs" 
/dev/sda5: UUID="BEDEBE9AE5A88189" LABEL="DATA" TYPE="ntfs" 
/dev/sda6: UUID="c9be0f67-497e-441e-9bbd-4396050f79ca" TYPE="ext3" 
/dev/sda7: UUID="c0f24e3c-b7f4-4634-8b7d-4dbf348fb272" TYPE="ext3" 
/dev/sda8: UUID="65423637-6ef2-4816-9da1-d5a9617cb33a" TYPE="swap" 
/dev/sdb5: UUID="6874037F74034F6E" LABEL="BackUp" TYPE="ntfs" 
/dev/sdc1: LABEL="USB" UUID="8E35-50FE" TYPE="vfat" 
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
/dev/sda7 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sda6 on /media/disk-1 type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sda5 on /media/DATA type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda1 on /media/WinXP type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdc1 on /media/USB type vfat (rw,nosuid,nodev,uhelper=hal,utf8,shortname=winnt,uid=999)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

=========================== sda6/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=c9be0f67-497e-441e-9bbd-4396050f79ca ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=c9be0f67-497e-441e-9bbd-4396050f79ca

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
uuid		c9be0f67-497e-441e-9bbd-4396050f79ca
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=c9be0f67-497e-441e-9bbd-4396050f79ca ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		c9be0f67-497e-441e-9bbd-4396050f79ca
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=c9be0f67-497e-441e-9bbd-4396050f79ca ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		c9be0f67-497e-441e-9bbd-4396050f79ca
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
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=c9be0f67-497e-441e-9bbd-4396050f79ca /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=c0f24e3c-b7f4-4634-8b7d-4dbf348fb272 /home           ext3    relatime        0       2
# /dev/sdb5
UUID=6874037F74034F6E /media/Backup   ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=BEDEBE9AE5A88189 /media/Data     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda1
UUID=1535319E481E6089 /media/WinXP    ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda8
UUID=65423637-6ef2-4816-9da1-d5a9617cb33a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 190.2GB: boot/grub/menu.lst
 190.2GB: boot/grub/stage2
 190.2GB: boot/initrd.img-2.6.27-7-generic
 190.2GB: boot/vmlinuz-2.6.27-7-generic
 190.2GB: initrd.img
 190.2GB: vmlinuz
```

---

### Post by meierfra. on 2009-03-12
Strange. Everything seems to be set up correctly. 

Lets see what happens if you add  Ubuntu to the Windows  boot loader:
Boot from the live CD and open a terminal.

```

sudo lilo -A /dev/sda 1
sudo mount /dev/sda1 /mnt
cd /mnt
sudo dd if=/dev/sda6 of=ubuntu.bin count=1
sudo nano boot.ini
```

Add  this line to the end of the file.

C:\ubuntu.bin="Ubuntu"

Save  the file and exit nano with "Ctr+O" "Enter" "Ctr+X"

(Be very careful with the "dd" command. If used incorrectly it can wipe a whole hard drive.  If "dd" runs for more  than a couple of second,  use "Ctr+C" to kill the process.)

Reboot and choose "Ubuntu" at the Windows Boot Menu.

---

### Post by meierfra. on 2009-03-12
I just fixed a typo in my previous post. (It said  "sudo lilo -A sda 1", but it needs to be "sudo lilo -A /dev/sda 1")

---

### Post by Roob on 2009-03-12
> **meierfra. said:**
> Strange. Everything seems to be set up correctly. 

Lets see what happens if you add  Ubuntu to the Windows  boot loader:
Boot from the live CD and open a terminal.

```

sudo lilo -A /dev/sda 1
sudo mount /dev/sda1 /mnt
cd /mnt
sudo dd if=/dev/sda6 of=ubuntu.bin count=1
sudo nano boot.ini
```

Add  this line to the end of the file.

C:\ubuntu.bin="Ubuntu"

Now we 're getting somewhere! On reboot this brought me into a boot menu(!) listing WinXP and Ubuntu. When choosing "WinXP" system booted into XP allright, when choosing "Ubuntu" system (edit:) brought me to the Grub prompt.

I just rebooted into the LiveCD to play with the boot-flags, but I figure you're going to provide me with some more code to solve this thing (?). (just very exited for having seen a boot-menu)

Edit: originally there was a boot flag at both sda1 and -6. I left it like this and rebooted. This brought me to the boot menu. I rebooted into the LiveCD and set the boot flag (in GParted) to sda6 only. After reboot system hung. Rebooted into LiveCD and set the flag to sda1 (only). As to be expected this brought me to the boot menu again, where (edit:)system brought me to the Grub-prompt again and WinXP to WinXP.

(BTW: why is the reolution so ridiculously high when I boot into the liveCD - who's idea was this - and how do I change this?)

---

### Post by meierfra. on 2009-03-12
> boot menu(!) listing WinXP and Ubuntu. 

Well, that is only the  Windows Boot Menu. So we did not really make any progress.  


Are you able  to type  at the grub prompt (the screen which appears after selecting Ubuntu at the Windows Boot Menu)?  If yes, what is the output of

```
geometry (hd0)

find /boot/grub/stage2

find /boot/grub/menu.lst
```

---

### Post by Roob on 2009-03-13
Sorry - fell asleep last night.. too much wine \\:D/

> **meierfra. said:**
> Are you able  to type  at the grub prompt 

The only thing I can 'type' here is Ctrl-Alt-Delete unfortunately.

EDIT1: I also tried setting "USB Keyboard Support via BIOS" (in stead off OS). Still couldn't type at the prompt.

EDIT2: I once more tried all the HDD-related boot options in the BIOS (HDD-0 through -3, ATA-100, SCSI). Every option brought me to the boot menu. I don't get this; shouldn't most of this options lead to "Hard Disk not Found" or "Unable to boot from HD" or something like that? Has this got something to do with "Boot other Device", which is set to enabled?

---

### Post by meierfra. on 2009-03-13
Well, I'm starting  run out of ideas. By now it looks like a bios problem to me.  You said you already tried out all the different settings in the bios. But I suggest to have another look. Maybe you missed something.  You might also consider a bios update.
 
Or you could see what happens if you install Xubuntu on a primary partition instead of a logical partition.  In 99.99 percent of all cases this makes no difference, but I have seen exactly two cases where a booting problem was solved by using  a primary partition instead of a logical.  And given the strange error messages  you are getting, this might be worth a try.

---

### Post by Roob on 2009-03-13
> **meierfra. said:**
> Well, I'm starting  run out of ideas. By now it looks like a bios problem to me.  You said you already tried out all the different settings in the bios. But I suggest to have another look. Maybe you missed something.  You might also consider a bios update.
I was already re-checking the BIOS settings while you were writing this: see the edits I made in my previous post.

I was quite sure I had the latest BIOS installed, but your post made me recheck that as well. And I found a BIOS-mod that looks interesting. Quote from the readme:
```
Bios.bin is based on latest Abit bios for BX133-Raid 12/03/2001-i440BX-W977-6A69KA1CC-72 
[-> This is the BIOS I have installed]
and moded by RayeR
[cut]
-[B]updated bios for RAID HPT370 to version 2.351 witch support drivers over 128G (48bit
 addressing)[/B] and shorten the timeout for drive detection from 8 sec to 1 sec ;)
```
I thought the HPT370-controler didn't have problems addressing HDD's over 128 GB - I thought this only aplied to the IDE1 and -2 controlers (The Highpoint BIOS correctly displayes HD size as 200 GB).

So this looks interesting. I'll be flashing the BIOS next time I'm working on this system - probably next tuesday. Unfortunately have to go earn some money now..
 
> **meierfra. said:**
> Or you could see what happens if you install Xubuntu on a primary partition instead of a logical partition.  In 99.99 percent of all cases this makes no difference, but I have seen exactly two cases where a booting problem was solved by using  a primary partition instead of a logical.  And given the strange error messages  you are getting, this might be worth a try.
Tried to do this during my last install, while manualy partitioning. I was able to make a primary root and /home-partition, but then I couldn't use the remaining free space anymore (options greyed out, don't remember what it said, something like unusable free space), which was meant to be my SWAP-partition. So I started partitioning again, choosing for Logical partitions.

---

### Post by HoodedCookie--&gt; on 2009-03-13
Have you tried any other programs for dualbooting? I use VirtualBox. It's an open source very easy-to-use program. 

DOWNLOAD:
[http://www.virtualbox.org/](http://www.virtualbox.org/)

---

### Post by meierfra. on 2009-03-13
> I thought the HPT370-controler didn't have problems addressing HDD's over 128 GB - I thought this only aplied to the IDE1 and -2 controlers (The Highpoint BIOS correctly displayes HD size as 200 GB).

So this looks interesting

I agree, sounds promising.  A size limit never crossed my mind, since that usually gives Grub error 18. 


>  I was able to make a primary root and /home-partition, but then I couldn't use the remaining free space anymore (options greyed out, don't remember what it said, something like unusable free space), which was meant to be my SWAP-partition.

You need to put the logcial  swap partition immediately after  the logical NTFS partition. (The logical partitions need to be consecutive)  

Or you could make a  primary /boot partition (200MB) at the beginning of the hard drive  and then  logical root, /home  and swap partitions. That would avoid any size limit caused by  Bios.

---

### Post by Roob on 2009-03-14
Sigh... This BX133 doesn't give in without a fight. Some character, really doesn't seem to keen on letting me install Linux into her.

So I flashed the BIOS, adjusted the settings carefully (I can post them later when I've written them down and analysed them - took some pictures). Rebooted into LiveCD, reinstalled Grub, rebooted... into the Grub loading stage1.5-loop. 

So I really thought the new BIOS hadn't done anything, but fortunately this isn't completely true:

I rebooted into GrubCD and tried to boot into Xubuntu from there, and this option brought me to the menu I'm so desperate to find when booting from my HDD. But both ubuntu-kernels and the memtest option returned error 13 (Invalid or Unsupported executable format). Only XP booted.

I then rebooted into the SGD once more and tried the procedure described [here]("http://www.supergrubdisk.org/wiki/SuperGrubDiskProblems"). It now brought me to a menu with all my partitions listed, see attached "partitions in SGD.jpg". With the old BIOS I only saw the first two partitions (that started under the old 126 GB-limit), I posted [that screenshot]("http://ubuntuforums.org/attachment.php?attachmentid=106115&d=1236796618") in #21 of this thread. So I tried to install Grub like so, rebooted, ... into my friend the loop.

I rebooted into LiveCD, checked how my HDD looks like, and it looks as promising and okay as ever. I'm giving up for today. Bit disapointed with this, I really felt good about this in advance, the more I thought it through the better: everything seemed to fit. Well: step-by-step. Goodnight, and thanks for reading!

Edit: PS: also disabled "boot from other device". Still the PC doesn't mind which HDD I chose to boot from - result is always the same. This really irritates me. Looks like when a HDD is chosen as boot-device, the system boots from whatever drive has been given the boot-flag in the Highpoint-BIOS.

---

### Post by meierfra. on 2009-03-14
Sounds like you made some  real progress with your Bios.  But this also means that you  have to try out all the different ways to install grub again. 


>  I flashed the BIOS, adjusted the settings carefully (I can post them later when I've written them down and analysed them - took some pictures). Rebooted into LiveCD, reinstalled Grub, rebooted... into the Grub loading stage1.5-loop.

How did you reinstall Grub? Did you try booting after you flashed the bios and before you reinstall grub?
Did you try booting from the Ubuntu item on your Windows Boot Menu?

I suggest installing grub to the MBR of /dev/sda (but maybe you already did that):


```
sudo grub
root (hd0,5)
setup (hd0)
quit 
```

> I rebooted into GrubCD and tried to boot into Xubuntu from there, and this option brought me to the menu I'm so desperate to find when booting from my HDD. But both ubuntu-kernels and the memtest option returned error 13

Getting Error 13  trying to  boot Ubuntu is pretty strange. Maybe it is caused by the fact that SuperGrub  currently does not understand the "uuid" line in menu.lst. So see what happens if you replace

uuid		c9be0f67-497e-441e-9bbd-4396050f79ca

in menu.lst  by

root (hd0,5).

---

### Post by Roob on 2009-03-15
Hi all,

You're not going to believe this, but I'm writing this from Xubuntu - and not from the LiveCD! 

I booted from the SGD one more time, and followed [the same procedure]("http://www.supergrubdisk.org/wiki/SuperGrubDiskProblems") I tried yesterday. Rebooted and... Voilá, it brought me to the boot menu.

Don't know why it works now and didn't work yesterday. I think I changed the boot-disk in the BIOS to HDD-0 (in stead of SCSI). But I also might have messed up yesterday, by changing more than one thing at a time. Anyway, I ran the Boot_Info_Script again and I will analyze the results, and compare them with yesterday's results, and I'll post my findings here.

- First time I booted into Xubuntu, I got the funny high-res screen, with three desktops horizontally compressed, see attached jpg. System froze, couldn't do anything
- Then I tried recovery console, lot of errors, see screen shots. Didn't try to fix anything
- Booted into normal Xubuntu again, same funny screen, tried to change resolution (system now didn't freeze), but couldn't find the monitor settings
- Booted into the liveCD, to see where to change resolution
- Booted intu Xubuntu on HD again. Now everything was just fine from the start (w/o me changing anything)!

One thing: I would like to change the boot order (Windows first - at least untill I got Xubuntu fine-tuned).

When I try to run
```
gksudo gedit /boot/grub/menu.lst
```
from the LiveCD, the console takes a while, then just returns the prompt w/o anything happening. When I try it in the HD-installation I get this:
```
gksudo gedit /boot/grub/menu.lst

(gksudo:5376): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
solletti@DeJonkies-desktop:~$ 
```
What's happening?

> **meierfra. said:**
> 
How did you reinstall Grub? Did you try booting after you flashed the bios and before you reinstall grub?
Did you try booting from the Ubuntu item on your Windows Boot Menu?

I suggest installing grub to the MBR of /dev/sda (but maybe you already did that):


```
sudo grub
root (hd0,5)
setup (hd0)
quit 
```

This was exactly what I did yesterday.

I'm a happy guy right now. Thank you so much for your technical and moral support!

EDIT: One other thing I would like to fix as soon as possible is this: in Ubuntu screen position is shifted to the right. I could compensate for this in the menu of my monitor, but then screen position in XP would be shifted to the left. Is there a way to change screen position in Xubuntu w/o touching monitor buttons?

---

### Post by meierfra. on 2009-03-15
Just to make sure. You are now able  to  directly boot  into xubuntu (or to you have  to use SGD)?

> gksudo gedit /boot/grub/menu.lst

(gksudo:5376): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

Did you install "gedit"?  Xubuntu use "mousepad" as the default editor

---

### Post by Roob on 2009-03-15
> **meierfra. said:**
> Just to make sure. You are now able  to  directly boot  into xubuntu (or to you have  to use SGD)?
Yes, I can boot directly! (I don't have to use SGD).

> **meierfra. said:**
> Did you install "gedit"?  Xubuntu use "mousepad" as the default editorI didn't.

EDIT: I tried "gksudo notepad /boot/grub/menu.lst" but this returned the same result as before. Then I tried installing gedit, entered the same password as during install (99,95% sure), but it kept saying wrong password.

---

### Post by meierfra. on 2009-03-15
It's "mousepad"  (and  not "notepad")

---

### Post by Roob on 2009-03-15
> **meierfra. said:**
> It's "mousepad"  (and  not "notepad")

:oops: I'll try again (I'm in WinXP now, so can't do it directly)

By the way: got the screen position thing solved. Both screens are fine in XP and Xubuntu (just used monitor buttons).

Tried rebooting in Xubuntu, to install gedit. Still system won't accept password (tried typing caps as well, allthough I'm quite sure didnt use them). This really is a problem. Does this mean I have to reinstall?

---

### Post by Roob on 2009-03-15
> **Roob said:**
> :oops: I'll try again (I'm in WinXP now, so can't do it directly)

Tried again, but now system asks for my password - which it still won't accept. I'll be giving up for today, made some progress ;) How can I resolve this password-thing? Re-install? And then there are all the errors displayed in the recovery console. Should I all fix them manually?

---

### Post by meierfra. on 2009-03-15
> And then there are all the errors displayed in the recovery console. Should I all fix them manually? 

I suggest a file system check. Boot from the live cd

```
sudo umount /dev/sda6
sudo e2fsck -fpv /dev/sda6 
```

(the "p" makes sure that "e2fsck" won't asked you too many questions)

(you can also use "e2fsck -fyv /dev/sda6". Then e2fsck automatically answers all the questions with "yes")


> How can I resolve this password-thing? Re-install?
Do you have to type your password when you login ? Or did you choose automatic login?

You can change your password by booting into recovery mode and type

```
passwd <your_username>
```

and type in your password twice (you won't  be asked for your  old password)

---

### Post by Roob on 2009-03-15
> **meierfra. said:**
> I suggest a file system check. Boot from the live cd
```
sudo umount /dev/sda6
sudo e2fsck -fpv /dev/sda6 
```
I did this, and everyting looked allright, but suddenly it stopped, w/o returning a prompt. I gave it some more time... nothing. I noticed I could type in the console, and I quit (maybe I didn't give it enough time). Anyway, I booted into the recovery mode again, and ran the system check from the menu. A lot of errors were displayed, I wounded up leaving my finger on the "Y"-key. Looked like an eternity untill all the errors were fixed.

Anyway, when I boot into Xubuntu ("normal" mode) I get two error messages (these were there from the start):
1. "Install problem!  The configuration defaults for GNOME [? Why Gnome, I have Xubuntu] power manager have not been installed correctly. Please contact ..."
2. I always get "Enter password for default keyring to unlock" at start up. After entering  password I get "The network manager applet could not find some required resources. It cannot continue"

> **meierfra. said:**
> 
You can change your password by booting into recovery mode and type
```
passwd <your_username>
```
This worked! I have now changed order of OS-es in menu.lst.

I really owe you big-time, Meierfra, thank you so much! Maybe I should mark this thread as solved, and start new threads for the problems I'm confronted with now?

---

### Post by meierfra. on 2009-03-15
> I really owe you big-time, Meierfra, thank you so much!

You are welcome. Glad to be of help.

> Maybe I should mark this thread as solved, and start new threads for the problems I'm confronted with now? 

Good idea. I  don't know anything about  those  two  problems. A new thread with a new title  will give you a better change to find some help.

---

### Post by meierfra. on 2009-03-15
> I don't know anything about those two problems.

Well, you might try reinstalling the "gnome-power-manager"

```
sudo apt-get purge gnome-power-manager
sudo apt-get install gnome-power-manager 
```

If that does not help, start a new thread.

---

### Post by Roob on 2009-03-15
Sounds like an okay idea, I'll try it next tuesday, enough for today.

Tried to mark the thread as solved, but I didn't find the option. I edited the title of the first message in this thread (I added "[solved]"), but this doesn't affect later messages.

To anyone who is reading this thread because (s)he has a problem simular to mine: problem here was caused essentially because the BIOS of my mainboard (year 2000/2001) wasn't able to address drives over 128 GB. And it could be solved by flashing the BIOS. I was lucky to find a BIOS mod (from 2005!) which addressed the problem. Another viable solution would have been to partition the drive in a way that the Ubuntu partition would have come directly after the WinXP partition (start of the partition < 128 GB). (Other/older BIOSsen can have a lower limit of GBytes that can be addressed: 8,4 GB for older Intel CPU-boards, don't know about AMD chipsets).

Once again: thanks everyone! Guess I'll read more of you in the future (next project: blow some live into parents' PC, another old beast). ):P

---

### Post by munishvit on 2009-03-15
Sorry to mix-up my problem with this thread, but I too have problem with dual-boot and I want to install Windows XP on non-first primary partition. Please Check
[http://ubuntuforums.org/showthread.php?t=1095893](http://ubuntuforums.org/showthread.php?t=1095893)
aaanny help would be great. Thanks :D

---

### Post by Roob on 2009-03-19
_Epilogue_

Installation gave so many errors that I decided to reinstall once more. I left BIOS settings untouched (of course), booted from the LiveCD and chose install with manual partitioning. I made sure I formatted the root and the /home directory (the latter was probably not necessary), as to be sure to wipe out everything from previous install.

- I rebooted from HD -> endless "stage1.5-loop" again.
- I rebooted into LiveCD. Installed Grub manually:
```
sudo grub
root (hd0,5)
setup (hd0)
quit
```
and rebooted from HD -> endless "stage1.5-loop"
- I tried changing my boot-HDD w/o succes

> **Roob said:**
> Hi all,
Don't know why it works now and didn't work yesterday. I think [because] Ichanged the boot-disk in the BIOS to HDD-0 (in stead of SCSI).
I was wrong there!

So I followed this SKG-procedure once more: ["Super Grub Disk hangs when embeding stage1_5"]("http://www.supergrubdisk.org/wiki/SuperGrubDiskProblems"), and I found the dual-boot was restored once more.

(In fact, the first time I tried, it didn't work. So I retried, and I realized that I probably hadn't followed the entire procedure the first time (you really have to go through a LOT of screens, many of them very simular); after selecting the partition containing the Linux kernel, you have to select the drive where you want to write to (mbr), and I think I skipped this crucial final step. In retrospect I'm quite sure that this was exactly what happened after the first install with the new BIOS ([this post]("http://ubuntuforums.org/showpost.php?p=6897621&postcount=45"))).

Then I booted into my fresh Xubuntu-install. No errors this time! Everything worked just fine right from the start. I updated the OS, language pack, installed some additional software (mediaplayers, codecs, few games) and configured Firefox and Thunderbird (using the profilemanager to point to existing WinXP profiles); everything worked just great! (Just no sound yet, but I guess I'll figure that out w/o to much trouble). 

This 1 GHz PIII-system really runs nice on Xubu, very responsive. I love the Synaptic Package manager, the concept of the Software repositories and the fact that you don't log in as root. All very safe, transparent and convenient: (Once installed...) I think this is a great OS for PC-illiterates like my friend and my parents. (I'm also considering throwing in the option of installing (Edu-/X-/-)Ubuntu in the school PC's in the next "parents meeting" at my daughter's school: PC's in her class-room sure look outdated, don't know what's installed right now; I would be happy to oblige).

-----

After reinstall I ran the Boot_Info_Script at three points in time:
- Directly after the reinstall: Results_1.txt
- After installing Grub via the LiveCD: Results_2.txt
- After installing Grub via the SGD: Results_3.txt

I looked up the differences in the first paragraph and the "sda6"-section (there were much more differences between the Results-files, especially in the "mount output"-section; no differences in menu.lst):

```
First paragraph:
Results_1:
 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.

Results_2:
 => Grub0.97 is installed in the MBR of /dev/sda and looks at sector 371491882 
    of the same hard drive for the stage2 file. A stage2 file is at this 
    location on /dev/sda. Stage2 looks on partition #6 for /boot/grub/menu.lst.

Results_3
 => Grub0.97 is installed in the MBR of /dev/sda and looks at sector 372909754 
    of the same hard drive for the stage2 file. A stage2 file is at this 
    location on /dev/sda. Stage2 looks on partition #6 for /boot/grub/menu.lst.
    [sector numbers are not the same, but I guess that the SGD wrote the stage2
    file to a different sector, so the listed sector number in Results_2 was
    probably correct at the time]


"sda6":
Results_1:
    File system:       ext3   
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

Results_2:
    File system:       ext3    
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda6 and 
                       looks at sector 371491882 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #6 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

Results_3:
    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab
```

Hard for me to tell what was wrong with the original boot config and with the one after manually installing Grub. Maybe one of you booting-experts see something of interest. On the other hand: I've got the feeling there's something funny with this mainboard, so I guess there is not much sense in over-analyzing things. I planned to post all three Results-files, but I accidently overwrote the 2nd one while comparing differences in MS Word, so I attached only Results-files 1 and 3 to this post for those who are interested.

-----

I think the most valuable lesson learned from the entire exercise described in this thread is that when you can't get an older system to dual boot, you should check whether the BIOS of your mainboard is able to address the entire hard disk. (Even if your BIOS lists the size of your hard disk correctly, this isn't necessarily the case!). If you install Linux beyond the BIOS's reach, your system will reboot into an endless loop (or maybe hang?). 

It's easy to check whether this is the case by checking your partitions using the Super Grub Disk (SGD), f.i. by following the procedure described [here]("http://www.supergrubdisk.org/wiki/SuperGrubDiskProblems"). The SGD relies on the BIOS for addressing your HDD's, so if it doesn't list all the partitions, you probably have a BIOS problem. If that is the case you can try updating your BIOS to one that's able to address your entire hard disk. I was so lucky to stumble upon a BIOS update (an unofficial mod) that did just that. In most cases though this won't be an option. In these cases there are two work-arounds:

- Install Linux within the addressing range of the BIOS, f.i. directly after your Windows (or other-OS) partition, by manual partitioning;
- Install Linux on a different HD in the first partition.
(Or as 3rd option, of course, dump Windows and install Linux in its place :) )

When I've got some spare time I'll make a 'sticky-proposal' out of this, or add it to an appropiate existing sticky. For now I'm going to fine-tune the Xubuntu install: want to hear some sound! Thanks for reading.

---

### Post by meierfra. on 2009-03-19
There are some inconsistency between the way you describe your course of action and the excerpts from RESULTS 1-3.

 [LIST=1]
[*]It looks like you used  "Super Grub Disk hangs when embedding stage1_5"    in between RESULTS1 and RESULTS2. 
[*]  It looks like you installed Grub to the boot sector of the Ubuntu partition  in between RESULTS1 and RESULTS2,  either with SuperGrub or via run "sudo grub, root (hd0,5), setup (hd0,5)". 
[*] It looks like you reinstalled  Xubuntu in between RESULTS2 and RESULTS3.
[/list]
Could any of this  be  true?  Or did you mix up the RESULTS  file? Could  RESULTS2 be left over from the time before you reinstalled Xubuntu

Anyway, here is my

[SIZE="4"][COLOR="Red"]Epilogue[/COLOR][/SIZE]

You have been dealing with two  problems:

[LIST]
[*]I) Grub does not work when the stage1.5 files  are used.

[*]II)  Your bios (before you flashed them) were not able to see the whole hard drive.
[/LIST]

Problem I) is fairly uncommon. I think its caused by some kind of bug in Grub which is only triggered by very few bios.

Problem I)  can be cured by   installing Grub  without the stage1.5 files. There are two methods to do this:
 [LIST]
[*]A)  Use  "Super Grub Disk hangs when embeding stage1_5"  (or use the "install" command in the grub shell, but the latter was never tried)
[*]    B) Install  Grub to the boot sector of the Ubuntu partition.
[/LIST]
You tried both these methods, but they failed. Maybe you did not carry  out  the  instruction correctly,  but it seems more likely  to me that  they failed because of Problem II)


Problem II) is somewhat more common.  Depending on the circumstances it can be cured by on of the following methods:
[LIST]
[*]C)  Flash the Bios.
[*]     D)  Create a separate boot partition at the beginning of the hard drive.
[*]     E)  Convert a logical partition to a primary partition (or vice versa)[/LIST]

You tried flashing the Bios, and it worked. Once Problem II) was solved , you were able to fix Problem I via method A).

---

### Post by Roob on 2009-03-20
> **meierfra. said:**
> There are some inconsistency between the way you describe your course of action and the excerpts from RESULTS 1-3.

 [LIST=1]
[*]It looks like you used  "Super Grub Disk hangs when embedding stage1_5"    in between RESULTS1 and RESULTS2. 
[*]  It looks like you installed Grub to the boot sector of the Ubuntu partition  in between RESULTS1 and RESULTS2,  either with SuperGrub or via run "sudo grub, root (hd0,5), setup (hd0,5)". 
[*] It looks like you reinstalled  Xubuntu in between RESULTS2 and RESULTS3.
[/list]
Could any of this  be  true?  Or did you mix up the RESULTS  file? Could  RESULTS2 be left over from the time before you reinstalled Xubuntu

Your findings surprise me.

I'm sure my description of (...the order of...) events in the post you refer to was accurate. I'm also sure I didn't make any mistakes in the original naming of the results-files (1, 2 & 3).

What happened next is that I analyzed the files at home. On my PC at home I have only Win XP installed (as of yet), and when I open the Linux text files the line breaks get replaced by little squares. So what I do is open the files in Word, which displays the files just fine, and choose 'save'. This saves the file as text-file with the exact same name, but w/o the little squares. I then compared the results-files using Word's compare tool. As I said, I lost the results2-file in this proces (after this the contents of results1 and -2 were identical). It is possible that in this process I mixed up these two files. I sure didn't use "Super Grub Disk hangs when embedding stage1_5" between the two. And it's very unlikely results3.txt got messed up as well. Would this make sense to you?

If you're *very *interested I could reinstall once more and repeat the procedure, making sure not to mess up. I would make an image of my Linux partition before doing this, and restore it afterwards; I guess the whole exercise would cost me little over an hour.


> **meierfra. said:**
> 
You have been dealing with two  problems:
[LIST]
[*]I) Grub does not work when the stage1.5 files  are used.[/LIST]

What makes you draw this conclusion? As far as I can see, this is not what the results file says. 

By the way: I noticed you and caljohnsmith wrote the Boot_Info_Script. Nice going!

---

### Post by meierfra. on 2009-03-20
>   [QUOTE]* I) Grub does not work when the stage1.5 files are used.

What makes you draw this conclusion?[/QUOTE]

First all of you solved your boot problem by using "Super Grub Disk hangs when embedding stage1_5".  This procedure installs Grub without the stage1.5 files.

Also

> Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.
means grub is installed with stage1.5. With  stage1.5  grub is able to locate files by their  name. It does not need to know the physical address of stage2.

and 

> Grub0.97 is installed in the MBR of /dev/sda and looks at sector 371491882 of the same hard drive for the stage2 file
means Grub is installed without  stage1.5 . Grub finds stage2 via  the physical address (sector   371491882 )


> If you're very interested I could reinstall once more and repeat the procedure,
No, that's ok.

But I'm curious whether you can boot via method "B" from my previous post.

So if you are willing to waste 10 minutes, try this:


```
sudo grub
root (hd0,5)
setup (hd0,5)
quit
```

and 

```
sudo lilo -M /dev/sda ext
sudo lilo -A /dev/sda 6

```

and see wether you can still boot into Xubuntu.
If this fails, just use "Super Grub Disk hangs when embedding stage1_5" one more time.

---

### Post by Roob on 2009-03-22
> **meierfra. said:**
> So if you are willing to waste 10 minutes, try this:


```
sudo grub
root (hd0,5)
setup (hd0,5)
quit
```

and 

```
sudo lilo -M /dev/sda ext
sudo lilo -A /dev/sda 6

```

and see wether you can still boot into Xubuntu.
If this fails, just use "Super Grub Disk hangs when embedding stage1_5" one more time.

Sure, anything for the advance of science ;) . It will take a while before I get to this though; I left my software (SGD included) at home, and I won't return here (my friend's place) till the end of march.

---

### Post by meierfra. on 2009-03-22
> Sure, anything for the advance of science

Thanks.

> will take a while before I get to this though; 
That's fine. No rush, in particular since there is  no real reason to do this anyway.

---

