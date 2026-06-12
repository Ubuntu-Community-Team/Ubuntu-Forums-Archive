---
title: "[SOLVED] Fresh Install with Grub error 17"
date: 2009-01-07
forum: Installation &amp; Upgrades
---

### Post by NEUR0M4NCER on 2009-01-07
Hi guys.

[noparse][back-story][/noparse]
I've been using Ubuntu for a couple years now, thought I knew what I was doing - just bought a nice big HD, planned to use it as a media storage drive, and re-format/re-install Ubuntu on the original drive to clean up all of the dirty, undisciplined "*tweaks*" i've done over the last year...
[noparse][/back-story][/noparse]

So after copying all of my data to the new HD, I installed 8.10 AMD64 and re-booted; oh dear.
```
Grub Error 17
```
```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders, total 240121728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6c136ec4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   240107489   120053713+  83  Linux

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000b08da

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   300527954   150263946   83  Linux
/dev/sdb2       300527955   312576704     6024375    5  Extended
/dev/sdb5       300528018   312576704     6024343+  82  Linux swap / Solaris

Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00073bed

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63  2930272064  1465136001   83  Linux
```

I'm a bit lost with this... i'm sure it's something ridiculously simple, but I can't see it right now. Any help would be awesome.

---

### Post by neu2buntu on 2009-01-07
have you checked the basics to make sure your bios is set to boot from /dev/sdb first where the bootloader is

---

### Post by NEUR0M4NCER on 2009-01-07
Yep. Definitely set to boot from the 160GB drive - it was the first thing I did.

---

### Post by neu2buntu on 2009-01-07
maybe try your menu.lst file incase somethings changed here and/or booting without your new disk not  plugged in (if you havnt already tried?)

---

### Post by NEUR0M4NCER on 2009-01-07
Sounding terribly 'green' here, but... what might I be looking for in menu.lst?

(thanks for your help)

---

### Post by neu2buntu on 2009-01-07
i had a prob before and changing the root hd to the right disk solved it, so you will want it to be (hd1,0)   or youcoul just change them manually at the boot prompt

---

### Post by neu2buntu on 2009-01-07
```
gedit /boot/grub/menu.lst
```    post the output of this, i just treat every1 as noobs (you prob know more about this than me...lol):lolflag:

---

### Post by NEUR0M4NCER on 2009-01-07
No, I appreciate the hand-holding.

I actually had to mount the drive and go to /media/disk/boot/grub/menu.lst because I can only run from the LiveCD now.

Here's what's in the menu.lst - not sure what to look for, because it's using the UUID instead of normal bloody words...
```
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
# kopt=root=UUID=6ae8b74e-97ed-4b15-8031-2a7cdc8ea004 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=6ae8b74e-97ed-4b15-8031-2a7cdc8ea004

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
uuid		6ae8b74e-97ed-4b15-8031-2a7cdc8ea004
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=6ae8b74e-97ed-4b15-8031-2a7cdc8ea004 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		6ae8b74e-97ed-4b15-8031-2a7cdc8ea004
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=6ae8b74e-97ed-4b15-8031-2a7cdc8ea004 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		6ae8b74e-97ed-4b15-8031-2a7cdc8ea004
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by neu2buntu on 2009-01-07
was just looking at my own menu.lst there.. and mine has a uuid= instead of the root= , so if this is the same in your case make sure the part ##default grub root device ,groot=(long code of nums and letters) matches uuid=(long code of nums and letters) too:D

---

### Post by NEUR0M4NCER on 2009-01-07
Yeah, they match. Hmph. What now?

---

### Post by neu2buntu on 2009-01-07
just seen your menu.lst there now, and it looks ok ...im stomped here too m8!!!  sorry i cant be more help atm.. i will check in 2morrow to see if you got it sorted

---

### Post by NEUR0M4NCER on 2009-01-07
No probs - thanks for your help so far!

---

### Post by caljohnsmith on 2009-01-07
Do you get the Grub error 17 before seeing a Grub menu, or before seeing the text "Press ESC to see menu", or do you get the error after selecting Ubuntu in the Grub menu? I would assume the former case, but I just want to check to be sure. In order to get a clearer picture of your setup, how about opening a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your problem might be.

---

### Post by NEUR0M4NCER on 2009-01-07
Hi - yes, I get the error before "Press Esc to see Menu".

Here's the output of boot_info_script:
```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sdb2: _________________________________________________________________________

    File system:       Extended Partition

sdb5: _________________________________________________________________________

    File system:       swap

sdc1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders, total 240121728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6c136ec4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   240107489   120053713+  83  Linux

sfdisk -V /dev/sda:

Warning: no primary partition is marked bootable (active)
This does not matter for LILO, but the DOS MBR will not boot this disk.
/dev/sda: OK

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000b08da

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   300527954   150263946   83  Linux
/dev/sdb2       300527955   312576704     6024375    5  Extended
/dev/sdb5       300528018   312576704     6024343+  82  Linux swap / Solaris

sfdisk -V /dev/sdb:

/dev/sdb: OK

Drive sdc: _____________________________________________________________________

fdisk -lu /dev/sdc:

Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00073bed

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63  2930272064  1465136001   83  Linux

sfdisk -V /dev/sdc:

Warning: no primary partition is marked bootable (active)
This does not matter for LILO, but the DOS MBR will not boot this disk.
/dev/sdc: OK

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="475c28ef-8e43-48ae-807d-46cfabdffc43" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb1: UUID="6ae8b74e-97ed-4b15-8031-2a7cdc8ea004" TYPE="ext3" 
/dev/sdb5: UUID="f0115bc3-7656-47c9-84c5-6f417231fa7d" TYPE="swap" 
/dev/sdc1: UUID="1eebe4aa-0c65-4487-a8d3-09181486d34c" SEC_TYPE="ext2" TYPE="ext3" 
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
/dev/sdb1 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)

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
# kopt=root=UUID=6ae8b74e-97ed-4b15-8031-2a7cdc8ea004 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=6ae8b74e-97ed-4b15-8031-2a7cdc8ea004

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
uuid		6ae8b74e-97ed-4b15-8031-2a7cdc8ea004
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=6ae8b74e-97ed-4b15-8031-2a7cdc8ea004 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		6ae8b74e-97ed-4b15-8031-2a7cdc8ea004
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=6ae8b74e-97ed-4b15-8031-2a7cdc8ea004 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		6ae8b74e-97ed-4b15-8031-2a7cdc8ea004
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=6ae8b74e-97ed-4b15-8031-2a7cdc8ea004 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=f0115bc3-7656-47c9-84c5-6f417231fa7d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sdb1/boot: ==================================

total 12808
drwxr-xr-x  3 root root    4096 2009-01-07 23:33 .
drwxr-xr-x 20 root root    4096 2009-01-07 23:33 ..
-rw-r--r--  1 root root  503560 2008-10-24 07:55 abi-2.6.27-7-generic
-rw-r--r--  1 root root   85316 2008-10-24 07:55 config-2.6.27-7-generic
drwxr-xr-x  2 root root    4096 2009-01-07 23:34 grub
-rw-r--r--  1 root root 8644662 2009-01-07 23:33 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root  124152 2008-09-11 20:11 memtest86+.bin
-rw-r--r--  1 root root 1352144 2008-10-24 07:55 System.map-2.6.27-7-generic
-rw-r--r--  1 root root    1130 2008-10-24 07:57 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root 2339712 2008-10-24 07:55 vmlinuz-2.6.27-7-generic

=============================== sdb1/boot/grub: ===============================

total 216
drwxr-xr-x 2 root root   4096 2009-01-07 23:34 .
drwxr-xr-x 3 root root   4096 2009-01-07 23:33 ..
-rw-r--r-- 1 root root    197 2009-01-07 23:33 default
-rw-r--r-- 1 root root     45 2009-01-07 23:33 device.map
-rw-r--r-- 1 root root   8108 2009-01-07 23:33 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2009-01-07 23:33 fat_stage1_5
-rw-r--r-- 1 root root     16 2009-01-07 23:33 installed-version
-rw-r--r-- 1 root root   8712 2009-01-07 23:33 jfs_stage1_5
-rw-r--r-- 1 root root   4310 2009-01-07 23:34 menu.lst
-rw-r--r-- 1 root root   7352 2009-01-07 23:33 minix_stage1_5
-rw-r--r-- 1 root root   9756 2009-01-07 23:33 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2009-01-07 23:33 stage1
-rw-r--r-- 1 root root 121460 2009-01-07 23:33 stage2
-rw-r--r-- 1 root root   9556 2009-01-07 23:33 xfs_stage1_5

=============================== StdErr Messages: ===============================

No errors were reported.
```
Oh. So it seems none of the drives are marked 'boot'... how might I go about fixing that?

---

### Post by caljohnsmith on 2009-01-07
OK, I think I see the problem; the Grub that is installed to your Ubuntu sdb drive points to the 5th partition for its boot files, but sdb5 is your swap partition. How about doing:
```
sudo grub
grub> root (hd1,0)
grub> setup (hd1)
grub> quit
```
Then reboot, make sure you set your BIOS to boot the 160 GB Ubuntu drive, and if all goes well you should be able to boot into Ubuntu. Also, about your question, the sdb1 Ubuntu partition is all ready marked as bootable, so you don't need to worry about setting the boot flag on any partitions. The "no primary partition is marked bootable (active)" warnings that you see are for your other drives, so if you can set your BIOS to boot the Ubuntu drive, you shouldn't need to worry about setting the boot flag for your sda or sdc drives. Let me know how it goes or if you run into problems. :)

---

### Post by NEUR0M4NCER on 2009-01-07
Thank-you so much - i'm booted into the new install. Now I just need to figure out why it won't install restricted GFX drivers or run update... but i'll figure those out on my own.

Thanks again!

---

### Post by caljohnsmith on 2009-01-07
Glad to hear that worked OK. Good luck with your GFX drivers, cheers and have fun with Ubuntu. :)

---

### Post by BLTicklemonster on 2009-04-25
Whoa, I've got a doozy.

here's my boot info script:

```
#!/bin/bash
#to use this script:
#
#sudo bash boot_info_script_024.sh
#
#date  1/31/09
#authors  meierfra.  and  caljohnsmith
#version 0.24
# 
#Looks at all MBRs and identifies the boot loader. 
#   For Grub and Supergrub:  displays the controlling partition.
#   If the  MBR is unknown, displays the whole MBR.
#Looks at all  partitions:
#   Determines their type
#   Identifies their boot sectors.
#         For grub: displays the controlling partition and the offset
#         of the stage2 file as recorded in the boot sector.
#         For NTFS and Fat, examines the Boot Parameter Block for errors.
#   Identifies the operating system
#   Lists  boot programs.
#   Displays the partition table
#   Displays "blkid -c /dev/null"
#   Finds  boot directories and displays their contents.
#   Looks in "/" and "NST" for  bootpart codes  and displays the offset
#                and boot drive it is trying to chainload
#   Looks on "/" and "/NST" for stage1 files and displays the offset
#         and bootdrive of the stage 2  files is trying to chainload.
#    displays  boot configuration files.
#All information is written to the file "RESULTS.txt" in the
#    same folder as the script

###### check whether user is rootsu
if [ $(whoami) != "root" ];
then 
   echo  Please use \"sudo\" or become \"root\" to run this script. >&2;
   exit 1;
fi;  

########  List of folders which might contained files used for chainloading
Boot_Codes_Dir="
    /
    /NST/
    "
#################  List of folders whose content will be displayed
################# Since all the important files in these folder are alreadt displayed
################# it doesn't seem necessary to display the contents of these folders.
#Boot_Dir="
#   /Boot
#    /boot
#    /BOOT
#    /boot/grub
#    /grub
#    /ubuntu/disks
#    /ubuntu/disks/boot/
#    /ubuntu/disks/boot/grub
#    /ubuntu/disks/install/boot
#    /ubuntu/disks/boot/grub
#    /NST
#    "


##############  List of files whose names will be displayed (if they exists)
Boot_Prog="
     /bootmgr /BOOTMGR
     /boot/bcd /BOOT/bcd /Boot/bcd  /boot/BCD /BOOT/BCD  /Boot/BCD
     /grldr /GRLDR
     /ntldr /NTLDR
     /NTDETECT.COM    /ntdetect.com
     /NTBOOTDD.SYS    /ntbootdd.sys
     /wubildr.mbr    /ubuntu/winboot/wubildr.mbr
     /ubuntu/disks/root.disk
     /ubuntu/disks/
     /ubunut/disks/swap.disk
     /core.img   /grub/core.img     /boot/grub/core.img
     /boot/map      /map
     /DEFAULT.MNU /default.mnu
     "

############### List of files whose contents will be displayed.
Boot_Files="
    /boot/grub/menu.lst /grub/menu.lst  /NST/menu.lst    /menu.lst
    /grub.cfg    /grub/grub.cfg    /boot/grub/grub.cfg
    /ubuntu/disks/boot/grub/menu.lst /ubuntu/disks/install/boot/grub/menu.lst /ubuntu/winboot/menu.lst
    /boot/grub/grub.conf    /grub/grub.conf    /grub.conf
    /boot.ini
    /etc/fstab
    /etc/lilo.conf  /lilo.conf
    "

############### List of files whose end point (in GB) will be displayed.
GrubError18_Files="
    boot/grub/menu.lst    grub/menu.lst    menu.lst /NST/menu.lst
    ubuntu/disks/boot/grub/menu.lst
    boot/grub/grub.conf    grub/grub.conf    grub.conf
    grub.cfg    grub/grub.cfg    boot/grub/grub.cfg
    boot/grub/stage2    grub/stage2    stage2
    boot/vmlinuz*  vmlinuz*    ubuntu/disks/boot/vmlinuz*
    boot/initrd*  initrd*    ubuntu/disks/boot/initrd*
    "


#######  Directory containing the script.

Dir=$(cd $(dirname $0);pwd);

########  To avoid overwriting existing files, look for a non-existing file 
########  RESULT.txt RESULTS1.txt  RESULTS2.txt ... 

LogFile=$Dir/RESULTS
while ( [ -e $LogFile$j.txt ] )
    do  
      ((j++))
      wait;
    done
LogFile=$LogFile$j.txt  #### The RESULTS file.

######  Redirect stdout to RESULT File
exec 6>&1   
exec >$LogFile

########### Create previously non-existing  folder of the form
##########  /tmp/BootInfo  /tmp/BootInfo1, /tmp/BootInfo2 ... 

Folder=/tmp/BootInfo
while (! mkdir $Folder$i 2>/dev/null)
    do  
      ((i++))
      wait;
    done
Folder=$Folder$i

cd $Folder

Log1=$Folder/Log1               #  Most of the information which is not part of
                                #the summary is recorded in this file.
Error_Log=$Folder/Error_Log     #  File to catch all unusal Standar Errors 
Trash=$Folder/Trash             #  File to catch all usual Standard Errors
                                #these messagges will not be included in the RESULTS       
Mount_Error=$Folder/Mount_Error # File to catch Mounting Errors
Unknown_MBR=$Folder/Unknown_MBR # File to record all unknown MBR and Boot sectors. 
Tmp_Log=$Folder/Tmp_Log         # File to temporarily hold some information.
PartitionTable=$Folder/PT       #  File to store the Partition   Table
FakeHardDrives=$Folder/FakeHD   # File to list devices which seem to have correspinding drives.
exec 2>$Error_Log               #Redirect all standard error to the file Error_Log

All_Hard_Drives=$(ls /dev/hd? /dev/sd? 2>>$Trash );   ### List of all Hard drives.

####Arrays to informattion about Partition hold the name, starting sector, ending sector, size in sector, Partition Type, Filesystem typw, UUID, Kind( Logical, Primary Extended), Hardrive, boot flag of the paritions.

declare -a NamesArray StartArray EndArray SizeArray TypeArray  FileArray UUIDArray KindArray DriveArray BootArray ParentArray LabelArray SystemArray


#####Arrays to hold information about the hardrives.
declare -a HDName  FirstPartion LastPartition  HDSize HDMBR HDHead HDTrack HDCylinder HDPT HDStart DEnd HDUUID;

PI=-1 ## Counter for the identification number of a partition. (each partition gets unique number)
HI=0 ## Counter for the identification number of a hard drive. (each hardrive gets unique number)
PTFormat='%-10s %4s%14s%14s%14s %3s %s\n';  ### standard format to use for Partition table,
           


##### A function which converts to two digit hexcode of a partition type 
#function HexToSystem() {
#echo $(sfdisk -T 2>>$Trash | grep -e '^[ ]*'$1' ' |  sed 's/[ ]*[^ ]*  //')    
#}
function HexToSystem() {
local type=$1 system
case $type in 
0) system="Empty";;
1) system="FAT12";;
2) system="XENIX root";;
3) system="XENIX usr";;
4) system="FAT16 <32M";;
5) system="Extended";;
6) system="FAT16";;
7) system="HPFS/NTFS";;
8) system="AIX";;
9) system="AIX bootable";;
a) system="OS/2 Boot Manager";;
b) system="W95 FAT32";;
c) system="W95 FAT32 (LBA)";;
e) system="W95 FAT16 (LBA)";;
f) system="W95 Ext d (LBA)";;
10) system="OPUS";;
11) system="Hidden FAT12";;
12) system="Compaq diagnostics";;
14) system="Hidden FAT16 <32M";;
16) system="Hidden FAT16";;
17) system="Hidden HPFS/NTFS";;
18) system="AST SmartSleep";;
1b) system="Hidden W95 FAT32";;
1c) system="Hidden W95 FAT32 (LBA)";;
1e) system="Hidden W95 FAT16 (LBA)";;
24) system="NEC DOS";;
39) system="Plan 9";;
3c) system="PartitionMagic recovery";;
40) system="Venix 80286";;
41) system="PPC PReP Boot";;
42) system="SFS";;
4d) system="QNX4.x";;
4e) system="QNX4.x 2nd part";;
4f) system="QNX4.x 3rd part";;
50) system="OnTrack DM";;
51) system="OnTrack DM6 Aux1";;
52) system="CP/M";;
53) system="OnTrack DM6 Aux3";;
54) system="OnTrackDM6";;
55) system="EZ-Drive";;
56) system="Golden Bow";;
5c) system="Priam Edisk";;
61) system="SpeedStor";;
63) system="GNU HURD or SysV";;
64) system="Novell Netware 286";;
65) system="Novell Netware 386";;
70) system="DiskSecure Multi-Boot";;
75) system="PC/IX";;
80) system="Old Minix";;
81) system="Minix / old Linux";;
82) system="Linux swap / Solaris";;
83) system="Linux";;
84) system="OS/2 hidden C: drive";;
85) system="Linux extended";;
86) system="NTFS volume set";;
87) system="NTFS volume set";;
88) system="Linux plaintext";;
8e) system="Linux LVM";;
93) system="Amoeba";;
94) system="Amoeba BBT";;
9f) system="BSD/OS";;
a0) system="IBM Thinkpad hibernation";;
a5) system="FreeBSD";;
a6) system="OpenBSD";;
a7) system="NeXTSTEP";;
a8) system="Darwin UFS";;
a9) system="NetBSD";;
ab) system="Darwin boot";;
b7) system="BSDI fs";;
b8) system="BSDI swap";;
bb) system="Boot Wizard hidden";;
be) system="Solaris boot";;
bf) system="Solaris";;
c1) system="DRDOS/sec (FAT-12)";;
c4) system="DRDOS/sec (FAT-16 < 32M)";;
c6) system="DRDOS/sec (FAT-16)";;
c7) system="Syrinx";;
da) system="Non-FS data";;
db) system="CP/M / CTOS / ...";;
de) system="Dell Utility";;
df) system="BootIt";;
e1) system="DOS access";;
e3) system="DOS R/O";;
e4) system="SpeedStor";;
eb) system="BeOS fs";;
ee) system="GPT";;
ef) system="EFI (FAT-12/16/32)";;
f0) system="Linux/PA-RISC boot";;
f1) system="SpeedStor";;
f4) system="SpeedStor";;
f2) system="DOS secondary";;
fb) system="VMware VMFS";;
fc) system="VMware VMKCORE";;
fd) system="Linux raid autodetect";;
fe) system="LANstep";;
ff) system="BBT";;
 *) system="Unknown";;
esac;
echo $system;
}

##### Function to convert GPT's Partition Type.
function UUIDToSystem() {
local type=$1 system
case $type in
    00000000000000000000000000000000)  system="Empty";;
    41ee4d02e733d3119d690008c781f39f)  system="MBR partition scheme";;
    28732ac11ff8d211ba4b00a0c93ec93b)  system="System/Boot Partition";;
    a2a0d0ebe5b9334487c068b6b72699c7)  system="Linux (usually)";; 
    6dfd5706aba4c44384e50933c84b4f4f)  system="Linux Swap";;
    16e3c9e35c0bb84d817df92df00215ae)  system="Microsoft Windows";;
    79d3d6e607f5c244a23c238f2a3df928)  system="LVM";;
    005346480000aa11aa1100306543ecac)  system="HFS+";;
                                   *)  system="-";
                                       echo Unknown GPT Partiton Type>>$Unknown_MBR;
                                       echo  $type >>$Unknown_MBR;;   
esac;
echo $system;
   }

##### Function which insert a comma every  third digits of a number
function InsertComma () {
echo $1 |sed -e :a -e 's/\(.*[0-9]\)\([0-9]\{3\}\)/\1,\2/;ta'
}

##### Function to read 4 bytes starting at $1 of device $2 and convert to decimal.


function Read4Bytes () {
echo $(hexdump -v -s  $1  -n 4 -e '4 "%u"'  $2);
}


##### Function to read 8 bytes starting at $1 of device $2 and convert to decimal.

function Read8Bytes () {
local start=$1 device=$2;
local first4 second4;
first4=$(hexdump -v -s  $start  -n 4 -e '4 "%u"'  $device);
second4=$(hexdump -v -s  $((start+4))  -n 4 -e '4 "%u"'  $device);
echo $((second4*1073741824+first4));
}




## Reads and display the  a partition table of an extended partitons    ###########
#############  and check it for errors                       #####################
#  This function can be applied iteratively  to read the extended partiton table           
# Variable 1:  HI of hard drive 
# Variable 2:  Starts Sector of the extended Partition,
# Variable 3:  Number of partitions in table (4 for regular PT, 2 for logical
# Variable 4:  File for storing the partitions table.
# Variable 5:  Format to use for displaying the partition table.  
# Variable 6:  Parent PI (PI of the primary extended partition containing the extended partition.
#              ""  for hard drive)
# Variable 7:  Last Linux Index assigned (the number in sdXY).


ReadPT (){
local HI=$1 StartEx=$2   N=$3 PT_file=$4 format=$5  EPI=$6 Base_Sector  
local   LinuxIndex=$7  boot  size   start end type drive system;
local i=0  boot_hex label limit MBRSig
drive=${HDName[$HI]};
limit=${HDSize[$HI]};
$(dd if=$drive skip=$StartEx of=$Tmp_Log count=1 2>>$Trash);
MBRSig=$(hexdump -v -s 510  -n 2 -e '"%x"'  $Tmp_Log);
[[ "$MBRSig" != "aa55" ]]  && echo  Invalid MBR Signature found >> $PT_file;
if [[ $StartX -lt $limit ]];
then
    [[ "$EPI" = "" ]] && Base_Sector=0 || Base_Sector=${StartArray[$EPI]}
    for (( i=0; i < N; i++ ));
    do
	$(dd if=$drive skip=$StartEx of=$Tmp_Log count=1 2>>$Trash);
        boot_hex=$(hexdump -v -s  $((446+16*i))  -n  1 -e '"%02x"'  $Tmp_Log)
	case $boot_hex  in
	    00) boot=" ";;
	    80) boot="* ";;
	    *) boot="?";;
	esac;
	start=$(hexdump -v -s  $((454+16*i))  -n 4 -e '4 "%u"'  $Tmp_Log);
	size=$(hexdump -v -s  $((458+16*i))  -n 4 -e '4 "%u"'  $Tmp_Log);
	type=$(hexdump -v  -s  $((450+16*i))  -n 1 -e '4 "%x"' $Tmp_Log);
	if  [[ $size != 0 ]];
	then
	    if  [[ ( "$type" = "5" || "$type" = "f" )  && $Base_Sector != 0 ]];
	    then
		start=$((start+Base_Sector))
		ReadPT $HI $start  2  $PT_file "$format"  $EPI $LinuxIndex;
	    else  
		((PI++))  
		if  [[ "$type" = "5" || "$type" = "f" ]];
		then
                    KindArray[$PI]="E";
		else
		    start=$((start+StartEx));
		    [[ $Base_Sector = 0 ]] && KindArray[$PI]="P" || KindArray[$PI]="L";
		fi;
		LinuxIndex=$((LinuxIndex+1));
		end=$((start+size-1));
		[[ "${HDPT[$HI]}"  = "BootIt"  ]] && label="${NamesArray[$EPI]}""_" || label=$drive;
		system=$(HexToSystem $type)

		printf "$format" "$label$LinuxIndex" "$boot" $(InsertComma $start) "$(InsertComma $end)"  "$(InsertComma $size)"  "$type" "$system" >> $PT_file;
		NamesArray[$PI]="$label"$LinuxIndex;
		StartArray[$PI]=$start;
		EndArray[$PI]=$end;
		TypeArray[$PI]=$type;
		SystemArray[$PI]="$system";
		SizeArray[$PI]=$size;
		BootArray[$PI]="$boot";
		DriveArray[$PI]=$HI;
		ParentArray[$PI]=$EPI;

		if [[ "$type" = "5" || "$type" = "f" ]];
		then
                ReadPT $HI $start  2  $PT_file "$format"  $PI 4;
		fi;
	    fi;
       
	elif [[ $Base_Sector != 0  &&  $i = 0  ]];
	then
	    echo "Empty Partition">>$PT_file;
	else 
	    LinuxIndex=$((LinuxIndex+1));
	fi;
    done;
else
    echo "EBR refers to a  location outside the Hard drive" >>$PT_file;
fi;  
}
############### Read partition table of type GPT (GUID, EFI)##########################
######  Variable 1:  HI of hard drive
######  Variable 2:  File to store the PartitionTable
function ReadEFI() {
    local HI=$1 drive file=$2 Size N=0 i=0  format Label PRStart Start End  Type Size System;
    drive="${HDName[$HI]}";
    format='%-10s %14s%14s%14s %s\n';
    printf "$format"  Partition Start End Size  System >> $file;
    HDStart[$HI]=$(Read8Bytes  552   $drive);
      HDEnd[$HI]=$(Read8Bytes  560   $drive);
     HDUUID[$HI]=$(hexdump -v -s 568   -n 16 -e '/1 "%02x"'  $drive); 
         PRStart=$(Read8Bytes  584    $drive);
               N=$(Read4Bytes  592   $drive);
          PRStart=$((PRStart*512));
          PRSize=$(Read4Bytes 596    $drive);
    for (( i = 0; i< N; i++ ))
    do
        Type=$(hexdump -v -s $((PRStart+PRSize*i))  -n 16 -e '/1 "%02x"'  $drive);
    if [ "$Type" != "00000000000000000000000000000000" ];
    then
        ((PI++))
         
	Start=$(Read8Bytes $((PRStart+32+PRSize*i))   $drive);
	  End=$(Read8Bytes $((PRStart+40+PRSize*i))   $drive);
        Size=$((End-Start+1));
        System=$(UUIDToSystem $Type);
        Label=$drive$((i+1));
        printf "$format"  "$Label"  "$(InsertComma $Start)" "$(InsertComma $End)" "$(InsertComma $Size)"  "$System"  >>$file;
        NamesArray[$PI]=$Label;
        StartArray[$PI]=$Start;
        TypeArray[$PI]=$Type;
        SizeArray[$PI]=$Size;
        SystemArray[$PI]=$System;
        EndArray[$PI]=$End;
        DriveArray[$PI]=$HI;
        KindArray[$PI]="P";
        ParentArray[$PI]=""; 
     fi;        
     done;
}



############### Read the Master Partition Table of  BootIt NG##########################
######  Variable 1:  HI of hard drive
######   Variable 2:  File to store the MPT.
function ReadEMBR() {
    local HI=$1 drive MPT_file=$2 Size N=0 i=0  BINGIndex  Label   Start End  Type BINGUnknown format Size System;
    drive="${HDName[$HI]}";
    format='%-18s %4s%14s%14s%14s %3s %-15s %3s %2s\n';
    printf "$format"  Partition Boot Start End Size Id System  Ind "?">> $MPT_file; 
    N=$(hexdump -v -s 534  -n 1 -e  '"%u"' $drive); 
    while [[ $i -lt "$N" ]]
	do
        ((PI++))
        BINGUnknown=$(hexdump -v -s  $((541+28*i))  -n 1 -e '"%x"'  $drive)
	Start=$(hexdump -v -s  $((542+28*i))  -n 4 -e '4 "%u"'  $drive);
	  End=$(hexdump -v -s  $((546+28*i))  -n 4 -e '4 "%u"'  $drive);
	BINGIndex=$(hexdump -v -s  $((550+28*i))  -n 1 -e '"%u"'  $drive);
	Type=$(hexdump -v -s  $((551+28*i))  -n 1 -e '"%x"'  $drive);
        Size=$((End-Start+1));
	Label=$(hexdump -v -s  $((552+28*i))  -n 15 -e '"%_u"'  $drive| sed -e  s/nul[^$]*//);
        System=$(HexToSystem $Type);
        printf "$format"  "$Label" "-" "$(InsertComma $Start)" "$(InsertComma $End)" "$(InsertComma $Size)" "$Type" "$System"  "$BINGIndex" "$BINGUnknown">>$MPT_file;
           NamesArray[$PI]=$Label
           StartArray[$PI]=$Start;
           TypeArray[$PI]=$Type;
           SizeArray[$PI]=$Size;
           SystemArray[$PI]=$System;
           EndArray[$PI]=$End;
           DriveArray[$PI]=$HI;
  
           
            if [[ $Type = "f" || $Type = "5" ]];
	    then
                 KindArray[$PI]="E";
                 ParentArray[$PI]=$PI;
		 ReadPT $HI  $Start  2  $MPT_file "$format"  $PI  4 ;  
            else
                KindArray[$PI]="P";
                ParentArray[$PI]="";
	    fi;
         ((i++))
         
	done;
}

#################   Check partition table for errors  ################################
###  
###  This function checks whether any two partitions  overlap.
###  and the logical partitions are inside the extended parition.
###  Variable 1:        First partition to consider
###  Variable 2:        Last Partition to consider
###  Variable 3:        File for the error messages.
###  Variable 4:        HI of containing hard drive
 CheckPT () {
    local  first=$1 last=$2 file=$3;  hi=$4;
    local  Si Ei Sj Ej Ki  Kj i j k cyl track head cyl_bound sec_bound
    cyl=${HDCylinder[$hi]};
    track=${HDTrack[$hi]};
    head=${HDHead[$hi]};
    cyl_bound=$((cyl*track*head));
    sec_bound=${HDSize[$hi]};
    for (( i=$first; i <= last; i++ ));
    do
         Si=${StartArray[$i]};
         Ei=${EndArray[$i]};
         Ki=${KindArray[$i]};
         Ni=${NamesArray[$i]};
         if [[ "$Ei" -gt "$sec_bound"  ]];
	 then
	     echo $Ni  ends after the last sector of ${HDName[$hi]}>>$file;
         elif  [[ "$Ei" -gt "$cyl_bound"  ]]
	 then
	     echo $Ni ends after the last cylinder of ${HDName[$hi]}>>$file;
         fi;
         if [[ $Ki = "L" ]];
	 then
	     k=${ParentArray[$i]};
            Sk=${StartArray[$k]};
            Ek=${EndArray[$k]};
            Nk=${NamesArray[$k]};
            [[ $Si -le $Sk || $Ei -gt $Ek ]] &&  echo  the logical partition  $Ni is not contained in the extended partition  $Nk>>$file;
         fi;
         for (( j = i+1; j <= last; j++ ));
	 do 
            Sj=${StartArray[$j]};
            Ej=${EndArray[$j]};
            Kj=${KindArray[$j]};
            Nj=${NamesArray[$j]};
            [[ !( ( $Ki = "L" && $Kj = "E"  )  || ( $Ki = "E" && $Kj = "L"  ) ) && ( ( $Si -lt $Sj &&   $Sj  -lt $Ei )  || ($Sj  -lt $Si && $Si -lt $Ej ) )]] && echo   $Ni overlaps with   $Nj >>$file;
          done;
    done
}


#############################################################################################
##########  Determine the embeded location of stage 2  in a stage 1 file,
##########  look  for the stage 2 and, if found, determine the
#########$  the location and the path of the embedded menu.lst

stage2_loc (){
  local stage1=$1 hi;
  offset=$(hexdump -v -s 68 -n 4 -e '4 "%u"' $stage1 2>>$Trash);
  dr=$(hexdump -v -s 64 -n 1 -e '"%d"' $stage1);
  pa="T"
  Grub_Version="";
  for hi in ${!HDName[@]};
  do
     hdd=${HDName[$hi]};
     if [ $offset -lt  ${HDSize[hi]}  ];
     then
	 tmp=$(dd if=$hdd skip=$offset count=1 2>>$Trash | hexdump -v    -n 4 -e '"%x"');
         if [[ "$tmp" = 3be5652 || "$tmp" =  bf5e5652  ]];  ###  If stage2 files was found.
         then
              dd if=$hdd skip=$((offset+1)) count=1 of=$Tmp_Log 2>>$Trash;
              pa=$(hexdump -v  -s 10  -n 1 -e '"%d"' $Tmp_Log);
              stage2_hdd=$hdd;
              Grub_String=$(hexdump -v -s 18 -n 94 -e '"%_u"' $Tmp_Log);
              Grub_Version=$(echo $Grub_String|sed -e  s/nul[^$]*//);
              BL=$BL$Grub_Version;
              menu=$(echo $Grub_String |sed -e  s/[^\/]*// -e s/nul[^$]*//);
              menu=${menu%% *};
         fi;
     fi;
 done;
 dr=$((dr-127))
 Stage2_Msg=$(echo  looks at sector $offset )        
 if [ "$dr" = 128 ];
 then
      Stage2_Msg=$(echo $Stage2_Msg of the same hard drive) 
 else
      Stage2_Msg=$(echo $Stage2_Msg on boot drive \#$dr)
 fi;
 Stage2_Msg=$(echo $Stage2_Msg for the stage2 file);
                    
 if [ "$pa" = "T"  ]   #### no stage 2 file found.
 then
      Stage2_Msg=$(echo $Stage2_Msg, but no stage2 files can be found at this location.); 
 else
     pa=$((pa+1))
     Stage2_Msg=$(echo $Stage2_Msg.  A stage2 file is at  this location on $stage2_hdd.  Stage2 looks on )                       
     if [ "$pa" = 256 ];
     then
         Stage2_Msg=$(echo $Stage2_Msg the same partition) 
     else
         Stage2_Msg=$(echo $Stage2_Msg  partition \#$pa )
     fi;
     Stage2_Msg=$(echo $Stage2_Msg for  $menu.)
  fi;
}
#######################################################################################

#############################################################################################
##########  Determine the embeded location of core.img  for a Grub2 stage1 file,
##########  look  for the core.img and,  the path of the Grub Folder.
#############################################################################

core_loc (){
  local stage1=$1  hi;
  offset=$(hexdump -v -s 68 -n 4 -e '4 "%u"' $stage1 2>>$Trash);
  dr=$(hexdump -v -s 76 -n 1 -e '"%d"' $stage1);
  pa="T"
    for hi in ${!HDName[@]};
  do
     hdd=${HDName[$hi]};
     if [ $offset -lt  ${HDSize[hi]}  ];
     then
	 tmp=$(dd if=$hdd skip=$offset count=1 2>>$Trash | hexdump -v    -n 4 -e '"%x"');
         if [ "$tmp" = 1bbe5652 ];  ###  If conf.img  file was found.
         then
              dd if=$hdd skip=$((offset+1)) count=1 of=$Tmp_Log 2>>$Trash;
              pa=$(hexdump -v  -s 20  -n 1 -e '"%d"' $Tmp_Log);
              core_hdd=$hdd;
	      Grub_String=$(hexdump -v -s 32 -n 64 -e '"%_u"' $Tmp_Log);
              Core_Dir=$(echo  $Grub_String | sed s/nul[^$]*//);
         fi;
     fi;
 done;
 dr=$((dr-127))
 Core_Msg=$(echo  looks at sector $offset )        
 if [ "$dr" = 128 ];
 then
      Core_Msg=$(echo $Core_Msg of the same hard drive) 
 else
      Core_Msg=$(echo $Core_Msg on boot drive \#$dr)
 fi;
 Core_Msg=$(echo $Core_Msg for core.img);
                    
 if [ "$pa" = "T"  ]   #### core.img  found.
 then
      Core_Msg=$(echo $Core_Msg, but core.img can not be found at this location.); 
 else
     pa=$((pa+1))
     Core_Msg=$(echo $Core_Msg  and on )                       
     if [ "$pa" = 256 ];
     then
         Core_Msg=$(echo $Core_Msg the same partition) 
     else
         Core_Msg=$(echo $Core_Msg  partition \#$pa )
     fi;
     Core_Msg=$(echo $Core_Msg for  $Core_Dir.)
  fi;
}
#######################################################################################


## "titlebar_gen" generates the $name$file title bar to always be either 79 or 80 chars total in length:
titlebar_gen () {
		name_file="$1$2:"; name_file_length=${#name_file}
		equal_signs_line_length=$(((80-name_file_length)/2-1)); equal_signs_line=""
		for length in $(seq $equal_signs_line_length); do
  			equal_signs_line='='$equal_signs_line
		done;
                echo >> $Log1;
		echo "$equal_signs_line $name_file $equal_signs_line" >> $Log1;
                echo >> $Log1;
                }



echo '============================= Boot Info Summary: =============================='; echo

#####   Search  for  hard drives which don't exists   or have a  corrupt partition table
#####   All hard drives which a valid partition table are stored   in $Hard_Drives
for drive in  $All_Hard_Drives;
do
        size=$(fdisk -s $drive 2>>$Trash);        
        if [ 0 -lt $size 2>>$Trash ];
	then
            size=$((2*size));
            Hard_Drives=$Hard_Drives" "$drive;
            HDName[$HI]=$drive;
            HDSize[$HI]=$size;
            geometry=$(fdisk  -lu $drive 2>>$Trash | grep "head");
            HDHead[$HI]=$(echo $geometry | awk '{print $1}');
            HDTrack[$HI]=$(echo $geometry | awk '{print $3}');
            HDCylinder[$HI]=$(echo $geometry | awk '{print $5}');
 ###Look at the first 4 bytes of the second sector to identify type of partition table;
            case $(hexdump -v -s 512 -n 4 -e '"%_u"' $drive) in
            "EMBR")  HDPT[$HI]="BootIt";;
            "EFI ")  tmp=$(hexdump -v -s 450 -n 1 -e '"%x"' $drive);
                    [[ "$tmp" = "ee" ]] && HDPT[$HI]="EFI" || HDPT[$HI]="MSDos";;
                 *)  HDPT[$HI]="MSDos";;
            esac; 
            HI=$((HI+1));
            
        else
            echo " $(basename $drive) .">> $FakeHardDrives
	fi;
done;
############ Identify the MBR of each  hard drive.
echo "Identifying MBRs..." >&6;
for hi in ${!HDName[@]};
  do 
    drive="${HDName[$hi]}";
    Message=$(echo is installed in the MBR of $drive)
    case $(hexdump -v -n  2 -e '/1 "%x"' $drive) in   ####Look at the first two bytes of the hard drive  to identify the boot code installed in the MBR
 
################################ If Grub is in the MBR   #########################

	eb48) offset=$(hexdump -v -s 68 -n 4 -e '"%u"' $drive);### 0x44 contains the offset of the next stage
              if  [ "$offset" != 1 ];   ###if  Grub is installed without stage1.5 files 
	      then
                  stage2_loc $drive;
                  Message=$(echo $Message and  $Stage2_Msg)
 	      else                         ### if grub is installed with stage1.5 files
                  Grub_String=$(hexdump -v -s 1042 -n 94 -e '"%_u"' $drive);
                  Grub_Version=${Grub_String%%nul*};
                  tmp='/'${Grub_String#*/};
                  tmp=${tmp%%nul*};
                  stage=$(echo $tmp| awk '{print $1}');
                  menu=$(echo $tmp| awk '{print $2}');
                  [[ "$menu" = "" ]] || stage=$(echo $stage and $menu);
                  part_info=$((1045 + ${#Grub_Version}));
	          pa=$(hexdump -v -s $part_info  -n 1 -e '"%d"' $drive);
                  part_info=$((part_info+1));
                  dr=$(hexdump -v -s $part_info -n 1 -e '"%d"' $drive);
                  dr=$((dr-127));
		  pa=$((pa+1));
		  if [ $dr = 128 ];
                  then
                       Message=$(echo $Message and looks on the same drive in partition \#$pa for $stage.)
                  else
                      Message=$(echo $Message and looks  on boot drive \#$dr in partition \#$pa for $stage.)
              fi;
	    fi;
              BL=Grub$Grub_Version;;
###############################  If Grub2 is in the MBR   #####################################

        eb4c) BL=Grub2;
              offset=$(hexdump -v -s 68 -n 4 -e '"%u"' $drive);### 0x44 contains the offset of the next stage
              if  [ "$offset" != 1 ];   ###if  Grub2 is  installed without  Core. 
	      then
                  core_loc $drive;
                  Message=$(echo $Message and  $Core_Msg)
 	      else                      ### if Grub2  is installed with Core
                  Grub_String=$(hexdump -v -s 1056 -n 64 -e '"%_u"' $drive);
                  Core_Dir=$(echo  $Grub_String | sed s/nul[^$]*//);
	          pa=$(hexdump -v -s 1044  -n 1 -e '"%d"' $drive);
                  dr=$(hexdump -v -s 77  -n 1 -e '"%d"' $drive);
                  dr=$((dr-127));
		  pa=$((pa+1));
		  if [ $dr = 128 ];
                  then
                       Message=$(echo $Message and looks on the same drive in partition \#$pa for $Core_Dir.)
                  else
                      Message=$(echo $Message and looks  on boot drive \#$dr in partition \#$pa for $Core_Dir.)
              fi;
	    fi;;
############################################################################################## 
 	33c0) BL=Windows;;
	fa31) BL=Syslinux;;
	faeb) BL=Lilo;; 
	fc31) BL=Testdisk;;
        fc33) BL=Gag;;
	eb5e) BL=Grub4Dos;;
	b800) BL=Plop;;
	33ff) BL='HP/Gateway';;
         ebe) BL=ThinkPad;;
        fa33) BL="No boot loader";; 
        fabe) BL="No boot loader?";;
        fab8) BL="No boot loader";;   
	fceb) BL="BootIt NG";;
              #PT_Kind="BootIt";
              #PT_Location=$hi;;
          00) BL="No boot loader";;
	   *) BL="No known boot loader"
              echo "Unknown MBR on $drive" >> $Unknown_MBR;
              echo >> $Unknown_MBR;
              hexdump -v -n 512 -C $drive >> $Unknown_MBR;
              echo >> $Unknown_MBR;;
        esac;
        ##Output message at beginning of summary that gives MBR info for each drive:
        echo -n " => "
        echo "$BL $Message" | fold -s -w 75 | sed -e '2~1s/.*/    &/'   
        HDMBR[$hi]=$BL;
    done
    echo;
######################################################################################
#############   Store and Display all the partitions tables.##########################
for HI in ${!HDName[@]};
    do
    drive=${HDName[$HI]};
    echo "Computing Partition Table of $drive..." >&6;
    FirstPartition[$HI]=$((PI+1))
    echo "Drive $(basename $drive ): _____________________________________________________________________" >>$PartitionTable;
    fdisk  -lu $drive 2>>$Trash |sed '/omitting/ d'|sed '6,$ d' >>$PartitionTable;
    echo >>$PartitionTable;
    PTType=${HDPT[$HI]};
    case $PTType in
      BootIt) ReadEMBR  $HI $PartitionTable;;
	 EFI) ReadEFI  $HI $PartitionTable;;
	   *) printf "$PTFormat" "Partition" "Boot" "Start" "End"  "Size"  "Id" "System">>$PartitionTable;
echo >>$PartitionTable;
              ReadPT $HI 0  4 $PartitionTable "$PTFormat" "" 0;;
    esac;    
    echo >>$PartitionTable;
    LastPartition[$HI]=$PI;
    CheckPT  ${FirstPartition[$HI]} ${LastPartition[$HI]}  $PartitionTable $HI;
    echo >>$PartitionTable;
done;

for hi in ${!HDName[@]};  ############Loop through all Hard Drives
 do
 drive=${HDName[$hi]}
for (( pi = FirstPartition[$hi]; pi <= LastPartition[$hi]; pi++ ));  ## And then loop through                                                                      ###the partition  on that drive
do
      BSI="";
      BFI="";    
      part_type=${TypeArray[$pi]};  #### Type of the partition according to fdisk
      start=${StartArray[$pi]};
      size=${SizeArray[$pi]};
      end=${EndArray[$pi]};
      kind=${KindArray[$pi]};
      if [[ "${HDPT[$hi]}" = "BootIt" ]];
      then
          name="${NamesArray[$pi]}";
          mountname=$(basename $drive)$pi;
          part=$(losetup -f --show  -o $((start*512)) --sizelimit $((size*512)) $drive)
      else
          part=${NamesArray[$pi]};
          name=$(basename $part);  ####  Name of the partition (/dev/sda8 -> sda8)
        
          mountname=$name;      
fi;
       echo "Searching $name for information..." >&6;
       type=$(blkid -c /dev/null -s TYPE $part 2>$Tmp_Log);  ##### type of file system according to blkid
       type=${type#*=\"};
       type=${type%\"*};
       FileArray[$pi]=$type;
       # part_number=${part:8} 

      echo $name: _________________________________________________________________________; echo
      mkdir "$mountname"    ####  Directory where the partition will be mounted.
      if [[ "${KindArray[$pi]}" = "E"  &&  "$type" = "" ]] ;  #### Check for extended partion.
         then
	 type="Extended Partition";
	 cat $Tmp_Log>>$Trash;  ### Don't display  the error message from blkid for extended partition
	 else
         cat $Tmp_Log>>$Error_Log
      fi;
      echo "    File system:       "$type;  ### Display the File System Type

     
          Bytes8081=$(hexdump -v -s 128 -n  2 -e '/1 "%x"'  $part)   #### Use bytes 0x80,81 to idendtify Boot sectors
          case    $Bytes8081    in
             8cd) BST="Windows XP";;
            b6d1) BST="Windows XP: Fat32";;
            fa33) BST="Windows XP";;
	    55aa) BST="Windows Vista";;
            e9d8) BST="Windows Vista";;
             10f) BST="HP Recovery";;
            3a5e) BST="Recovery:Fat 32";;
            89e)  BST="MSDOS5.0: Fat 16";;
            bd0)  BST="MSWIN4.1: Fat 32";;
            6f6e) BST="-";;  #MSWIN4.1: Fat 32"
            7cc6) BST="MSWIN4.1: Fat 32";;
            745)  BST="Vista:  Fat 32";;
            19d)  BST="BSD4.4: Fat32";;
 b60 | 211 | e00) BST="Dell Utility: Fat16";; 
            8ed0) BST="DEll Recovery: Fat32";;
            4445) BST="DEll Restore: Fat32";; 
            6974) BST="BootIt: Fat16";;
            6f65) BST="BootIt: Fat16";;
            7cc6) BST=Win_98;;
            734)  BST=Dos_1.0;;
            2d5e) BST=Dos_1.1;;
	    7815) BST=Fat32;;
            6f74) BST=Fat32;;
            696e) BST=Fat16;;
            6616) BST=Fat16;;
     ####### if Grub, Grub 2 or Lilo  is  in the boot sector,  ########
     ####### investigate the embedded information              ########
            48b4) BST=Grub2;    
                  core_loc $part;
                  BSI=$(echo $BSI Grub2 is installed in the boot sector of $name  and $Core_Msg);;
     aa75 | 5272) BST=Grub;
                  stage2_loc $part;
                  BSI=$(echo $BSI Grub$Grub_Version is installed in the boot sector of $name  and $Stage2_Msg);;
     #############  If Lilo look for map file  ##############################################

 	     8053) BST=LILO;
                   offset=$(hexdump -v -s 32 -n 4 -e '"%u"' $part);  ### 0x20-23 contains the offset
                                                                    #####  of  /boot/map         
                   BSI=$(echo $BSI" "LILO  is installed in boot sector of $part and looks at sector $offset of $drive for the \"map\"  file,); 
                   if [ $offset -lt  $size ];   ### check whether offset
                                                                    #### is on the had drive.
                   then
	                 tmp=$(dd if=$drive skip=$offset count=1 2>>$Trash | hexdump -v -s 508  -n 4 -e '"%_p"');                     
                         if [[ "$tmp" = "LILO" ]];
			 then
			     BSI=$(echo $BSI" "and the \"map\" file was found at this location.);
	                 else
                             BSI=$(echo $BSI" "but the \"map\" file was not found at this location.);
                         fi;
                    else
                        BSI=$(echo $BSI" "but the \"map\" file was not found at this location.);
                    fi;;
     #########################################################################################

              00)   sig2=$(hexdump -v -s 128 -n  2 -e '/1 "%x"'  $part)
                      if [ "$sig2" = 00 ];    #### If the first two bytes are zero, the boot sector does not contain any boot loader.
		      then
                      BST="-";
		      else           ###### Otherwise, display the boot sector, so we that we might identify it and add it to the list of known boot sectors.
		      BST="Unknown"
                      echo "Unknown BootLoader  on $name" >> $Unknown_MBR;
                      echo >> $Unknown_MBR;
                      hexdump  -n 512 -C $part >> $Unknown_MBR;
                      echo >> $Unknown_MBR;
                  fi;;
                *) BST="Unknown"
                   echo "Unknown BootLoader  on $name" >> $Unknown_MBR;
                   echo >> $Unknown_MBR;
                   hexdump -n 512 -C $part >> $Unknown_MBR;
                   echo >> $Unknown_MBR;
            esac;
######################   Display the boot sector type.
           echo "    Boot sector type:  "$BST  

####################### Investigate the Boot Parameter Block of an NTFS partition.

           if [[ "$type" = "ntfs" ]]
           then
           offset=$(hexdump -v -s 28 -n 4 -e '"%u"' $part);
           BPB_Part_Size=$(hexdump -v -s 40 -n 4 -e '"%u"' $part)
           Comp_Size=$(( (BPB_Part_Size - size)/256 ))
           SectorsPerCluster=$(hexdump -v -s 13 -n 1 -e '"%d"' $part);
           MFT_Cluster=$(hexdump -v -s 48 -n 4 -e '"%d"' $part);
           MFT_Sector=$(( MFT_Cluster * SectorsPerCluster ));
         #  Track=$(hexdump -v -s 24 -n 2 -e '"%u"' $part)''  ### Number of sectors per track.
         #  Heads=$(hexdump -v -s 26 -n 2 -e '"%u"' $part)''  ### Number of heads
         #  if [[ "$Heads" != 255  || "$Track" != 63 ]]
	 #  then
         #     BSI=$(echo $BSI" "Geometry: $Heads Heads and $Track sectors per Track.)
	 #  fi;           
           if [[ "$MFT_Sector" -lt "$size" ]];
           then
               MFT_FILE=$(dd if=$part skip=$MFT_Sector count=1 2>>$Trash | hexdump -v    -n 4 -e '"%_u"');
              MFT_MFT=$( dd if=$part skip=$MFT_Sector count=1 2>>$Trash| hexdump -v -e '4/1 "%x"' | grep "432404d046054")
               
	   else 
               MFT_FILE="";
               MFT_MFT="";
           fi;
           MFT_Mirr_Cluster=$(hexdump -v -s 56 -n 4 -e '"%d"' $part);
           MFT_Mirr_Sector=$(( MFT_Mirr_Cluster * SectorsPerCluster ));
           if [[ "$MFT_Mirr_Sector" -lt "$size" ]];
           then
           MFT_Mirr_FILE=$(dd if=$part skip=$MFT_Mirr_Sector count=1 2>>$Trash | hexdump -v    -n 4 -e '"%_u"');
  
           MFT_Mirr_MFT=$(dd if=$part skip=$MFT_Mirr_Sector count=1 2>>$Trash |hexdump -v -e '4/1 "%x"' | grep "432404d046054")
           else 
               MFT_Mirr_FILE="";
               MFT_Mirr_MFT="";
           fi;
           if [[ "$offset" = "$start"  && "$MFT_FILE" = "FILE"  &&  "$MFT_MFT" != "" && "$MFT_Mirr_FILE" = "FILE"  &&  "$MFT_Mirr_MFT" != "" && "$Comp_Size" = "0"  ]];
	    then
	       BSI=$(echo $BSI" "No errors found in the  Boot Parameter Block.);
           else
	    if [[ "$offset" != "$start" ]] 
            then
                BSI=$(echo $BSI"  "According to the info in the boot sector, $name starts at sector $offset.)
                if [[ "$offset" != "63" && "$offset" != "2048"  ||  "$kind" != "L" ]]
                then
                    BSI=$(echo $BSI" "But according to the info  from fdisk, $name starts at sector   $start.);
                 fi;
            fi;
            if  [[ "$MFT_FILE" != "FILE"  ||  "$MFT_MFT" = "" ]]; 
	    then 
                BSI=$(echo $BSI" "The info in boot sector  on  the starting sector of the MFT is wrong.);
                echo MFT Sector of $name >> $Unknown_MBR;
                echo >> $Unknown_MBR
                dd if=$part skip=$MFT_Sector count=1 2>>$Trash| hexdump -C >>$Unknown_MBR;
             fi;
             if [[ "$MFT_Mirr_FILE" != "FILE"  ||  "$MFT_Mirr_MFT" = "" ]];
	     then
		 BSI=$(echo $BSI" "The info in the boot sector on  the starting sector of the MFT Mirror  is wrong.);
             fi;

             if  [[ "$Comp_Size" != "0"  ]];
             then  
                   BSI=$(echo $BSI"  "According to the info in the boot sector, $name has    $BPB_Part_Size sectors, but according to the info  from fdisk, it has  $size sectors.);
             fi;
           fi;
          fi;

######################## Investigate the Boot Parameter Block (BPB)of some Fat partitions
 #####  Identifies Fat Bootsectors which are used for booting.

##  if [[ "$Bytes8081" = "7cc6" ||  "$Bytes8081" = "7815"  ||  "$Bytes8081" = "B6D1"  || "$Bytes8081" =  "7405" || "$Bytes8081" = "6974" || "$Bytes8081" = "bd0" ||  "$Bytes8081" =  "89e"  ]] ;

        if [[ "$type" = "vfat" ]];
           then
           offset=$(hexdump -v -s 28 -n 4 -e '"%d\n"' $part); #### Starting sector the partition  according to BPP
           BPB_Part_Size=$(hexdump -v -s 32 -n 4 -e '"%d"' $part); ### Partition Size in sectors accoring to BPB 
           Comp_Size=$(( (BPB_Part_Size - size)/256 )) ### This number will be unequal to zero  if the two partions size  differ by more than 255 sectors.  
           #Track=$(hexdump -v -s 24 -n 2 -e '"%u"' $part)''  ### Number of sectors per track.
           #Heads=$(hexdump -v -s 26 -n 2 -e '"%u"' $part)''  ### Number of heads
           #if [[ "$Heads" != 255  || "$Track" != 63 ]] ###  Checks for an usual geometry. 
	   #then
           #   BSI=$(echo $BSI" "Geometry: $Heads Heads and $Track sectors per Track.)  ### Report unusal geometry
	   #fi;     
           if [[ "$offset" = "$start" && "$Comp_Size" = "0"  ]];  ### Check whether Partitons starting sector  and  the Partition Size of BPB and fdisk agree. 
	    then
	       BSI=$(echo $BSI" "No errors found in the  Boot Parameter Block.);  ##If they agreee
	    else      ######   if they  don't agree
            if [[ "$offset" != "$start" ]]   ###  if partition starting sector disagree 
            then
                BSI=$(echo $BSI"  "According to the info in the boot sector, $name starts at sector $offset.)   ### display the starting sector accoding to BPB
                if [[ "$offset" != "63" && "$offset" != "2048" ||  "$kind" != "L" ]]  ### check whether partition is logcial partition and starting sector is a 63.
                then  ### if not, display starting sector according to fdisk.
                    BSI=$(echo $BSI" "But according to the info  from fdisk, $name starts at sector   $start.);
                fi; ### If not, don't display.  (This is quite common occurence, and only matters if one tries to boot Windows from a logical partition. So I decided not to display a warning message in this case. 
            fi;  
#### If Partition sizes from BPB and FDISK differ by more than 255 sector, display both sizes.       
            if [[ "$Comp_Size" != "0"  ]];
            then    
		BSI=$(echo $BSI"  "According to the info in the boot sector, $name has    $BPB_Part_Size sectors.)
                if [[ "$BPB_Part_Size" != 0 ]];
                then 
                BSI=$(echo "$BSI"." " But according to the info  from the partition table , it has  $size sectors.);
                fi;  ## Don't display warning message in the common case BPB_Part_Size=0. 
            fi; 
              
            fi;   #### End of BPB Error if then else 
          fi;   ###### End of Investigation of the BPB of vfat partitions. 
################################################################################################
      #####  Display boot sector info
      echo -n "    Boot sector info:  "
      echo $BSI | fold -s -w 55 |  sed -e '2~1s/.*/                       &/'

      ####Exclude Partitions which contain no information,     #########
      ##### or which we (currently) don't know how to  accces. #########  
      if [ "$type" != "swap" ]  && [ "$type" != "Extended Partition"  ] && [ "$type" != "unknown volume type" ] && [ "$type" != "LVM2_member" ]  && [ "$type" != "linux_raid_member" ] && [ "$type" != "crypto_Luks" ] ; 
      then     
 
         CheckMount=$(mount| grep "$part ");
         CheckMount=${CheckMount% type*};
         CheckMount=${CheckMount#* on };   
          ### Check wether partition is already mounted
         [[ "$CheckMount" != "" ]]  &&  mountname=$CheckMount;  #### if yes,use existing mount point.
         if  [ "$CheckMount" != "" ] || mount -t "$type" $part "$mountname" 2>$Mount_Error  || ( [ $type = ntfs ] && ntfs-3g  $part "$mountname" 2>>$Mount_Error  ) ;     ####### Try to mount partition
         then     ############  if partition is  mounted.
         #####Try to identify the Operating  System (OS) by  looking for files specific to the OS
       OS=""
       [ -e "$mountname/Windows/System32/config/BCD-Template" ] ||  [ -e "$mountname/windows/system32/config/bcd-template" ] || [ -e "$mountname/WINDOWS/System32/config/BCD-Template" ] ||
  [ -e "$mountname/WINDOWS/system32/config/BCD-Template" ] && OS="Windows Vista"

       [ -e "$mountname/Windows/System32/config/SecEvent.Evt" ] ||  [ -e "$mountname/WINDOWS/system32/config/SecEvent.Evt" ] || [ -e "$mountname/WINDOWS/system32/config/secevent.evt" ] || [ -e "$mountname/windows/system32/config/secevent.evt" ] && OS="Windows XP"
  
     [ -e "$mountname/etc" ] && OS=$(sed -e 's/\\. //g' -e 's/\\.//g' -e 's/^[ \t]*//' "$mountname"/etc/issue)
     
 ####################################  search for  the files in $Bootfiles   ########################
###################################### and if found, display there contained ########################
       BootFiles=""    
       for file in $Boot_Files;
       do
           if [ -f "$mountname"$file ];
              then BootFiles=$(echo $BootFiles"  "$file);
              if ! [ -h "$mountname"$file ];  ### check whether file is  symlink
              then
                 titlebar_gen "$name" $file	##generates a titlebar above each file/dir listed
                 cat "$mountname"$file >> $Log1;  ### if not a symlink, display content.
              fi;
	   fi;
       done;
#################################### Search for the programs in $Boot_Prog, ###############
################################### if found disply where names.           ###############

       for file in $Boot_Prog;   
       do
           if [ -f "$mountname"$file ];
              then BootFiles=$(echo $BootFiles"  "$file);          
	   fi;
       done;


################### Search for the directories related to Booting ########################
##################, if found display the list of files             #######################

#       for file in $Boot_Dir;  #directories in that directory.
#       do
#          if [ -d "$mountname"$file ];
#          then
#	      BootFiles=$(echo $BootFiles"  "$file); 
#              titlebar_gen "$name" $file	##generates a titlebar above each file/dir listed
#              ls -la  "$mountname"$file >> $Log1 ; 
#             
#	  fi;
#       done;

####################  Search for files containing boot codes #################################

       for file in $Boot_Codes_Dir    #####  loop through all directories which might conatin boot_code files
       do
	   if [ -d "$mountname"$file ];   ##### if such directory exits
	   then  
	       for loader in $( ls  "$mountname"$file );  ##### look at the content of that directory 
	       do
                  if [ -f "$mountname"$file$loader ];  ####  it its a file
		  then		     
                      sig=$(hexdump -v -s 257 -n 8  -e '8/1 "%_p"' "$mountname"$file$loader);
                      if [ "$sig"  = "BootPart" ]    ##### Bootpart code has "BootPart" written at0x101
		      then
                          offset=$(hexdump -v -s 241 -n 4 -e '"%d"' "$mountname"$file$loader);
                              dr=$(hexdump -v -s 111 -n 1 -e '"%d"' "$mountname"$file$loader);
			      dr=$((dr -127))
 			  BFI=$(echo $BFI "  "BootPart in the file $file$loader is trying to chain load sector \#$offset on boot drive \#$dr);
		      fi;
		      sig=$(hexdump -v -s 383 -n 4  -e '4/1 "%_p"' "$mountname"$file$loader);
                      if [ "$sig"  = "GRUB" ];   ##### Grub and Grub2  have "Grub" written at 0x17f
                      then
                          sig2=$(hexdump -v -n  2 -e '/1 "%x"' "$mountname"$file$loader);
                          if [[ "$sig2" = "eb48" ]] ### distinguish Grub and Grub 2 by the
                                                    ##### first two bytes.
                          then
                               stage2_loc  "$mountname"$file$loader;
                               BFI=$(echo $BFI" "Grub$Grub_Version in the file  $file$loader $Stage2_Msg);
                          else 
                               core_loc  "$mountname"$file$loader;
                               BFI=$(echo $BFI" "Grub2  in the file  $file$loader $Core_Msg); 
                          fi;    
                      fi;
                      
 		  fi;
	        done; ## End of loop through the files in a particular  Boot_Code_Directory
            fi;
        done   ## End of the loop through the Boot_Code_Directories.

######### Determine the end point of all files in the GrubError18_Files list
    
     echo >$Tmp_Log;
     counter=0;
     cd "$mountname";
     for file in $(ls $GrubError18_Files 2>>$Trash);
     do
     if [[ -f $file ]]
     then 
	 BlockSize=$(filefrag -v $file| grep "Blocksize" |awk '{print $6}');
	 LastBlock=$(filefrag -v $file| grep "Last block"  |awk '{print $3}');
	 EndGB=$(echo $(((BlockSize*LastBlock + 512*start)/100000000 ))|sed 's/\(.\)$/\.\1/')
	 printf "%6sGB: %-s\n" $EndGB "$file" >>$Tmp_Log;
         ((counter++)); 
     fi;
     done;
     cd $Folder;
     if [ $counter != 0 ];
     then
	  titlebar_gen "$name"  ": Location of files loaded by Grub";
          cat $Tmp_Log>>$Log1;
     fi;
     echo >$Tmp_Log;

      if [[ $BFI != "" ]];
      then
          echo -n "    Boot file info:     "
          echo $BFI | fold -s -w 55 |  sed -e '2~1s/.*/                       &/'
      fi;
      echo "    Operating System:  "$OS | fold -s -w 55 | sed -e '2~1s/.*/                       &/'     
      echo -n "    Boot files/dirs:   "
      echo $BootFiles | fold -s -w 55 |  sed -e '2~1s/.*/                       &/'
     
        if [ "$CheckMount" = "" ];  ## if partition was mounted by the script
        then
           umount "$mountname" || umount -l "$mountname"; 
        fi;
     else     ############### if partition failed to mount  
       echo "    Mounting failed:";  
     cat $Mount_Error 
     fi;  ### end of Mounting "if then else"
     fi;  ### end of Partition Type "if then else"
     echo;
     [[ "${HDPT[$hi]}" = "BootIt" ]] && losetup -d $part;
     done;  ### end of partition loop
     done;  ### end of hard drive loop



echo '=========================== Drive/Partition Info: ============================='; echo
 
[ -e $PartitionTable ] && cat $PartitionTable || echo no valid partition table found ;

echo "blkid -c /dev/null: ____________________________________________________________";
echo; blkid -c /dev/null
echo;
echo '=============================== "mount" output: ===============================';
echo; mount
echo >> $Log1

#################   Write the content of Log1 to the RESULTS file
cat $Log1  

if [ -e $Unknown_MBR ]; 
then
 echo "=========================== Unknown MBRs/Boot Sectors/etc =======================";
 echo;
 cat $Unknown_MBR;
 echo
fi;

if [ -e $FakeHardDrives ];
then 
 echo "=======Devices which don't seem to have a corresponding hard drive==============";
 echo;
 cat $FakeHardDrives;
 echo;
fi;
  

#####################  Write the Error Log to the RESULT file
if [ -s $Error_Log ];
then
    echo "=============================== StdErr Messages: ===============================";
    echo;
    cat $Error_Log;
fi;

#####   Make the  user the owner of Result file
chown $(basename ~) $LogFile    

#######  Reset the Standard Output to the Terminal 
exec 1>&-
exec 1>&6
exec 6>&-

echo Finished. The results are in the file $(basename $LogFile) located in $Dir
exit


```

By the way, menu.lst does not exist.

I've tried to install grub using sudo grub and setting it to the place shown when found, but that still gives me an error 17 prior to seeing grub.

I'm going to try to use the old menu.lst if I can find the uid stuff for the drive I know I'm got Ubuntu mounted on, I guess.


*EDIT: no go. Ran xp disk, did a fixmbr, it booted straight into windows. Did the grub fix; nothing. Reinstalling ubuntu and trying again, lol.

It's all good, I was wiping out partitions and redoing everything anyway and had just reinstalled ubuntu. Probably messed up my mbr when I was doing stuff, but I made sure I stayed away from the xp partition. I guess that wasn't good enough.

*SECOND EDIT: That didn't work, even with setting grub again. It's finding it on hd1,0, but setup (hd1) does not do any good (read on for why I think this is a problem). I did however look at the Advance tab on the last install, and noticed that it was putting the bootloader in (hd0), although XP is (hd2,0) and Ubuntu is loading on (hd1,0). I'm installing again, and this time I have changed it to put the bootloader on ... well, of course it doesn't give me the option to put it on (hd1,0), so I have to put it on /dev/sdb1 which I know is the place Ubuntu is being loaded. Good thing I remembered that. Installing again again, and crossing my fingers... Perhaps the problem where I was finding stage1 on hd1,0 will be resolved if I put the bootloader there, also? I got no idea, but it's the only thing I can come up with right now. 

Problem is, at present, XP is on and loads up just fine. I have Ubuntu loaded, yet I don't find grub when I boot, the computer just goes straight into XP.

---

### Post by caljohnsmith on 2009-04-25
BLTicklemonster, how about first downloading the latest version of the Boot Info Script to your desktop from the following location:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

And then instead of posting the contents of the script, run this command instead:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
And then post the contents of the RESULTS.txt file that will be created on your desktop. That will give us a better place to start.

---

### Post by BLTicklemonster on 2009-04-25
```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /menu.lst

sdb1: _________________________________________________________________________

    File system:       reiserfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdc1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdc1 sdc1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdc1 sdc1 ntfs-3g force 0 0
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdc1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdc1 sdc1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdc1 sdc1 ntfs-3g force 0 0

sdc2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdc2': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdc2 sdc2 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdc2 sdc2 ntfs-3g force 0 0
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdc2': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdc2 sdc2 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdc2 sdc2 ntfs-3g force 0 0

sdc4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdc5': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdc5 sdc5 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdc5 sdc5 ntfs-3g force 0 0
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdc5': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdc5 sdc5 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdc5 sdc5 ntfs-3g force 0 0

sdc6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdc6': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdc6 sdc6 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdc6 sdc6 ntfs-3g force 0 0
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdc6': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdc6 sdc6 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdc6 sdc6 ntfs-3g force 0 0

sdc7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdc7': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdc7 sdc7 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdc7 sdc7 ntfs-3g force 0 0
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdc7': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdc7 sdc7 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdc7 sdc7 ntfs-3g force 0 0

sdc8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdc8': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdc8 sdc8 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdc8 sdc8 ntfs-3g force 0 0
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdc8': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdc8 sdc8 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdc8 sdc8 ntfs-3g force 0 0

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders, total 156368016 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x55054103

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   156,360,644   156,360,582   b W95 FAT32


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x38903890

Partition  Boot         Start           End          Size  Id System

/dev/sdb1 [COLOR="Red"](hd1,0) which is where findstage1 says grub should be[/COLOR] 63   296,961,524   296,961,462  83 Linux
/dev/sdb2         296,961,525   312,576,704    15,615,180  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xed19ed19

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63    81,905,039    81,904,977   7 HPFS/NTFS
/dev/sdc2          81,915,435   242,067,419   160,151,985   7 HPFS/NTFS
/dev/sdc4         242,067,420 1,250,258,624 1,008,191,205   5 Extended
/dev/sdc5         242,067,483   408,356,234   166,288,752   7 HPFS/NTFS
/dev/sdc6         572,749,443   911,512,034   338,762,592   7 HPFS/NTFS
/dev/sdc7         911,512,098 1,250,258,624   338,746,527   7 HPFS/NTFS
/dev/sdc8         408,356,298   572,749,379   164,393,082   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="49F2-9E75" TYPE="vfat" 
/dev/sdb1: UUID="08e4a59d-a05c-49d8-a25e-2de8bb30a67f" TYPE="reiserfs" 
/dev/sdb2: TYPE="swap" UUID="a205df67-db8e-43a4-b17d-d5124b4340d0" 
/dev/sdc1: UUID="74CCB7DECCB798B6" TYPE="ntfs" 
/dev/sdc2: UUID="164E0DFF4FA7590E" TYPE="ntfs" 
/dev/sdc5: UUID="13E0DC9E4BCF716A" TYPE="ntfs" 
/dev/sdc6: UUID="3C54FD5865B9878F" TYPE="ntfs" 
/dev/sdc7: UUID="411901812E94D527" TYPE="ntfs" 
/dev/sdc8: UUID="046704EE44B00084" TYPE="ntfs" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)
/dev/sdb1 on /media/disk-1 type reiserfs (rw,nosuid,nodev,uhelper=hal)


================================ sda1/menu.lst: ================================

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
# kopt=root=UUID=40d4580c-e355-4b6a-b3ea-ce61045d1429 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=40d4580c-e355-4b6a-b3ea-ce61045d1429

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

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		40d4580c-e355-4b6a-b3ea-ce61045d1429
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=40d4580c-e355-4b6a-b3ea-ce61045d1429 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		40d4580c-e355-4b6a-b3ea-ce61045d1429
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=40d4580c-e355-4b6a-b3ea-ce61045d1429 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		40d4580c-e355-4b6a-b3ea-ce61045d1429
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=40d4580c-e355-4b6a-b3ea-ce61045d1429 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		40d4580c-e355-4b6a-b3ea-ce61045d1429
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=40d4580c-e355-4b6a-b3ea-ce61045d1429 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		40d4580c-e355-4b6a-b3ea-ce61045d1429
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Windows XP Professional x64 Edition
#root		(hd2,0)
root		(hd0,0)
#savedefault
makeactive
#map		(hd0) (hd2)
#map		(hd2) (hd0)
chainloader	+1




=================== sda1: Location of files loaded by Grub: ===================


   3.1GB: menu.lst

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
# kopt=root=UUID=08e4a59d-a05c-49d8-a25e-2de8bb30a67f ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=08e4a59d-a05c-49d8-a25e-2de8bb30a67f ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=08e4a59d-a05c-49d8-a25e-2de8bb30a67f ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Windows XP Professional x64 Edition
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=08e4a59d-a05c-49d8-a25e-2de8bb30a67f /               reiserfs notail,relatime 0       1
# /dev/sdb2
UUID=a205df67-db8e-43a4-b17d-d5124b4340d0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


   3.2GB: boot/grub/menu.lst
   3.2GB: boot/grub/stage2
   3.2GB: boot/initrd.img-2.6.24-16-generic
    .1GB: boot/initrd.img-2.6.24-16-generic.bak
    .1GB: boot/vmlinuz-2.6.24-16-generic
   3.2GB: initrd.img
    .1GB: vmlinuz

```

I started being unable to mount a bunch of partitions since trying to set the bootloader to a different place :( I can get that resolved later though.

Mind you, I was able to mount all partitions when I first started having the error 17. Now I have no grub at all, just straight boot into xp.

---

### Post by BLTicklemonster on 2009-04-25
Doh. Sorry for the trouble. I have resolved this, and I wish I had remembered this trick earlier! 

When I got to where I was booting to xp without grub, all I had to do was boot to live cd, open sudo gparted, go to the drive where ubuntu is loaded, which is sbd1, and right click on the partition itself, then go to manage flags and set it to boot. 

I checked others, and sdc1 was still marked as boot for some reason, so I unchecked that in manage flags, closed gparted, then ran sudo grub, root (hd1,0), then setup (hd1) and voila, I'm getting grub at boot, and it shows ubuntu and XP.

I stumbled onto that once a long time ago, and forgot all about it. Now to get my mounting back working on my partitions... hooo boy.

:popcorn:

---

### Post by caljohnsmith on 2009-04-26
Glad to hear you figured out your booting problem, BLTicklemonster. :) It sounds like your computer has a BIOS that won't boot a drive unless one of the partitions has the boot flag set, even though Grub does not care about which partition has the boot flag set. But the important thing is you fixed your booting problem, so now you can move on to more interesting matters in Ubuntu. :)

---

### Post by BLTicklemonster on 2009-04-26
I'm still learning after all this time.

Thanks for the help, though!

---

