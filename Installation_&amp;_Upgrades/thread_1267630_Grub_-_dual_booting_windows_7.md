---
title: "Grub - dual booting windows 7"
date: 2009-09-16
forum: Installation &amp; Upgrades
---

### Post by dazman19 on 2009-09-16
Hi,

I have dual booted windows XP and windows Vista in the past using this from my /boot/grub/menu.lst


title windows
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1,1)
makeactive
chainloader +1

And it has worked for BOTH OS's. But now i try to do windows 7 and it doesnt seem to want to work. At first i thought it was cuz of that stupid 100mb partition windows 7 makes for the bitlocker drive. so i re-installed windows 7  and got rid of the bitlocker. And then re-attached it and booted to the grub hard drive that has the menu.lst file. 

And it doesnt work anymore. I get Error 22: no such partition. 

Any idea's on what I put in there? If i disconnect the linux hard drive windows boots. And I can boot linux thats not a problem. I have tried:

map (hd0) (hd1,1)
map (hd1,1) (hd0)

And this didnt work either.. any help?

---

### Post by presence1960 on 2009-09-16
Let's get a better look at your setup. Boot the Ubuntu Live CD. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by dazman19 on 2009-09-16
Here we go. 

FYI linux sees the drive sdb as the one i want to boot in windows. 

I HAVE NOT MOUNTED it in linux and dont intend to.

heres my /etc/fstab
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sdc1       /data                   ntfs    defaults        0       0
/dev/sdd2       /video          ntfs    defaults        0       0





and the rest.. 





============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
 => No boot loader is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ext3
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
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /grldr

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdc1 has 
                       1465143295 sectors, but according to the info from 
                       fdisk, it has 1465144002 sectors.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdd2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa3d0a3d1

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   292,961,339   292,961,277  83 Linux
/dev/sda2         292,961,340   312,576,704    19,615,365   5 Extended
/dev/sda5         292,961,403   312,576,704    19,615,302  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
240 heads, 63 sectors/track, 20673 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x10f3da8c

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   312,578,047   312,576,000   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9ae58afc

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63 1,465,144,064 1,465,144,002  42 SFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa3d0a3d0

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                   1 1,465,149,167 1,465,149,167  ee GPT


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sdd1              34       262,177       262,144 Microsoft Windows
/dev/sdd2         264,192 1,465,147,391 1,464,883,200 Linux (usually)

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="893c0d9e-fe59-4b17-b756-a2eff952973d" TYPE="ext3" 
/dev/sda5: UUID="421d666a-7604-4ad3-85f7-e8373b32b309" TYPE="swap" 
/dev/sdb1: UUID="FAE8BA7AE8BA34AB" LABEL="System Reserved" TYPE="ntfs" 
/dev/sdc1: UUID="EAB0B00AB0AFDAF9" LABEL="DataDrive" TYPE="ntfs" 
/dev/sdd2: UUID="14FC2255FC223182" LABEL="Video" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-13-generic/volatile type tmpfs (rw,mode=755)
/dev/sdc1 on /data type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdd2 on /video type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/daz/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=daz)


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
timeout		8

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
# kopt=root=UUID=893c0d9e-fe59-4b17-b756-a2eff952973d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=893c0d9e-fe59-4b17-b756-a2eff952973d

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

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		893c0d9e-fe59-4b17-b756-a2eff952973d
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=893c0d9e-fe59-4b17-b756-a2eff952973d ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		893c0d9e-fe59-4b17-b756-a2eff952973d
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=893c0d9e-fe59-4b17-b756-a2eff952973d ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-12-generic
uuid		893c0d9e-fe59-4b17-b756-a2eff952973d
kernel		/boot/vmlinuz-2.6.28-12-generic root=UUID=893c0d9e-fe59-4b17-b756-a2eff952973d ro quiet splash 
initrd		/boot/initrd.img-2.6.28-12-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-12-generic (recovery mode)
uuid		893c0d9e-fe59-4b17-b756-a2eff952973d
kernel		/boot/vmlinuz-2.6.28-12-generic root=UUID=893c0d9e-fe59-4b17-b756-a2eff952973d ro  single
initrd		/boot/initrd.img-2.6.28-12-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		893c0d9e-fe59-4b17-b756-a2eff952973d
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=893c0d9e-fe59-4b17-b756-a2eff952973d ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		893c0d9e-fe59-4b17-b756-a2eff952973d
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=893c0d9e-fe59-4b17-b756-a2eff952973d ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		893c0d9e-fe59-4b17-b756-a2eff952973d
kernel		/boot/memtest86+.bin
quiet

title		Windows 7
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify	(hd1,1)
makeactive	
chainloader	+1

### END DEBIAN AUTOMAGIC KERNELS LIST

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
UUID=893c0d9e-fe59-4b17-b756-a2eff952973d /               ext3    relatime,errors=remount-ro 0       1
# /seagate160/ was on /dev/sdb1 during installation
UUID=a99cfbaa-65b4-42f4-bb61-97de5a5bc564 /seagate160/    ext3    relatime        0       2
# swap was on /dev/sda5 during installation
UUID=421d666a-7604-4ad3-85f7-e8373b32b309 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sdc1       /data                   ntfs    defaults        0       0
/dev/sdd2       /video          ntfs    defaults        0       0

=================== sda1: Location of files loaded by Grub: ===================


 109.4GB: boot/grub/menu.lst
  53.0GB: boot/grub/stage2
  53.1GB: boot/initrd.img-2.6.28-11-generic
  53.0GB: boot/initrd.img-2.6.28-12-generic
  56.4GB: boot/initrd.img-2.6.28-13-generic
  53.0GB: boot/vmlinuz-2.6.28-11-generic
  53.1GB: boot/vmlinuz-2.6.28-12-generic
 100.0GB: boot/vmlinuz-2.6.28-13-generic
  56.4GB: initrd.img
  53.0GB: initrd.img.old
 100.0GB: vmlinuz
  53.1GB: vmlinuz.old

---

### Post by presence1960 on 2009-09-16
reboot your machine and go into BIOS & make sure sda is set as first hard disk to boot & sdb is set as second. Save changes to CMOS (if you made changes) and continue to boot into Ubuntu.

Edit your windows entry in menu.lst to this:

```
title          Windows 7
rootnoverify   (hd1,0)
map            (hd0) (hd1)
map            (hd1) (hd0)
chainloader    +1
```

Click save on toolbar, close file and reboot. Try windows from GRUB menu.

---

### Post by dazman19 on 2009-09-16
Nice job, thanks very much, it worked.

It wasnt much of a change to what I had though.
Just changed the rootnoverify from (hd1,1) to (hd1,0) and drop the makeactive.

---

### Post by presence1960 on 2009-09-16
> **dazman19 said:**
> Nice job, thanks very much, it worked.

It wasnt much of a change to what I had though.
Just changed the rootnoverify from (hd1,1) to (hd1,0) and drop the makeactive.

Just so you are aware, numbering for GRUB devices (x) and partitions (y) in (hdx,y) start with 0. sda1 = (hd0,0), sda2 = (hd0,1), sda3 = (hd0,2) etc..same for sdb, sdc, etc.

But for devices (x) in (hdx,y) it is the boot order in BIOS that determines the x designation for that is the actual order of the disks regardless of what fdisk reports. That's why i specified set sda as first boot & sdb as second boot in BIOS.

Glad you got it working.

---

