---
title: "Grub + Win 7 + Jaunty = Help!"
date: 2009-10-02
forum: Installation &amp; Upgrades
---

### Post by impreziv on 2009-10-02
I have read many threads on this topic, but everything that I find has people using the same hard drive, which is partitioned, in order to boot both OS's. In my case I am using 2 separate hard drives to boot and I think that this is where my problem lies.

My hard drive configuration is as follows:

```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x92824e89

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   976762879   488380416    7  HPFS/NTFS

Disk /dev/sdb: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders, total 145226112 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0b090b09

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   139363874    69681906   83  Linux
/dev/sdb2       139363875   145211534     2923830    5  Extended
/dev/sdb5       139363938   145211534     2923798+  82  Linux swap / Solaris

Disk /dev/sdc: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders, total 586072368 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf72aa317

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        2048      206847      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdc2          206848   586070015   292931584    7  HPFS/NTFS

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x92824e89

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *        2048   976762879   488380416    7  HPFS/NTFS


```I have 4 hard drives in total. There are 2 500GB drives that are strictly for data. Then comes the 300GB drive which I installed Windows 7 Ultimate RC1 onto first. Finally, I have a 74GB drive that I have just installed Ubuntu 9.04 onto. Now, when I select the 300GB drive as my boot drive it boots right into Windows 7 and when I select the 74GB drive as my boot drive it boots right to the Grub boot loader, which is fine. The problem I am having is when I try to add either of them to the others boot menu. In Windows I tried using easybcd and I also tried to manually edit the boot menu, but it seemed very unlikely that I would get that to work. I then turned to the Grub boot loader and I have made more progress with that, but I still cant get it to boot into Windows. Whenever I select my Windows 7 boot option it tells me that BOOTMGR cannot be found. I read some posts suggesting to copy and past the BOOTMGR file from its C:\Windows directory to the root, but that did not work for me. Any help with this topic would be greatly appreciated :) !!!!

Here is my Windows 7 boot option in my menu.lst:


```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title        Windows 7
rootnoverify    (hd2,0)
savedefault
makeactive
chainloader    +1

```

---

### Post by Bucky Ball on 2009-10-02
[http://members.iinet.net/~herman546/p15.html#BOOTMGR_is_missing]("http://members.iinet.net/%7Eherman546/p15.html#BOOTMGR_is_missing")

Hope that helps. Maybe the Windows 7 BOOTmgr is not on hd2,0 as you would expect. Maybe try pointing to one of the other ntfs partitions, although it  seems unlikely it would be there. 

You should be able to repair it with the Windows 7 disk then try again if you can't find the bootmgr anywhere. In XP it is:

```
chkdisk
fixboot
fixmbr

```Worked for me to get things going again.

* On second thoughts, I just noticed something ... why are all your drives set to boot, specifically the two data drives??

---

### Post by oldfred on 2009-10-02
Win 7, when installed first, creates a separate small boot partition.

You may need to map back to drive 0. Your actual boot order in BIOS is important if you are changing drives around. If it is the third drive in BIOS:

title        Microsoft Windows 7
rootnoverify    (hd2,0)
savedefault
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader    +1

makeactive should not be required if the partition is set as boot with the *.

---

### Post by stereopanda on 2009-10-02
Try playing around with the GRUB entries..
I had the same problem today.. i dualbooted windows 7 + 9.04 on 2 disks.. for me the entry (hd1,1) worked.

---

### Post by Bucky Ball on 2009-10-02
Don't think mapping is going to work until the bootmgr is found. That is what's missing.

---

### Post by presence1960 on 2009-10-02
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by i.artiles on 2009-11-01
I am having a similar issue, I previously had winxp and ubuntu fine on one drive, but I was given win7 to try and I liked it. So I loaded win 7 on a 200gb ide drive and was not able to get into Ubuntu on a separate 250gb sata drive. I needed to update and switch over to 64bit anyways so I went ahead backed up to an external and proceeded to reinstall, this time jaunty amd64. I cant get grub to display the "vista" boot record and I would really apreciate any headway into this matter. Sorry if Im post jacking, but figured it would be worth a shot since its practically the same issue. 

fdisk -lu
```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa49fa49f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    81063989    40531963+  83  Linux
/dev/sda4        81063990   464744384   191840197+   f  W95 Ext'd (LBA)
/dev/sda5       251176338   464744384   106784023+   7  HPFS/NTFS
/dev/sda6        81064116   243175904    81055894+  83  Linux
/dev/sda7       243175968   251176274     4000153+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8d7c8d7c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   398295039   199146496    7  HPFS/NTFS

```

Results from boot_info_script
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa49fa49f

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    81,063,989    81,063,927  83 Linux
/dev/sda4          81,063,990   464,744,384   383,680,395   f W95 Ext d (LBA)
/dev/sda5         251,176,338   464,744,384   213,568,047   7 HPFS/NTFS
/dev/sda6          81,064,116   243,175,904   162,111,789  83 Linux
/dev/sda7         243,175,968   251,176,274     8,000,307  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8d7c8d7c

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   398,295,039   398,292,992   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="c11fe6a3-dab8-4998-96d1-5d97d396ea2b" TYPE="ext4" 
/dev/sda5: UUID="01411B636D1DD15D" TYPE="ntfs" 
/dev/sda6: UUID="c5d6c092-475c-43b3-b8d3-17f6ca2dd933" TYPE="ext4" 
/dev/sda7: UUID="6437d44a-7981-4dc0-9e14-b75ec08e6e5f" TYPE="swap" 
/dev/sdb1: UUID="50E4BFEFE4BFD606" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda1 on / type ext4 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-16-generic/volatile type tmpfs (rw,mode=755)
/dev/sda6 on /home type ext4 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/archimedes/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=archimedes)


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
# kopt=root=UUID=c11fe6a3-dab8-4998-96d1-5d97d396ea2b ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=c11fe6a3-dab8-4998-96d1-5d97d396ea2b

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

title		Ubuntu 9.04, kernel 2.6.28-16-generic
uuid		c11fe6a3-dab8-4998-96d1-5d97d396ea2b
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=c11fe6a3-dab8-4998-96d1-5d97d396ea2b ro quiet splash 
initrd		/boot/initrd.img-2.6.28-16-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
uuid		c11fe6a3-dab8-4998-96d1-5d97d396ea2b
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=c11fe6a3-dab8-4998-96d1-5d97d396ea2b ro  single
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		c11fe6a3-dab8-4998-96d1-5d97d396ea2b
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=c11fe6a3-dab8-4998-96d1-5d97d396ea2b ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		c11fe6a3-dab8-4998-96d1-5d97d396ea2b
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=c11fe6a3-dab8-4998-96d1-5d97d396ea2b ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		c11fe6a3-dab8-4998-96d1-5d97d396ea2b
kernel		/boot/memtest86+.bin
quiet

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
UUID=c11fe6a3-dab8-4998-96d1-5d97d396ea2b /               ext4    relatime,errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=c5d6c092-475c-43b3-b8d3-17f6ca2dd933 /home           ext4    relatime        0       2
# swap was on /dev/sda7 during installation
UUID=6437d44a-7981-4dc0-9e14-b75ec08e6e5f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


   1.2GB: boot/grub/menu.lst
   2.4GB: boot/grub/stage2
   2.4GB: boot/initrd.img-2.6.28-11-generic
    .8GB: boot/initrd.img-2.6.28-16-generic
   2.4GB: boot/vmlinuz-2.6.28-11-generic
    .9GB: boot/vmlinuz-2.6.28-16-generic
    .8GB: initrd.img
   2.4GB: initrd.img.old
    .9GB: vmlinuz
   2.4GB: vmlinuz.old
```

---

### Post by i.artiles on 2009-11-02
okay updated grub menu.lst to include windows 7 
```
title		Windows 7
# root		(hd1,0)
# makeactive
# chainloader	+1
map (hd0) (hd1)
map (hd1) (hd0)
```

When I press enter on grub menu nothing happens. I did try and change hd1 to sd1 and ended up getting error 23 in grub.

---

