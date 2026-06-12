---
title: "No bootable Device error"
date: 2009-09-29
forum: Installation &amp; Upgrades
---

### Post by ddsvi78 on 2009-09-29
After a fresh install of Ubuntu Server I get the error " No bootable device -- insert disk and press any key "

If I put the live CD in and select "Boot from first hard drive" Grub loads and everything comes up as expected. But I cant seem to get the system to boot directly to the first hard drive without the Live CD. 

I have checked the boot order in the BIOS and have set the Hard drive to be first in line, this hasnt helped. Just for fun I tried going through the system recovery option on the Live CD and when it gets to detecting the filesystem. It says something to the affect of No file system found, it may not be mounted or something like that. If you need the full error I get here, I can go through that process again.

But then I put the live cd in again, select boot from first hard drive and everything boots up perfectly.

Any ideas?

---

### Post by rreese6 on 2009-09-29
Looks as if you did not write grub to the Master Boot Record (MBR) but to the first sector of the HD. Once you boot up on the live CD you could run grub-install to fix that

---

### Post by ddsvi78 on 2009-09-29
Thanks rresse6 for the reply.

I am not sure how to correctly run grub-install. 

However I did do the following.


```
grub> find /boot/grub/stage1
 (hd0,0)
 (hd1,0)

grub> root (hd0,0)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,0)/boot/grub/stage2
/boot/grub/menu.lst"... failed

Error 22: No such partition

grub>

```

---

### Post by ddsvi78 on 2009-09-29
LOL, now since I have done that, I cant boot up using the CD any longer.

So I went ahead and went back through the recover a broken system option. Here is the message I get:


The installer could not find any partitions, so you will not be able to mount a root file system. This may be caused by the kernel failing to detect your hard disk drive or failing to read the partition table, or the disk may be  unpartitioned. If you wish, you may investigate this from a shell in the installer environment.
No partitions Found


This is the same message I was getting before I mucked it up worse.

---

### Post by presence1960 on 2009-09-29
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by ddsvi78 on 2009-09-29
Here you go,





```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #256 for /boot/grub/stage2.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #256 for /boot/grub/stage2.

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

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00019b67

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   613,120,724   613,120,662  83 Linux
/dev/sda2         613,120,725   625,137,344    12,016,620   5 Extended
/dev/sda5         613,120,788   625,137,344    12,016,557  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00019b67

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   613,120,724   613,120,662  83 Linux
/dev/sdb2         613,120,725   625,137,344    12,016,620   5 Extended
/dev/sdb5         613,120,788   625,137,344    12,016,557  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="3afcdb75-753e-4681-9ad9-8861385c60f6" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="da1566a3-6220-4239-90c2-2376a7ec4a26" TYPE="swap" 
/dev/sdb1: UUID="3afcdb75-753e-4681-9ad9-8861385c60f6" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: UUID="da1566a3-6220-4239-90c2-2376a7ec4a26" TYPE="swap" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
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
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=/dev/mapper/isw_bebiecfafj_Volume01 ro

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

title        Ubuntu 9.04, kernel 2.6.28-11-server
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.28-11-server root=/dev/mapper/isw_bebiecfafj_Volume01 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-server

title        Ubuntu 9.04, kernel 2.6.28-11-server (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.28-11-server root=/dev/mapper/isw_bebiecfafj_Volume01 ro  single
initrd        /boot/initrd.img-2.6.28-11-server

title        Ubuntu 9.04, memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin

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
# / was on /dev/mapper/isw_bebiecfafj_Volume01 during installation
UUID=3afcdb75-753e-4681-9ad9-8861385c60f6 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/mapper/isw_bebiecfafj_Volume05 during installation
UUID=da1566a3-6220-4239-90c2-2376a7ec4a26 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  75.5GB: boot/grub/menu.lst
  75.4GB: boot/grub/stage2
  75.5GB: boot/initrd.img-2.6.28-11-server
  75.4GB: boot/vmlinuz-2.6.28-11-server
  75.5GB: initrd.img
  75.4GB: vmlinuz

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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=/dev/mapper/isw_bebiecfafj_Volume01 ro

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

title        Ubuntu 9.04, kernel 2.6.28-11-server
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.28-11-server root=/dev/mapper/isw_bebiecfafj_Volume01 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-server

title        Ubuntu 9.04, kernel 2.6.28-11-server (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.28-11-server root=/dev/mapper/isw_bebiecfafj_Volume01 ro  single
initrd        /boot/initrd.img-2.6.28-11-server

title        Ubuntu 9.04, memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/mapper/isw_bebiecfafj_Volume01 during installation
UUID=3afcdb75-753e-4681-9ad9-8861385c60f6 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/mapper/isw_bebiecfafj_Volume05 during installation
UUID=da1566a3-6220-4239-90c2-2376a7ec4a26 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


  75.5GB: boot/grub/menu.lst
  75.4GB: boot/grub/stage2
  75.5GB: boot/initrd.img-2.6.28-11-server
  75.4GB: boot/vmlinuz-2.6.28-11-server
  75.5GB: initrd.img
  75.4GB: vmlinuz

```

---

### Post by presence1960 on 2009-09-29
It looks like you have a RAID array, correct? Unfortunately I am not versed in RAID.

But I did notice that your GRUB in both MBRs points to partition # 256 which does not exist. I would look into that.

---

### Post by ddsvi78 on 2009-09-29
Yes you are correct there is a Raid 1 setup.
 
Can you point me in the right direction for fixing grub to point to the correct partition?
 
If you think that this issue has to do with the raid, I can always remove the hardware raid and re-install linux.

---

### Post by presence1960 on 2009-09-29
> **ddsvi78 said:**
> Yes you are correct there is a Raid 1 setup.
 
Can you point me in the right direction for fixing grub to point to the correct partition?
 
If you think that this issue has to do with the raid, I can always remove the hardware raid and re-install linux.

I am not versed in RAID, but you can try this. Your GRUB is pointing to partition # 256 but your Ubuntu is on the first partition on both disks.

```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,0) &  (hd1,0)". Use whatever your computer spits out for the following lines.
5. Type "root (hd0,0)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR
```
 
This will fix sda, now do sdb:

```
1. Type "root (hd1,0)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
2. Type "setup (hd1)", to install GRUB to MBR
3. Quit grub by typing "quit".
4. Reboot and remove the bootable CD.
```

Like I said I am not versed in RAID so I do not know if when you restore GRUB on sda if it will also put it on sdb. But these are the correct partitions for GRUB to point to.

---

### Post by ddsvi78 on 2009-09-30
Ok, I did that, and rebooted without the CD, I still get the Insert Bootable Disk message. So I boot back up with the CD and run that utility again. Here is what I get.



```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

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

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00019b67

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   613,120,724   613,120,662  83 Linux
/dev/sda2         613,120,725   625,137,344    12,016,620   5 Extended
/dev/sda5         613,120,788   625,137,344    12,016,557  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00019b67

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   613,120,724   613,120,662  83 Linux
/dev/sdb2         613,120,725   625,137,344    12,016,620   5 Extended
/dev/sdb5         613,120,788   625,137,344    12,016,557  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="3afcdb75-753e-4681-9ad9-8861385c60f6" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="da1566a3-6220-4239-90c2-2376a7ec4a26" TYPE="swap" 
/dev/sdb1: UUID="3afcdb75-753e-4681-9ad9-8861385c60f6" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: UUID="da1566a3-6220-4239-90c2-2376a7ec4a26" TYPE="swap" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
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
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=/dev/mapper/isw_bebiecfafj_Volume01 ro

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

title        Ubuntu 9.04, kernel 2.6.28-11-server
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.28-11-server root=/dev/mapper/isw_bebiecfafj_Volume01 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-server

title        Ubuntu 9.04, kernel 2.6.28-11-server (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.28-11-server root=/dev/mapper/isw_bebiecfafj_Volume01 ro  single
initrd        /boot/initrd.img-2.6.28-11-server

title        Ubuntu 9.04, memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin

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
# / was on /dev/mapper/isw_bebiecfafj_Volume01 during installation
UUID=3afcdb75-753e-4681-9ad9-8861385c60f6 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/mapper/isw_bebiecfafj_Volume05 during installation
UUID=da1566a3-6220-4239-90c2-2376a7ec4a26 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  75.5GB: boot/grub/menu.lst
  75.4GB: boot/grub/stage2
  75.5GB: boot/initrd.img-2.6.28-11-server
  75.4GB: boot/vmlinuz-2.6.28-11-server
  75.5GB: initrd.img
  75.4GB: vmlinuz

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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=/dev/mapper/isw_bebiecfafj_Volume01 ro

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

title        Ubuntu 9.04, kernel 2.6.28-11-server
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.28-11-server root=/dev/mapper/isw_bebiecfafj_Volume01 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-server

title        Ubuntu 9.04, kernel 2.6.28-11-server (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.28-11-server root=/dev/mapper/isw_bebiecfafj_Volume01 ro  single
initrd        /boot/initrd.img-2.6.28-11-server

title        Ubuntu 9.04, memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/mapper/isw_bebiecfafj_Volume01 during installation
UUID=3afcdb75-753e-4681-9ad9-8861385c60f6 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/mapper/isw_bebiecfafj_Volume05 during installation
UUID=da1566a3-6220-4239-90c2-2376a7ec4a26 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


  75.5GB: boot/grub/menu.lst
  75.4GB: boot/grub/stage2
  75.5GB: boot/initrd.img-2.6.28-11-server
  75.4GB: boot/vmlinuz-2.6.28-11-server
  75.5GB: initrd.img
  75.4GB: vmlinuz

```

---

### Post by ddsvi78 on 2009-09-30
Doing this did fix the issue so that I can get back in using the LIVE CD option "Boot from first hard drive".

So now I am back to my original issue. I wander if it does have to do with the RAID. I have attempted the install 3 times on this machine with the same result using different guided install options.

---

### Post by presence1960 on 2009-09-30
> **ddsvi78 said:**
> Doing this did fix the issue so that I can get back in using the LIVE CD option "Boot from first hard drive".

So now I am back to my original issue. I wander if it does have to do with the RAID. I have attempted the install 3 times on this machine with the same result using different guided install options.

Did you install with the alternate text based installer? This has support for RAID set up where the Live CD does not. Get it [here]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate").

I wish I know more about RAID. Maybe someone who does will come along.

---

### Post by ddsvi78 on 2009-09-30
No I didnt install with the text based installer. I would prefer to figure out how to fix it, just for future knowledge instead of just re-installing again. But if we cant figure it out, then I will go ahead and re-install. I think I will wait a day or 2 to see if anyone has any further ideas.

We have to be close. The server is up and running, just have to use the CD to get Grub to load.

---

### Post by presence1960 on 2009-09-30
> **ddsvi78 said:**
> No I didnt install with the text based installer. I would prefer to figure out how to fix it, just for future knowledge instead of just re-installing again. But if we cant figure it out, then I will go ahead and re-install. I think I will wait a day or 2 to see if anyone has any further ideas.

We have to be close. The server is up and running, just have to use the CD to get Grub to load.

Sounds like a good plan. Sorry I don't know RAID. I do know that the alternate installer will detect your RAID and ask you if you want to activate it. Wish I knew more about RAID.

You may want to consider marking this thread as solved and start a new thread with RAID in the title so to draw attention from those with RAID knowledge.

---

### Post by ddsvi78 on 2009-10-02
Hey Presence1960,

Just wanted to shoot you a reply and say I got it fixed. I ended up using Super Grub Disk and Activating the first Partition. Once I did this, everything loaded up perfectly.

Thanks for the help.

link for reference: [http://www.supergrubdisk.org/forum/index.php?topic=375.0](http://www.supergrubdisk.org/forum/index.php?topic=375.0)

---

### Post by presence1960 on 2009-10-02
> **ddsvi78 said:**
> Hey Presence1960,

Just wanted to shoot you a reply and say I got it fixed. I ended up using Super Grub Disk and Activating the first Partition. Once I did this, everything loaded up perfectly.

Thanks for the help.

link for reference: [http://www.supergrubdisk.org/forum/index.php?topic=375.0](http://www.supergrubdisk.org/forum/index.php?topic=375.0)

Great news! Sorry i couldn't be more help but I know close to nothing about RAID. Enjoy ubuntu.

---

### Post by huuan on 2010-01-12
I had a similar problem involving RAID1 and no bootable device which I just solved yesterday. The catalyst was a post on the apple intel users ubuntu forum 
[http://ubuntuforums.org/showthread.php?t=761023](http://ubuntuforums.org/showthread.php?t=761023)
which talked about using something called refit to sync the partition table.
I ended up using a related tool called gptsync which fixed the problem (woohoo!)
-------------
from man gptsync:
 gptsync - GPT partition table to MBR partition table synchronisation
 gptsync reads the GPT partition table on device and synchronises the legacy MBR partition table with the GPT partition table. The MBR partition table can hold only 4 partitions.

       Legacy bootloaders or operating systems that do not support GPT require an MBR partition table; this is typically the case when using GRUB or LILO on an Intel-based Apple machine.
-------------------
I wasn't using a mac, here's the background in case other folks have the same issue:
intel i7 cpu, ubuntu 9.10 server, 2 sata hdd in raid1 for /, swap and 1 other partition but ext3 for /boot
partition table like this for each of two 2TB disks with 1st partition on each bootable.
100MB /boot ext3 (boot enabled)
20GB / RAID1
6GB swap RAID1
1000GB /shares RAID1
9xxGB spare for later

The reason I'm using separate ext3 /boot is that the 9.10 server installer would not support booting from RAID1 and so I ended up regressing to grub legacy and having a separate boot partition.

The install went fine, RAID1 works and reboot worked fine with both drives in place. Now I needed to be able to boot from the second hard drive in case of failure of the first drive so I copied over /boot to the 2nd drive and tried it out but kept getting "No bootable device" when trying to boot from the second hard drive with the first removed. 

Lots of research, reinstalls and trying different things over many days, all to no avail until I found that message in the apple users section about refit.

Installed refit and somehow gptsync came with it so I read man on both and the gptsync seemed more applicable to my case so I tried it out and saw that it was friendly in that it shows you what it will do before it does it and gives you the chance to opt out.
Here's what gptsync shows on a run for my system:
# gptsync /dev/sda


Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             34       195346  EFI System (FAT)
 2         195347     39257847  Linux RAID
 3       39257848     50976598  Linux RAID
 4       50976599   2004101599  Linux RAID

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1 *            1   3907029167  ee  EFI Protective

Status: MBR table must be updated.

Proposed new MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1           33  ee  EFI Protective
 2 *           34       195346  83  Linux
 3         195347     39257847  fd  Linux RAID
 4       39257848     50976598  fd  Linux RAID

After I ran gptsync on both drives I can now boot from either with the other removed. woohoo! Thanks Christoph Pfisterer for gptsync. :popcorn:

---

