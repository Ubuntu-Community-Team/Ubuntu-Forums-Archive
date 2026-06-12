---
title: "XP won't boot after Ubuntu install"
date: 2008-12-24
forum: Installation &amp; Upgrades
---

### Post by likemike64 on 2008-12-24
I have searched the forum but not found a fix that works.
I installed 64 bit Ubuntu on my Compaq GX5050 using all defaults except the partitioning. After the install, XP will not boot. 

The only change I made in partitioning (during the install) was to use the slider to change the size of the windows partition to about 160 GB of the 250 GB drive. I put the / partition second, and the swap last. I used ext3 for /.

When I try to boot XP, it simply hangs on a black screen, with no display. The windows logo and slider never show up.  Ubuntu boots fine; I am using it to post this message.

I can mount and see the contents of the Windows drive.

Here is my /boot/grub/menu.list file:
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
default		saved

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
# kopt=root=UUID=aba64f9e-870f-4146-abf0-753702ade62a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=aba64f9e-870f-4146-abf0-753702ade62a

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

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		aba64f9e-870f-4146-abf0-753702ade62a
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=aba64f9e-870f-4146-abf0-753702ade62a ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		aba64f9e-870f-4146-abf0-753702ade62a
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=aba64f9e-870f-4146-abf0-753702ade62a ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		aba64f9e-870f-4146-abf0-753702ade62a
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=aba64f9e-870f-4146-abf0-753702ade62a ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		aba64f9e-870f-4146-abf0-753702ade62a
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=aba64f9e-870f-4146-abf0-753702ade62a ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		aba64f9e-870f-4146-abf0-753702ade62a
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

```

Here is the results of fdisk -lu:
```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xbc2326ea

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   318761729   159380833+   7  HPFS/NTFS
/dev/sda2       318761730   488392064    84815167+   5  Extended
/dev/sda5       318761793   481387724    81312966   83  Linux
/dev/sda6       481387788   488392064     3502138+  82  Linux swap / Solaris

```

Here is the content of XP's boot.ini:
```
[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

```

Any help is greatly appreciated.

---

### Post by caljohnsmith on 2008-12-24
How about posting the output of:
```
sudo hexdump -s 28 -n 4 -e '"%d\n"' /dev/sda1
```
I suspect your problem might be that you need to repair the XP partition boot sector, but the above command will help determine whether it is necessary.

---

### Post by likemike64 on 2008-12-25
The result is "63"
What does that mean?

---

### Post by caljohnsmith on 2008-12-25
> **likemike64 said:**
> The result is "63"
What does that mean?
The XP partition boot sector contains the sector starting location of the partition, which is what that command returned; "63" is what we were hoping for, because your XP sda1 partition starts at sector 63. It still might be that your XP boot sector needs repairing, so how about doing:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk, choose "no log", choose the correct HDD and "proceed", choose "intel", choose "advanced", select the sda1 Windows partition, choose "boot", then choose "Rebuild BS"; if testdisk gives you a warning that the "sectors are not identical", then choose "write". If you do write the new boot sector, reboot and let me know exactly what happens when you boot Windows XP from the Grub menu. But if testdisk says the boot sectors are identical, let me know, and we can work from there.

---

### Post by VastOne on 2008-12-25
> **caljohnsmith said:**
> The XP partition boot sector contains the sector starting location of the partition, which is what that command returned; "63" is what we were hoping for, because your XP sda1 partition starts at sector 63. It still might be that your XP boot sector needs repairing, so how about doing:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk, choose "no log", choose the correct HDD and "proceed", choose "intel", choose "advanced", select the sda1 Windows partition, choose "boot", then choose "Rebuild BS"; if testdisk gives you a warning that the "sectors are not identical", then choose "write". If you do write the new boot sector, reboot and let me know exactly what happens when you boot Windows XP from the Grub menu. But if testdisk says the boot sectors are identical, let me know, and we can work from there.

Incredible, insightful and well said reply...Not anything I am in need of but this help gave me a lot of new tools and info to work with...

Thanks for the time and guru level help CalJohnSmith

---

### Post by likemike64 on 2008-12-25
Thanks CalJohnSmith, for all of the help!!! :KS

The sectors were not identical. I followed the steps you outlined, and it fixed them. When I booted to Windows, it automatically ran a chkdsk, then rebooted, and booted into Windows fine.

I want to make sure I understand what happened correctly. When the Ubuntu install script moved the Windows boot sector, it somehow got written incorrectly? Windows, couldn't handle it and would not boot as a result, right?

This "testdisk" is a very useful tool. Thanks for calling it to my attention.

---

### Post by caljohnsmith on 2008-12-26
> **likemike64 said:**
> Thanks CalJohnSmith, for all of the help!!! :KS

The sectors were not identical. I followed the steps you outlined, and it fixed them. When I booted to Windows, it automatically ran a chkdsk, then rebooted, and booted into Windows fine.

I want to make sure I understand what happened correctly. When the Ubuntu install script moved the Windows boot sector, it somehow got written incorrectly? Windows, couldn't handle it and would not boot as a result, right?

This "testdisk" is a very useful tool. Thanks for calling it to my attention.
I'm glad to hear that testdisk did the trick; I know from the "vicarious" experience of helping others in the forums that the starting sector value that gets written to the NTFS boot sector sometimes ends up being wrong (that was the value you checked with the hexdump command), but I'm not sure of what exact circumstances cause that to happen. As I understand it, there are also other Windows file system parameters stored in the Windows boot sector that sometimes seem to get corrupted when resizing the Windows partition, but fortunately testdisk is usually really good about fixing them if they somehow are off. Anyway, cheers and have fun with Windows and Ubuntu. :)

---

### Post by Bread Pit on 2008-12-26
Thanks again for your answers, they didn't work for me, but I think at least now I'm on the right path. I have the same problem as likemike64, only I've moved my win XP partition to the end of the disk, because I'm computing stuff on Ubuntu and want it to work faster. 
When I tried sudo hexdump -s 28 -n 4 -e '"%d\n"' /dev/sda2, (my WinXP partition is on /sda2) I got this:
126961695

I have added in my menu.lst

title WinXP
root (hd0,1)
makeactive
chainloader+1

I got to the point where testdisk states that boot sectors are identical, and need instructions from there. I can't find boot.ini anywhere in /windows using find, so there is no way to change it for partition 2 on disk. Is that necessary? Thanks.

---

### Post by caljohnsmith on 2008-12-26
Bread Pit, In order to get a clearer picture of your setup, how about opening  a terminal in Ubuntu (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post. That will help clarify your setup and hopefully what your Windows problem might be.

---

### Post by Bread Pit on 2008-12-26
I did it. here's the results.txt:

============================= Boot Info Summary: ==============================

Grub is installed in the MBR of /dev/sda and looks on the same drive in partition #1 for its boot files.

_______________________________________________________________________________
sda1:
    File system:  ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst /grub

_______________________________________________________________________________
sda2:
    File system:  ntfs
    Boot sector type:  Unknown
    Boot sector info:  According to the info in the boot sector, sda2 starts 
                       at sector 126961695.
    Operating System:  XP
    Boot files/dirs:   

_______________________________________________________________________________
sda3:
    File system:  swap

_______________________________________________________________________________
sda4:
    File system:  Extended Partition

_______________________________________________________________________________
sda5:
    File system:  ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

_______________________________________________________________________________
sda6:
    File system:  ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /etc/fstab /boot

_______________________________________________________________________________
sda7:
    File system:  ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

_______________________________________________________________________________
sda8:
    File system:  ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================
fdisk -lu /dev/sda:

Disk /dev/sda: 79.8 GB, 79826342400 bytes
255 heads, 63 sectors/track, 9705 cylinders, total 155910825 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1ab7902e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63      610469      305203+  83  Linux
/dev/sda2       126961695   155910824    14474565    7  HPFS/NTFS
/dev/sda3   *      610470     4514264     1951897+  82  Linux swap / Solaris
/dev/sda4         4514265   126961694    61223715    5  Extended
/dev/sda5         4514328    67007114    31246393+  83  Linux
/dev/sda6        67007178    80678429     6835626   83  Linux
/dev/sda7        80678493   119748509    19535008+  83  Linux
/dev/sda8       119748573   126961694     3606561   83  Linux

Partition table entries are not in disk order

sfdisk -V /dev/sda:

/dev/sda: OK

_______________________________________________________________________________
blkid -c /dev/null:

/dev/sda1: UUID="5e03c342-ffc8-4fee-a40f-1ab2a137e719" TYPE="ext3" 
/dev/sda2: UUID="52B36DF879594230" TYPE="ntfs" 
/dev/sda3: UUID="04e2dad1-93dc-417b-9d22-ea9ede78ba29" TYPE="swap" 
/dev/sda5: UUID="fa861f6e-b1ec-45c5-ab6b-ef92b90f3bd2" TYPE="ext3" 
/dev/sda6: UUID="06da7abe-c9de-458c-8a5f-07a27f31e096" TYPE="ext3" 
/dev/sda7: UUID="913e58da-1826-4145-90aa-916942dd7911" TYPE="ext3" 
/dev/sda8: UUID="517e07ae-76a2-4a4a-b5ca-59e164d8ce35" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-9-generic/volatile type tmpfs (rw,mode=755)
/dev/sda1 on /boot type ext3 (rw,relatime)
/dev/sda5 on /home type ext3 (rw,relatime)
/dev/sda7 on /usr type ext3 (rw,relatime)
/dev/sda8 on /var type ext3 (rw,relatime)
/dev/sda2 on /windows type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/marija/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=marija)
/dev/scd0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,utf8,user=marija)

============================ sda1/grub/menu.lst: ============================

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
# kopt=root=UUID=06da7abe-c9de-458c-8a5f-07a27f31e096 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=5e03c342-ffc8-4fee-a40f-1ab2a137e719

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

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		5e03c342-ffc8-4fee-a40f-1ab2a137e719
kernel		/vmlinuz-2.6.27-9-generic root=UUID=06da7abe-c9de-458c-8a5f-07a27f31e096 ro quiet splash 
initrd		/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		5e03c342-ffc8-4fee-a40f-1ab2a137e719
kernel		/vmlinuz-2.6.27-9-generic root=UUID=06da7abe-c9de-458c-8a5f-07a27f31e096 ro  single
initrd		/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		5e03c342-ffc8-4fee-a40f-1ab2a137e719
kernel		/vmlinuz-2.6.27-7-generic root=UUID=06da7abe-c9de-458c-8a5f-07a27f31e096 ro quiet splash 
initrd		/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		5e03c342-ffc8-4fee-a40f-1ab2a137e719
kernel		/vmlinuz-2.6.27-7-generic root=UUID=06da7abe-c9de-458c-8a5f-07a27f31e096 ro  single
initrd		/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		5e03c342-ffc8-4fee-a40f-1ab2a137e719
kernel		/memtest86+.bin
quiet


title           WinXP 
rootnoverify    (hd0,0
makeactive
chainloader     +1



### END DEBIAN AUTOMAGIC KERNELS LIST

============================ sda1/grub: ============================

total 194
drwxr-xr-x 2 root root   1024 2008-12-26 18:51 .
drwxr-xr-x 4 root root   1024 2008-12-17 11:04 ..
-rw-r--r-- 1 root root    197 2008-12-07 21:19 default
-rw-r--r-- 1 root root     15 2008-12-07 21:19 device.map
-rw-r--r-- 1 root root   8108 2008-12-07 21:19 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2008-12-07 21:19 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-12-07 21:19 installed-version
-rw-r--r-- 1 root root   8712 2008-12-07 21:19 jfs_stage1_5
-rw-r--r-- 1 root root   4827 2008-12-26 18:51 menu.lst
-rw-r--r-- 1 root root   4749 2008-12-21 19:29 menu.lst~
-rw-r--r-- 1 root root   4844 2008-12-24 20:19 menu.lstOLD
-rw-r--r-- 1 root root   7352 2008-12-07 21:19 minix_stage1_5
-rw-r--r-- 1 root root   9756 2008-12-07 21:19 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-12-07 21:19 stage1
-rw-r--r-- 1 root root 121460 2008-12-07 21:19 stage2
-rw-r--r-- 1 root root   9556 2008-12-07 21:19 xfs_stage1_5

============================ sda6/etc/fstab: ============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=06da7abe-c9de-458c-8a5f-07a27f31e096 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda1
UUID=5e03c342-ffc8-4fee-a40f-1ab2a137e719 /boot           ext3    relatime        0       2
# /dev/sda5
UUID=fa861f6e-b1ec-45c5-ab6b-ef92b90f3bd2 /home           ext3    relatime        0       2
# /dev/sda7
UUID=913e58da-1826-4145-90aa-916942dd7911 /usr            ext3    relatime        0       2
# /dev/sda8
UUID=517e07ae-76a2-4a4a-b5ca-59e164d8ce35 /var            ext3    relatime        0       2
# /dev/sda2
UUID=52B36DF879594230 /windows        ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda3
UUID=04e2dad1-93dc-417b-9d22-ea9ede78ba29 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

============================ sda6/boot: ============================

total 8
drwxr-xr-x  2 root root 4096 2008-12-07 21:05 .
drwxr-xr-x 20 root root 4096 2008-12-10 20:26 ..

=============================== StdErr Messages: ===============================

Unknown BootLoader  on /dev/sda2

00000000  eb 5b 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.[.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 1f 48 91 07  |........?....H..|
00000020  00 00 00 00 80 00 80 00  89 ba b9 01 00 00 00 00  |................|
00000030  04 00 00 00 00 00 00 00  a8 9b 1b 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  30 42 59 79 f8 6d b3 52  |........0BYy.m.R|
00000050  00 00 00 00 00 00 00 00  00 00 00 00 00 fa 33 c0  |..............3.|
00000060  8e d0 bc 00 7c fb b8 c0  07 8e d8 c7 06 54 00 00  |....|........T..|
00000070  00 c7 06 56 00 00 00 c7  06 5b 00 10 00 b8 00 0d  |...V.....[......|
00000080  8e c0 2b db e8 07 00 68  00 0d 68 66 02 cb 50 53  |..+....h..hf..PS|
00000090  51 52 06 66 a1 54 00 66  03 06 1c 00 66 33 d2 66  |QR.f.T.f....f3.f|
000000a0  0f b7 0e 18 00 66 f7 f1  fe c2 88 16 5a 00 66 8b  |.....f......Z.f.|
000000b0  d0 66 c1 ea 10 f7 36 1a  00 88 16 25 00 a3 58 00  |.f....6....%..X.|
000000c0  a1 18 00 2a 06 5a 00 40  3b 06 5b 00 76 03 a1 5b  |...*.Z.@;.[.v..[|
000000d0  00 50 b4 02 8b 16 58 00  b1 06 d2 e6 0a 36 5a 00  |.P....X......6Z.|
000000e0  8b ca 86 e9 8a 36 25 00  b2 80 cd 13 58 72 2a 01  |.....6%.....Xr*.|
000000f0  06 54 00 83 16 56 00 00  29 06 5b 00 76 0b c1 e0  |.T...V..).[.v...|
00000100  05 8c c2 03 d0 8e c2 eb  8a 07 5a 59 5b 58 c3 be  |..........ZY[X..|
00000110  59 01 eb 08 be e3 01 eb  03 be 39 01 e8 09 00 be  |Y.........9.....|
00000120  ad 01 e8 03 00 fb eb fe  ac 3c 00 74 09 b4 0e bb  |.........<.t....|
00000130  07 00 cd 10 eb f2 c3 1d  00 41 20 64 69 73 6b 20  |.........A disk |
00000140  72 65 61 64 20 65 72 72  6f 72 20 6f 63 63 75 72  |read error occur|
00000150  72 65 64 2e 0d 0a 00 29  00 41 20 6b 65 72 6e 65  |red....).A kerne|
00000160  6c 20 66 69 6c 65 20 69  73 20 6d 69 73 73 69 6e  |l file is missin|
00000170  67 20 66 72 6f 6d 20 74  68 65 20 64 69 73 6b 2e  |g from the disk.|
00000180  0d 0a 00 25 00 41 20 6b  65 72 6e 65 6c 20 66 69  |...%.A kernel fi|
00000190  6c 65 20 69 73 20 74 6f  6f 20 64 69 73 63 6f 6e  |le is too discon|
000001a0  74 69 67 75 6f 75 73 2e  0d 0a 00 33 00 49 6e 73  |tiguous....3.Ins|
000001b0  65 72 74 20 61 20 73 79  73 74 65 6d 20 64 69 73  |ert a system dis|
000001c0  6b 65 74 74 65 20 61 6e  64 20 72 65 73 74 61 72  |kette and restar|
000001d0  74 0d 0a 74 68 65 20 73  79 73 74 65 6d 2e 0d 0a  |t..the system...|
000001e0  00 17 00 5c 4e 54 4c 44  52 20 69 73 20 63 6f 6d  |...\NTLDR is com|
000001f0  70 72 65 73 73 65 64 2e  0d 0a 00 00 00 00 55 aa  |pressed.......U.|
00000200

---

### Post by Bread Pit on 2008-12-26
I've tampered with mu menu.lst just now (idiot), the line where it says

rootnoverify (hd0,0

is rootnoverify (hd0,1)

Sorry about that.

---

### Post by caljohnsmith on 2008-12-26
No problem, I'm glad that you figured it out. Cheers and have fun with Windows and Ubuntu. :)

---

### Post by Bread Pit on 2008-12-26
no, still doesn't work...

---

### Post by caljohnsmith on 2008-12-26
> **Bread Pit said:**
> no, still doesn't work...
OK, so you originally said you moved Windows to the end of the disk; exactly what method did you use to do this? Where was Windows to begin with? It also looks like you are missing your Windows boot files, but that might be only one of a number of problems with Windows right now. When you boot Windows from Grub using (hd0,1), are you getting a "NTLDR missing" error?

---

### Post by Bread Pit on 2008-12-26
First I had windows only(german version). Then I used Fedora Live CD and resized the partitions on the disk. I've formated the back of the disk with ntfs erasing windows (it was a German version I didn't want), and left space in the front for ubuntu. I've formated the first part of the diski(250 MB) into ntfs primary partition (later to be left for /boot) so that i can install winXP, and then installed windows. Then I installed ubuntu on the space in the front(formatting the first sectors along with /boot in ext3 FS), and changed menu.lst. When I restart and enter grub menu, and choose WinXP it only writes starting... or smth. similar. And waits there indefinetly. :) I have a feeling I've messed things up. :) Thank you again.

---

### Post by caljohnsmith on 2008-12-26
OK, how about posting the output of:
```
sudo mount /dev/sda2 /mnt
ls -l /mnt
```

---

### Post by Bread Pit on 2008-12-26
no need for a mount, it's automatically mounted on /windows, here is what I get from mount:

/dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-9-generic/volatile type tmpfs (rw,mode=755)
/dev/sda1 on /boot type ext3 (rw,relatime)
/dev/sda5 on /home type ext3 (rw,relatime)
/dev/sda7 on /usr type ext3 (rw,relatime)
/dev/sda8 on /var type ext3 (rw,relatime)
/dev/sda2 on /windows type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/marija/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=marija)
/dev/scd0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,utf8,user=marija)

and here is 'ls -l /windows':

marija@shabana:~$ ls -l /windows/
total 1573268
drwxrwx--- 1 root plugdev       4096 2008-12-07 19:18 Documents and Settings
-rwxrwx--- 1 root plugdev     364721 2008-05-02 11:11 DPsFnshr.exe
-rwxrwx--- 1 root plugdev 1610612736 2008-12-07 19:15 pagefile.sys
drwxrwx--- 1 root plugdev       8192 2008-12-07 19:20 Program Files
drwxrwx--- 1 root plugdev          0 2008-12-07 19:24 RECYCLER
drwxrwx--- 1 root plugdev       4096 2008-12-07 19:16 System Volume Information
drwxrwx--- 1 root plugdev      28672 2008-12-07 19:18 WINDOWS
marija@shabana:~$

---

### Post by caljohnsmith on 2008-12-26
OK, so you are definitely missing the Windows boot files, but I'm a bit confused why you would be missing them if you just installed Windows to the sda2 partition. But anyway, I've attached the three boot files you need to this post, and also configured the "boot.ini" file so that it should work with your particular setup. How about downloading the attached "WinXP_boot_files2.zip" to your Ubuntu desktop, and do:
```
cd ~/Desktop
unzip WinXP_boot_files2.zip
sudo mv boot.ini ntldr NTDETECT.COM /windows
ls -l /windows
cat -A /windows/boot.ini
```
And please post the output of the above commands. Also, I think the boot code in your XP boot sector might need repairing, because I believe you should have gotten a "NTLDR is missing" error when booting the XP partition before since XP didn't have its boot files; also the script you ran was not able to identify your XP boot sector as being valid. To fix it, how about doing the following (note this is slightly different than the previous testdisk procedure you used):
```
sudo testdisk
```
After starting testdisk, choose "no log", choose the correct HDD and "proceed", choose "intel", choose "advanced", select the Windows partition, choose "boot", then choose "Backup BS"; if testdisk gives you a warning that the "sectors are not identical", then choose "write". After you are done doing the "Backup BS" in testdisk, reboot and let me know exactly what happens when you boot Windows XP from the Grub menu. We can work from there.

---

### Post by Bread Pit on 2008-12-26
i did it:

marija@shabana:zaWin$ ls -l /windows/
total 1573565
-rwxrwx--- 1 root plugdev        202 2008-12-18 01:31 boot.ini
drwxrwx--- 1 root plugdev       4096 2008-12-07 19:18 Documents and Settings
-rwxrwx--- 1 root plugdev     364721 2008-05-02 11:11 DPsFnshr.exe
-rwxrwx--- 1 root plugdev      47564 2008-12-09 20:06 NTDETECT.COM
-rwxrwx--- 1 root plugdev     250048 2008-12-09 20:06 ntldr
-rwxrwx--- 1 root plugdev 1610612736 2008-12-07 19:15 pagefile.sys
drwxrwx--- 1 root plugdev       8192 2008-12-07 19:20 Program Files
drwxrwx--- 1 root plugdev          0 2008-12-07 19:24 RECYCLER
drwxrwx--- 1 root plugdev       4096 2008-12-07 19:16 System Volume Information
drwxrwx--- 1 root plugdev      28672 2008-12-07 19:18 WINDOWS
marija@shabana:zaWin$ cat -A /windows/boot.ini 
[boot loader]^M$
timeout=30^M$
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS^M$
[operating systems]^M$
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP" ^M$
/fastdetect /NoExecute=OptIn^M$
^M$
marija@shabana:zaWin$ 

THANK YOU. :)

---

### Post by Bread Pit on 2008-12-26
I'll restart now...

---

### Post by Bread Pit on 2008-12-26
nope. :) There's just this on the screen:

starting up... 

and just hangs there. :) The only problem now is, if I am to install windows again on this ntfs formatted disk space, that I can't do it because first (MBR) part of the disk drive is in ext3 file format, so XP can't write it's boot loader there(if i understand it in the right way). I was thinking about setting up KVM, but my processor doesn't supprot intel VM technology. :|

---

### Post by caljohnsmith on 2008-12-26
Did you run the testdisk procedure? Did testdisk say the sectors were not identical or what happened with that? (Did you make sure to use "Backup BS" and not the "Rebuild BS" option this time?)

---

### Post by Bread Pit on 2008-12-26
ok, those were my options during testdisk:

TestDisk 6.9, Data Recovery Utility, February 2008
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 79 GB / 74 GiB - CHS 9705 255 63
     Partition                  Start        End    Size in sectors
 2 * HPFS - NTFS           7903   0  1  9704 254 63   28949130

Boot sector
Status: OK

Backup boot sector
Status: OK

Sectors are identical.

A valid NTFS Boot sector must be present in order to access
any data; even if the partition is not bootable.





[  Quit  ]  [  List  ]  [Rebuild BS]  [Repair MFT]  [  Dump  ]
                            Return to Advanced menu

I didn't see backup BS. I hope I didn't accidentaly activated backup before. I was reading about grub. There seems to be an option to install windows with it acting like it's writing it's bootloader on MBR. I have no idea how to solve this.

---

### Post by caljohnsmith on 2008-12-26
OK, since your Windows is a new install anyway, how about reinstalling Windows to sda2, and after you've installed, check to make sure you can boot directly into Windows and everything works OK. I think it makes more sense to just reinstall Windows at this point since it is a fresh install anyway, rather than try and figure out its booting problem. If Windows boots OK once you've reinstalled, then you can restore Grub to the MBR with the following steps from the Live CD:
```
sudo grub
grub> root (hd0,0)
grub> setup (hd0)
grub> quit
```
Let me know how it goes or if you run into problems.

---

### Post by Bread Pit on 2008-12-26
thank you for your help. ALOT. :) I'll reinstall it, and then setup grub like you said. I just hope windows won't complain if the first half of the disk (as well as MBR) is in ext3.. :)

---

### Post by lazman on 2008-12-26
I am having the same issue but I did not move windows at all. I installed Ubuntu 8.10 and when I try to start windows it blue screens with inaccessible_boot_device on the spash screen about 3/4 the way on the blue pregress bar. I did get the value 63 and the results from test disk are identical instead of diffrent. I really don't want to reinstall windows if at all possible. What action would I take if I did NOT move the windows partition?

Thanks
~laz

---

### Post by caljohnsmith on 2008-12-26
Lazman, how about posting the output of the boot_info_script.txt from post #9. That will clarify your setup.

---

### Post by lazman on 2008-12-26
Thanks for your help!
> ============================= Boot Info Summary: ==============================

Grub is installed in the MBR of /dev/sda and looks on the same drive in 
partition #5 for its boot files.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  XP
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sda6: _________________________________________________________________________

    File system:       swap

=========================== Drive/Partition Info: =============================
fdisk -lu /dev/sda:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x36423641

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   424067804   212033871    7  HPFS/NTFS
/dev/sda2       424067805   488392064    32162130    5  Extended
/dev/sda5       424067868   485644949    30788541   83  Linux
/dev/sda6       485645013   488392064     1373526   82  Linux swap / Solaris

sfdisk -V /dev/sda:

/dev/sda: OK

_______________________________________________________________________________
blkid -c /dev/null:

/dev/sda1: UUID="ECE8ADEDE8ADB66C" TYPE="ntfs" 
/dev/sda5: UUID="0e97d67c-6aa5-4b82-af73-94608229f08b" TYPE="ext3" 
/dev/sda6: UUID="0d724598-3248-46b0-8dee-9c4383c65807" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-9-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/shannon/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=shannon)

================================ sda1/boot.ini: ================================

[boot loader]

timeout=0

default=multi(0)disk(0)rdisk(0)partition(1)\WINNT

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINNT="Microsoft Windows 2000 Professional" /fastdetect

C:\="Microsoft Windows" 


=========================== sda5/boot/grub/menu.lst: ===========================

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=0e97d67c-6aa5-4b82-af73-94608229f08b ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=0e97d67c-6aa5-4b82-af73-94608229f08b

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
# defoptions=quiet splash vga=795

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

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		0e97d67c-6aa5-4b82-af73-94608229f08b
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=0e97d67c-6aa5-4b82-af73-94608229f08b ro quiet splash vga=795 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		0e97d67c-6aa5-4b82-af73-94608229f08b
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=0e97d67c-6aa5-4b82-af73-94608229f08b ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		0e97d67c-6aa5-4b82-af73-94608229f08b
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=0e97d67c-6aa5-4b82-af73-94608229f08b ro quiet splash vga=795 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		0e97d67c-6aa5-4b82-af73-94608229f08b
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=0e97d67c-6aa5-4b82-af73-94608229f08b ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		0e97d67c-6aa5-4b82-af73-94608229f08b
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows 2000 Professional
root		(hd0,0)
#savedefault
makeactive
chainloader	+1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=0e97d67c-6aa5-4b82-af73-94608229f08b /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=0d724598-3248-46b0-8dee-9c4383c65807 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sda5/boot: ==================================

total 25516
drwxr-xr-x  3 root root    4096 2008-12-26 17:56 .
drwxr-xr-x 21 root root    4096 2008-12-20 10:16 ..
-rw-r--r--  1 root root  503560 2008-11-04 14:53 abi-2.6.27-7-generic
-rw-r--r--  1 root root  503560 2008-11-20 17:30 abi-2.6.27-9-generic
-rw-r--r--  1 root root   85316 2008-11-04 14:53 config-2.6.27-7-generic
-rw-r--r--  1 root root   85316 2008-11-20 17:30 config-2.6.27-9-generic
drwxr-xr-x  3 root root    4096 2008-12-26 18:21 grub
-rw-r--r--  1 root root 8666514 2008-12-26 17:56 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root 8666278 2008-12-26 17:56 initrd.img-2.6.27-9-generic
-rw-r--r--  1 root root  124152 2008-09-11 15:11 memtest86+.bin
-rw-r--r--  1 root root 1352144 2008-11-04 14:53 System.map-2.6.27-7-generic
-rw-r--r--  1 root root 1352144 2008-11-20 17:30 System.map-2.6.27-9-generic
-rw-r--r--  1 root root    1130 2008-11-04 14:57 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root    1130 2008-11-20 17:32 vmcoreinfo-2.6.27-9-generic
-rw-r--r--  1 root root 2339552 2008-11-04 14:53 vmlinuz-2.6.27-7-generic
-rw-r--r--  1 root root 2339712 2008-11-20 17:30 vmlinuz-2.6.27-9-generic

=============================== sda5/boot/grub: ===============================

total 236
drwxr-xr-x 3 root root   4096 2008-12-26 18:21 .
drwxr-xr-x 3 root root   4096 2008-12-26 17:56 ..
-rw-r--r-- 1 root root    197 2008-12-19 22:25 default
-rw-r--r-- 1 root root     15 2008-12-19 22:25 device.map
-rw-r--r-- 1 root root   8108 2008-12-19 22:25 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2008-12-19 22:25 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-12-19 22:25 installed-version
-rw-r--r-- 1 root root   8712 2008-12-19 22:25 jfs_stage1_5
-rw-r--r-- 1 root root   5126 2008-12-26 18:21 menu.lst
-rw-r--r-- 1 root root   5125 2008-12-26 17:56 menu.lst~
-rw-r--r-- 1 root root   5105 2008-12-26 17:54 menu.lst.backup
-rw-r--r-- 1 root root   7352 2008-12-19 22:25 minix_stage1_5
-rw-r--r-- 1 root root   9756 2008-12-19 22:25 reiserfs_stage1_5
drwxr-xr-x 2 root root   4096 2008-12-26 17:54 splashimages
-rw-r--r-- 1 root root    512 2008-12-19 22:25 stage1
-rw-r--r-- 1 root root 121460 2008-12-19 22:25 stage2
-rw-r--r-- 1 root root   9556 2008-12-19 22:25 xfs_stage1_5

=============================== StdErr Messages: ===============================


---

### Post by caljohnsmith on 2008-12-26
Lazman, it looks like Grub is correctly booting your Windows sda1 partition, so I think you unfortunately have a Windows problem and not a Grub problem at this point. How about booting your Windows Install CD, go to the command line (recovery console) and run:
```
chkdsk /r
```
And run chkdsk as many times as it takes until it reports no errors. Then try booting Windows again, and let me know if you get any further or what the error is.

---

### Post by j_galt on 2008-12-27
I've got the same problem - sort of.  Let me describe my problem, and then please let me know if I should create a new thread for this...

I've got a laptop that is running WinXP Home - this is the only OS on the internal hard drive (sda).  I have set up an external USB hard drive (sdb) with a couple of FAT32 partitions (both primary) to use to back up the laptop and another system I have here.  I created an extended partition on which to put at least 2 linux distros, the first of which is Kubuntu 8.10.  I've left plenty of free space to divide up however I want to install further distros.  My final primary partition is the first 8MB of the USB drive where I have put Grub.

I had a couple of false starts, but I've got Kubuntu up and running - I have no problems booting into either the main OS or the recovery mode from Grub.  The USB drive is set up so that the laptop will boot directly into WinXP when it is not attached, but so that Grub will control bootup when it is connected upon startup / restart.

My problem is that when I boot up with the USB drive connected, and I choose WinXP from the Grub menu, I get a black screen with the only output being:

"Starting up ..."

It doesn't 'lock up', as I can <Ctrl><Alt><Delete> to restart every time.  What has really got me stumped is that it did boot into WinXP a couple of times when I first set it up, but it doesn't now.  After I initially checked it, I made some adjustments to allow Kubuntu to boot, and once I got that taken care of, this came up.

Because I can still boot into XP so long as I disconnect the USB drive before boot up, this is not a crucial issue.  However, I am really curious to figure out what is going on.

- I've run the testdisk program - the sectors are identical
- I've run chkdsk, fixboot, & fixmbr from the XP recovery (install) disc with no issues
- I've run the 'hexdump', and the numbers are what they should be
- I can't find any problems, despite a number of hours of research online, but obviously something isn't quite right.

Let me know what info I can provide that might help, and I'll make it happen.  Thanks in advance for any help anyone can provide.

---

### Post by caljohnsmith on 2008-12-27
J_galt, my guess at this point is that your Windows entry in your Grub's menu.lst is missing the "mapping" lines that are necessary whenever you boot Windows from a drive that is not first in the BIOS boot order. But in order to get a clearer picture of your setup to see if that is the issue, how about running the script from post #9 and post the results, and we can work from there.

---

### Post by Bread Pit on 2008-12-27
Hey, just to let you (caljohnsmith) and the world know: everything works fine now.:) I've reinstalled win XP and everything is ok. :) THANK YOU!

---

### Post by caljohnsmith on 2008-12-27
> **Bread Pit said:**
> Hey, just to let you (caljohnsmith) and the world know: everything works fine now.:) I've reinstalled win XP and everything is ok. :) THANK YOU!
You're certainly welcome, and I'm really glad to hear everything is working OK. Cheers and have fun with Windows and Ubuntu. :)

---

### Post by lazman on 2008-12-29
Well, I'm not so lucky.... I tried the chkdsk /r option from the recovery console and it didn't work. It reported an unrecoverable error. Before it even started. In an attempt to get windows working I tried FixBoot thinking that if it failed to fix it I could simply reinstall grub and back everything up from my windows partition to another computer using Ubuntu. But now the partitions themselves are messed up. From the live CD I looked at the partition and it's reporting I have a 1.7Tb hard drive! I know for a fact that it's only 250GB. It will not allow me to mount it so I can get the files off of it that I want to keep.

I know to fix this I'm going to have to do a low level format on the hard drive and start all over. But before I do that, is there another solution that will hopefully allow me to backup files from the windows partition so that I do not loose them?

I have already ran the Seagate software and there is nothing wrong with the hard drive. It passed every test. I'm rather aggravated at the fact that Ubuntu has led to a low level format and reinstall however, I am willing to give it another shot. I just would like to save the pictures and source code that I have on the windows partition if at all possible.

Thanks
~laz

---

### Post by lazman on 2008-12-29
Well, it looks like short of installing another hard drive and trying some kind of data recovery software I'm out of luck. I think with the drive reporting that it's 1.7TB instead of 250GB most if not all of the free data recovery software will most likely fail. At this point I'm not willing to spend the money or time it's probably going to take to get the files off of the hard drive. I think I will just face the fact that they are gone and start the reformating and installation of windows and Ubuntu again. I'm thinking at this point that a second hard drive for source code and pictures would be a good idea however.

Thanks for the help!
~laz

---

### Post by caljohnsmith on 2008-12-29
Lazman, how about posting the output of:
```
sudo fdisk -lu
```
And we can go from there.

EDIT: I didn't see your last post, if you don't want to mess with it that's certainly OK too.

---

### Post by lazman on 2008-12-29
Well, I have windows installed and updated. I'm going to try to install ubuntu again. I only used about 130gig of the 250gig hd for windows this time. The rest of it is all zeros. So there will be no partition resizing this time around. Just the making of a new one. Maybe everything will go well. 

I think that thing about it reporting that the hd was 1.7Tb was strange. I used the seagate dos software to zero the whole 250gig and setup the 130gig partition for ntfs. Thanks for your response but, I really had my doubts about getting any of that data back. I have just tossed it up as the price I'm paying for messing with OS's. I will most likely get a second hd to store files on now. That way if things go south like that again it's a simple decision and alot of time saved trying to salvage what is on the disk.

Wish me luck haha
~laz

---

### Post by lazman on 2008-12-29
Well, everything went well on that install. I'm still not sure what went wrong with the last install. I don't know if it was just one of those things or, if it was something I did wrong. All in all it wasn't so bad I guess. I lost some time on the source code and lost a few photos, but it was a good learning experience. Perhaps if it had happened a couple of months ago before I decided to back everything up and do the ritual yearly reinstall of windows it would have been worse of a loss. 

I have installed different releases over the last couple of years a few weeks before I decide to reinstall windows. And I have to say, despite this issue this is the best release I have installed thus far. Now perhaps I can get down to learning how to use linux. There is much to be learned, but this nice interface is making it so much easier. It's fast, it works, and there are nice people that are willing to help with a quick and helpful response. You can't ask for more than that!

Thanks for all your help!
~laz

---

### Post by caljohnsmith on 2008-12-30
Glad to hear your system is up-and-running again; I hope you don't run into any other major obstacles. Cheers and have fun with your OSes. :)

---

### Post by Heliman5 on 2009-01-01
Hi there, Maybe I should start a new thread for this but I think I have a similar problem. When I try to boot XP It says:
--------------------------------------
starting up

disk read error encountered
Press ctrl, alt, del to restart
--------------------------------------
This sounds like it might fall into the "really bad" catagory. :(
any Help would be appreciated!

--------------------------------------------------------------------------------------
I forgot, Here Is My "RESULTS.txt" (post 9):
I have a kinda weird setup that may be causing this, however it did boot for a while.
NOTE. (sda,1) is small (8MB) "boot" partition for XP. the rest is on raid array (sdb-sdc)

============================= Boot Info Summary: ==============================

 => Grub is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for its boot files.
 => Grub is installed in the MBR of /dev/sdb and looks on boot drive #3 in 
    partition #3 for its boot files.
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP                                             
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       swap

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  Ubuntu 8.04.1
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sdb1: _________________________________________________________________________

    File system:                                                                
    Boot sector type:  Windows XP
    Mounting failed:
mount: you must specify the filesystem type

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xbc4fbc4f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63       16064        8001    7  HPFS/NTFS                
/dev/sda2       311596740   312576704      489982+  82  Linux swap / Solaris
/dev/sda3           16065   311596739   155790337+  83  Linux

Partition table entries are not in disk order

sfdisk -V /dev/sda:

/dev/sda: OK

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

Disk /dev/sdb: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders, total 160836480 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0009ed43

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   321637364   160818651    7  HPFS/NTFS

sfdisk -V /dev/sdb:

Warning: partition 1 extends past end of disk                                    

Drive sdc: _____________________________________________________________________

fdisk -lu /dev/sdc:

Disk /dev/sdc: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders, total 160836480 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000


sfdisk -V /dev/sdc:


sfdisk: ERROR: sector 0 does not have an msdos signature
 /dev/sdc: unrecognized partition table type

sfdisk: no partition table present.

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="2A702ACE702AA115" TYPE="ntfs" 
/dev/sda2: TYPE="swap" UUID="36447ff0-40ec-4840-8b1a-ee4fb30512fa" 
/dev/sda3: UUID="fbb79228-2ffd-4324-859c-7be1dce4cc34" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/sda3 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-22-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/wes/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=wes)

================================ sda1/boot.ini: ================================

[boot loader]

timeout=1

default=multi(0)disk(0)rdisk(1)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=========================== sda3/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=fbb79228-2ffd-4324-859c-7be1dce4cc34 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=fbb79228-2ffd-4324-859c-7be1dce4cc34 ro quiet splash
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=fbb79228-2ffd-4324-859c-7be1dce4cc34 ro single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=fbb79228-2ffd-4324-859c-7be1dce4cc34 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=fbb79228-2ffd-4324-859c-7be1dce4cc34 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Microsoft Windows XP Professional
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1


=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc3
UUID=fbb79228-2ffd-4324-859c-7be1dce4cc34 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdc2
UUID=36447ff0-40ec-4840-8b1a-ee4fb30512fa none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

================================== sda3/boot: ==================================

total 36396
drwxr-xr-x  3 root root    4096 2008-12-27 02:15 .
drwxr-xr-x 21 root root    4096 2009-01-01 12:29 ..
-rw-r--r--  1 root root  422667 2008-08-20 23:46 abi-2.6.24-19-generic
-rw-r--r--  1 root root  422838 2008-11-24 16:47 abi-2.6.24-22-generic
-rw-r--r--  1 root root   80049 2008-08-20 23:46 config-2.6.24-19-generic
-rw-r--r--  1 root root   80062 2008-11-24 16:47 config-2.6.24-22-generic
drwxr-xr-x  2 root root    4096 2009-01-01 16:19 grub
-rw-r--r--  1 root root 7495523 2008-12-27 02:11 initrd.img-2.6.24-19-generic
-rw-r--r--  1 root root 7885399 2008-12-26 10:29 initrd.img-2.6.24-19-generic.bak
-rw-r--r--  1 root root 7496475 2008-12-27 02:15 initrd.img-2.6.24-22-generic
-rw-r--r--  1 root root 7496381 2008-12-27 02:12 initrd.img-2.6.24-22-generic.bak
-rw-r--r--  1 root root  103204 2007-09-28 05:06 memtest86+.bin
-rw-r--r--  1 root root  905170 2008-08-20 23:46 System.map-2.6.24-19-generic
-rw-r--r--  1 root root  905617 2008-11-24 16:47 System.map-2.6.24-22-generic
-rw-r--r--  1 root root 1921464 2008-08-20 23:46 vmlinuz-2.6.24-19-generic
-rw-r--r--  1 root root 1921176 2008-11-24 16:47 vmlinuz-2.6.24-22-generic

=============================== sda3/boot/grub: ===============================

total 212
drwxr-xr-x 2 root root   4096 2009-01-01 16:19 .
drwxr-xr-x 3 root root   4096 2008-12-27 02:15 ..
-rw-r--r-- 1 root root    197 2008-12-26 10:29 default
-rw-r--r-- 1 root root     45 2008-12-26 10:29 device.map
-rw-r--r-- 1 root root   8056 2008-12-26 10:29 e2fs_stage1_5
-rw-r--r-- 1 root root   7904 2008-12-26 10:29 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-12-26 10:29 installed-version
-rw-r--r-- 1 root root   8608 2008-12-26 10:29 jfs_stage1_5
-rw-r--r-- 1 root root   5048 2009-01-01 16:19 menu.lst
-rw-r--r-- 1 root root   5048 2008-12-29 17:09 menu.lst~
-rw-r--r-- 1 root root   7324 2008-12-26 10:29 minix_stage1_5
-rw-r--r-- 1 root root   9632 2008-12-26 10:29 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-12-26 10:29 stage1
-rw-r--r-- 1 root root 108356 2008-12-26 10:29 stage2
-rw-r--r-- 1 root root   9276 2008-12-26 10:29 xfs_stage1_5

=============================== StdErr Messages: ===============================

Disk /dev/sdc doesn't contain a valid partition table

---

### Post by caljohnsmith on 2009-01-01
Heliman5, how about running the script and posting the output:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your problem might be.

---

### Post by Heliman5 on 2009-01-01
Sorry about the Code tags (or lack thereof).
 I was unable to run the code you posted. All I got was an HTML file named "error_404.html" I think My internet Is messed up, I cant download anything on my laptop ether.

---

### Post by caljohnsmith on 2009-01-01
> **Heliman5 said:**
> Sorry about the Code tags (or lack thereof).
 I was unable to run the code you posted. All I got was an HTML file named "error_404.html"
Sorry, please try again, I fixed the problem so the script is back in place on the server.

---

### Post by Heliman5 on 2009-01-01
thanks, here are the results

```
============================= Boot Info Summary: ==============================

 => Grub is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for its boot files.
 => Grub is installed in the MBR of /dev/sdb and looks on boot drive #3 in 
    partition #3 for its boot files.
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       swap

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  Ubuntu 8.04.1
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sdb1: _________________________________________________________________________

    File system:       
    Boot sector type:  Windows XP
    Mounting failed:
mount: you must specify the filesystem type

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xbc4fbc4f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63       16064        8001    7  HPFS/NTFS
/dev/sda2       311596740   312576704      489982+  82  Linux swap / Solaris
/dev/sda3           16065   311596739   155790337+  83  Linux

Partition table entries are not in disk order

sfdisk -V /dev/sda:

/dev/sda: OK

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

Disk /dev/sdb: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders, total 160836480 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0009ed43

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   321637364   160818651    7  HPFS/NTFS

sfdisk -V /dev/sdb:

Warning: partition 1 extends past end of disk

Drive sdc: _____________________________________________________________________

fdisk -lu /dev/sdc:

Disk /dev/sdc: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders, total 160836480 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000


sfdisk -V /dev/sdc:


sfdisk: ERROR: sector 0 does not have an msdos signature
 /dev/sdc: unrecognized partition table type

sfdisk: no partition table present.

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="2A702ACE702AA115" TYPE="ntfs" 
/dev/sda2: TYPE="swap" UUID="36447ff0-40ec-4840-8b1a-ee4fb30512fa" 
/dev/sda3: UUID="fbb79228-2ffd-4324-859c-7be1dce4cc34" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/sda3 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-22-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/wes/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=wes)

================================ sda1/boot.ini: ================================

[boot loader]

timeout=1

default=multi(0)disk(0)rdisk(1)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=========================== sda3/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=fbb79228-2ffd-4324-859c-7be1dce4cc34 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=fbb79228-2ffd-4324-859c-7be1dce4cc34 ro quiet splash
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=fbb79228-2ffd-4324-859c-7be1dce4cc34 ro single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Microsoft Windows XP Professional
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1



=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc3
UUID=fbb79228-2ffd-4324-859c-7be1dce4cc34 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdc2
UUID=36447ff0-40ec-4840-8b1a-ee4fb30512fa none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

================================== sda3/boot: ==================================

total 36396
drwxr-xr-x  3 root root    4096 2008-12-27 02:15 .
drwxr-xr-x 21 root root    4096 2009-01-01 20:43 ..
-rw-r--r--  1 root root  422667 2008-08-20 23:46 abi-2.6.24-19-generic
-rw-r--r--  1 root root  422838 2008-11-24 16:47 abi-2.6.24-22-generic
-rw-r--r--  1 root root   80049 2008-08-20 23:46 config-2.6.24-19-generic
-rw-r--r--  1 root root   80062 2008-11-24 16:47 config-2.6.24-22-generic
drwxr-xr-x  2 root root    4096 2009-01-01 22:15 grub
-rw-r--r--  1 root root 7495523 2008-12-27 02:11 initrd.img-2.6.24-19-generic
-rw-r--r--  1 root root 7885399 2008-12-26 10:29 initrd.img-2.6.24-19-generic.bak
-rw-r--r--  1 root root 7496475 2008-12-27 02:15 initrd.img-2.6.24-22-generic
-rw-r--r--  1 root root 7496381 2008-12-27 02:12 initrd.img-2.6.24-22-generic.bak
-rw-r--r--  1 root root  103204 2007-09-28 05:06 memtest86+.bin
-rw-r--r--  1 root root  905170 2008-08-20 23:46 System.map-2.6.24-19-generic
-rw-r--r--  1 root root  905617 2008-11-24 16:47 System.map-2.6.24-22-generic
-rw-r--r--  1 root root 1921464 2008-08-20 23:46 vmlinuz-2.6.24-19-generic
-rw-r--r--  1 root root 1921176 2008-11-24 16:47 vmlinuz-2.6.24-22-generic

=============================== sda3/boot/grub: ===============================

total 224
drwxr-xr-x 2 root root   4096 2009-01-01 22:15 .
drwxr-xr-x 3 root root   4096 2008-12-27 02:15 ..
-rw-r--r-- 1 root root    197 2008-12-26 10:29 default
-rw-r--r-- 1 root root     45 2008-12-26 10:29 device.map
-rw-r--r-- 1 root root   8056 2008-12-26 10:29 e2fs_stage1_5
-rw-r--r-- 1 root root   7904 2008-12-26 10:29 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-12-26 10:29 installed-version
-rw-r--r-- 1 root root   8608 2008-12-26 10:29 jfs_stage1_5
-rw-r--r-- 1 root root      1 2009-01-01 22:00 menu.1st
-rw-r--r-- 1 root root   4617 2009-01-01 22:15 menu.lst
-rw-r--r-- 1 root root   4575 2009-01-01 22:07 menu.lst~
-rw-r--r-- 1 root root   5048 2009-01-01 22:05 menu.lst.old
-rw-r--r-- 1 root root   7324 2008-12-26 10:29 minix_stage1_5
-rw-r--r-- 1 root root   9632 2008-12-26 10:29 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-12-26 10:29 stage1
-rw-r--r-- 1 root root 108356 2008-12-26 10:29 stage2
-rw-r--r-- 1 root root   9276 2008-12-26 10:29 xfs_stage1_5

=============================== StdErr Messages: ===============================

Disk /dev/sdc doesn't contain a valid partition table
```

By the way, I just tried booting from the Super grub flopy disk and that worked!

```
rootnoverify (hd0,0)
chainloader +1
boot

```

I should have tried that long ago!
is it possible to just copy that into the menu.lst file?

---

### Post by caljohnsmith on 2009-01-02
So you're sure that you can boot Windows OK with that entry you gave? Because currently your Windows boot.ini file uses rdisk(1) and not rdisk(0), and the latter should work to boot Windows from the first boot drive like you are doing. But if it works, I'm certainly not going to argue. :) To modify your menu.lst you can do:
```
gksudo gedit /boot/grub/menu.lst
```
And just change the Windows entry near the bottom to the Super Grub entry that worked to boot Windows (you don't need the "boot" line):
```
title Windows XP
rootnoverify (hd0,0)
chainloader +1

```
Save, reboot, and make sure it works. If it still works OK, please let me know, because as I mentioned, I'm a little surprised it would work with the Windows boot.ini configured the way it is. :)

---

### Post by Heliman5 on 2009-01-02
Yup, works fine. believe me I was as suprised as anyone when I poped the disk in and it worked! menu.lst must have got messed up when i changed things to make ubuntu boot. Well, I guess sometimes desperation is the best insperation.

---

### Post by Heliman5 on 2009-01-02
Im not sure why boot.ini says rdisk(1) when i installed windows (before ubuntu) I wanted to install compleatly on the raid array. but the installer wanted at least a 8MB partition on the first drive, so thats what i did. is boot.ini using files on rdisk(1) to boot because they won't fit on the first disk?  thats the only thing I can think of.

---

### Post by caljohnsmith on 2009-01-02
> **Heliman5 said:**
> Im not sure why boot.ini says rdisk(1) when i installed windows (before ubuntu) I wanted to install compleatly on the raid array. but the installer wanted at least a 8MB partition on the first drive, so thats what i did. is boot.ini using files on rdisk(1) to boot because they won't fit on the first disk?  thats the only thing I can think of.
You're right, I missed the fact that your Windows is actually installed on sdb1 and not sda1, because the script couldn't mount your sdb1 partition. In that case it makes perfect sense then why "rdisk(1)" works; although if you wanted to, you could move all your Windows boot files (boot.ini, ntldr, NTDETECT.COM) from your sda1 partition to your sdb1 Windows partition, reconfigure boot.ini for "rdisk(0)", and then you could boot Windows directly from the sdb drive rather than booting your sda1 partition. Or if you are OK with leaving Windows boot files in your sda1 partition, there's nothing wrong with that.

---

### Post by Heliman5 on 2009-01-02
>  if you wanted to, you could move all your Windows boot files (boot.ini, ntldr, NTDETECT.COM) from your sda1 partition to your sdb1 Windows partition, reconfigure boot.ini for "rdisk(0)", and then you could boot Windows directly from the sdb drive rather than booting your sda1 partition. I will keep that in mind, but for now everything works and I am not changing anything! :)
thank you for your time and patience, 
     Heliman5

---

