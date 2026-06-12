---
title: "Unable to Boot to Newly Installed Ubuntu"
date: 2009-06-04
forum: Installation &amp; Upgrades
---

### Post by xxdjsethxx on 2009-06-04
I am Unable to Boot to Newly Installed Ubuntu.

I have 4 Hard Drivers in my computer system, I'll give you alittle information before I give my issue.

Main HD: Ubuntu 9.0.4
2nd HD: Storage
3rd: HD: Storage
4th HD: Windows Vista x64 

(main drive is where I have installed Ubuntu and everything went fine during the installation) I was able to boot from CD before installation and go through the partition setup and make sure it installed onto my Main HD. After installing, and rebooting the system I took the CD out as it request, and reboot my system.
Upon bootup it tries to Boot from the CD still. 

I already played around to make sure it wasn't because how I might have my bootup in my Bios, so I changed it to Boot to Main HD 1st, also changed it around so it wouldn't even try to boot to the CD. I have tried booting into the CD and then going to boot to drive, and it just hangs as it is booting.
I have also hit F11 to choose the hard drive manally to boot to the Main HD and still get the same issue with trying to Boot to the CD.
However if I want to Boot into Vista I just select that drive and it boots perfectly fine into that OS.

I did remove ubuntu and try reinstalling again to make sure it wasn't a bad installation, I also ran a check on the disc to make sure it was ok, and it was. When installing the 2nd time it shown that the HD I was installing to had Ubuntu on it already, so it's seeing it as being there just everything I try and boot my system it goes directly to the CD instead of the HD1. As I said I have played w/ the bios and made sure it was not booting directly to CD, and switched around to see if I could get this corrected before posting here. I have done some searching but couldn't find any help topics on a issue like this.

So any help is needed!
Thanks

---

### Post by utnubuuser on 2009-06-04
show the output of > sudo fdisk -las well as the output from> less /boot/grub/menu.lst

---

### Post by xxdjsethxx on 2009-06-04
I was only able to boot to the Live CD to show you this..

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa02fa02f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24791   199133676    7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9725    78116031    7  HPFS/NTFS

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5a6ac646

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       13995   112414806   83  Linux
/dev/sdc2           13996       14593     4803435    5  Extended
/dev/sdc5           13996       14593     4803403+  82  Linux swap / Solaris

Disk /dev/sdd: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0342bc4e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       24321   195358401    7  HPFS/NTFS
ubuntu@ubuntu:~$ 


I was unable to do the less /boot/grub/menu.lst

---

### Post by lindsay7 on 2009-06-04
Try typing gedit /boot/grub/menu.lst   that is a letter l not the number 1. For some reason I am having a hard time getting the "less" command to work. Just be sure you do not  change anything in the grub menu file.

From what you show here, Ubuntu is on the third hard drive and windows is on the fourth.

Post the output of the grub menu and we can go from there.

---

### Post by xxdjsethxx on 2009-06-04
BTW when I log on via the Live CD , I am able to see the drive that Ubuntu is installed to, and browse the directories and everything if this helps in anyway.

I'll stay booted into the LIveCD and keep a eye on this forum for some help

---

### Post by xxdjsethxx on 2009-06-04
was unable to access it by the terminal but was able to open the file directly.

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
timeout        10

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
# kopt=root=UUID=e90c3405-3ab0-4244-9f46-b6038cb0b600 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=e90c3405-3ab0-4244-9f46-b6038cb0b600

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

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        e90c3405-3ab0-4244-9f46-b6038cb0b600
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=e90c3405-3ab0-4244-9f46-b6038cb0b600 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        e90c3405-3ab0-4244-9f46-b6038cb0b600
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=e90c3405-3ab0-4244-9f46-b6038cb0b600 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        e90c3405-3ab0-4244-9f46-b6038cb0b600
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Windows Vista (loader)

---

### Post by lindsay7 on 2009-06-04
Are you sure that you copied all of the grub file. You are missing some lines at the end. This could be  the problem.

---

### Post by xxdjsethxx on 2009-06-04
I checked again and yea a total of 166 lines. I have installed Ubuntu twice already and already did a scan on the cd and got no issues on that side. I am clueless right now =/ it's been years since I even used a Linux Based OS (I think last time was around 2002 or so and was red hat I think LOL)

---

### Post by lindsay7 on 2009-06-04
Ok, I looked again and I am not sure where your windows is but the end of the windows loader indicates that is on sdb or disk two. Add these lines to the end of the file using the gedit command and save the file and reboot.


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title          Windows Vista (loader)
rootnoverify   (hd1,0)
savedefault    
makeactive
map            (hd0) (hd1)
map            (hd1) (hd0)
chainloader    +1

---

### Post by xxdjsethxx on 2009-06-04
I looked again and yea It does have

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Windows Vista (loader)
rootnoverify    (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1


already on there, I guess the paste limited to how much I could paste/copy

---

### Post by lindsay7 on 2009-06-04
Well, I was hoping that was the fix. Lets take a look a little deeper.

Can you do this, it will give us all the info about you machine,

Please download this and place it on your Desktop in Ubuntu:

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

You will have you run it, so that we can gather more information about your hard drive setup and boot process to troubleshoot the problem more clearly.

After you download it to the Desktop, right-click it and click Properties, then click the Permissions tab and check the box at the bottom of the window that 'allows executing'.

Then click the Applications menu at the top right of your screen, followed by the Accessories menu and then click Terminal. A black window will come up, in it type the following commands, ending each line with a press of the Enter key:

Code:

cd ~/Desktop
sudo ./boot*.sh

Please remember that in Linux, everything is case sensitive. Therefore, a lowercase 'd' is different than an uppercase 'D'. Also, you will be prompted for the password you gave when you installed Ubuntu whenever you use the 'sudo' command. The 'sudo' command escalates privileges and in this case is needed to properly view the hard drives and boot process.

After you have done this, it should place a Results.txt file on your desktop. Double-click that file and select Edit->Copy. Then return here and start a new reply message. In this message, click the # sign at the top of the message editor box and this will give you CODE tags; click between these tags ({code]here[/code}) and paste the contents that you copied from the Result

---

### Post by xxdjsethxx on 2009-06-04
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #3 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
 => No known boot loader is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /grldr

sdc1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa02fa02f

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   398,267,414   398,267,352   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe686f016

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   156,232,124   156,232,062   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5a6ac646

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   224,829,674   224,829,612  83 Linux
/dev/sdc2         224,829,675   234,436,544     9,606,870   5 Extended
/dev/sdc5         224,829,738   234,436,544     9,606,807  82 Linux swap / Solaris


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0342bc4e

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *             63   390,716,864   390,716,802   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="08C475D6C475C68A" LABEL="Storage2" TYPE="ntfs" 
/dev/sdb1: UUID="A234126934124129" TYPE="ntfs" 
/dev/sdc1: UUID="e90c3405-3ab0-4244-9f46-b6038cb0b600" TYPE="ext3" 
/dev/sdc5: UUID="14d74a37-47a4-48ce-a421-3e8f2ff8a04c" TYPE="swap" 
/dev/sdd1: UUID="BC2020BF2020830E" LABEL="Storage" TYPE="ntfs" 

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
/dev/sda1 on /media/Storage2 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb1 on /media/disk type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdc1 on /media/disk-1 type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sdd1 on /media/Storage type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


=========================== sdc1/boot/grub/menu.lst: ===========================

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
timeout        10

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
# kopt=root=UUID=e90c3405-3ab0-4244-9f46-b6038cb0b600 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=e90c3405-3ab0-4244-9f46-b6038cb0b600

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

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        e90c3405-3ab0-4244-9f46-b6038cb0b600
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=e90c3405-3ab0-4244-9f46-b6038cb0b600 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        e90c3405-3ab0-4244-9f46-b6038cb0b600
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=e90c3405-3ab0-4244-9f46-b6038cb0b600 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        e90c3405-3ab0-4244-9f46-b6038cb0b600
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Windows Vista (loader)
rootnoverify    (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1


=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdc1 during installation
UUID=e90c3405-3ab0-4244-9f46-b6038cb0b600 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=14d74a37-47a4-48ce-a421-3e8f2ff8a04c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdc1: Location of files loaded by Grub: ===================


  15.7GB: boot/grub/menu.lst
  15.7GB: boot/grub/stage2
  15.7GB: boot/initrd.img-2.6.28-11-generic
  15.7GB: boot/vmlinuz-2.6.28-11-generic
  15.7GB: initrd.img
  15.7GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdd

00000000  90 e9 7d 01 fa 33 c0 8e  d0 8e c0 8e d8 bc 00 7c  |..}..3.........||
00000010  8b f4 fb bf 00 06 b9 00  01 f3 a5 bb 20 06 ff e3  |............ ...|
00000020  90 90 be 7d 07 81 3c aa  55 75 11 e8 58 00 73 0c  |...}..<.Uu..X.s.|
00000030  e8 65 00 72 07 e8 b1 00  72 3b eb 2c be 7d 07 c7  |.e.r....r;.,.}..|
00000040  04 00 00 ba 80 00 be be  07 b9 04 00 f6 04 80 75  |...............u|
00000050  07 83 c6 10 e2 f6 eb 1d  8a 74 01 8b 4c 02 bb 00  |.........t..L...|
00000060  7c b8 01 02 cd 13 72 0d  81 3e fe 7d 55 aa 75 05  ||.....r..>.}U.u.|
00000070  ea 00 7c 00 00 be 6a 07  ac 0a c0 74 fe bb 07 00  |..|...j....t....|
00000080  b4 0e cd 10 eb f2 bb 00  7e c6 07 13 c6 47 01 00  |........~....G..|
00000090  b2 80 b8 00 e0 cd 13 c3  bf 00 7e ba f0 01 b3 a0  |..........~.....|
000000a0  e8 84 00 72 0c b1 01 e8  48 00 72 05 e8 19 00 73  |...r....H.r....s|
000000b0  16 f6 c3 10 75 05 80 cb  10 eb e5 81 fa 70 01 74  |....u........p.t|
000000c0  05 ba 70 01 eb d8 f9 c3  81 bd fe 01 55 aa 75 17  |..p.........U.u.|
000000d0  8b 75 02 81 fe be 01 77  0e 03 f7 81 3c aa 55 75  |.u.....w....<.Uu|
000000e0  06 f6 44 02 01 75 01 f9  c3 bf 00 7c b1 0a e8 01  |..D..u.....|....|
000000f0  00 c3 52 57 83 c2 02 b0  01 ee 42 8a c1 ee 42 32  |..RW......B...B2|
00000100  c0 ee 42 ee 42 8a c3 ee  42 b0 20 ee e8 33 00 ec  |..B.B...B. ..3..|
00000110  24 fd 3c 58 75 0d 83 ea  07 b9 00 01 fa f3 6d fb  |$.<Xu.........m.|
00000120  f8 eb 01 f9 5f 5a c3 52  83 c2 07 ec a8 80 75 0f  |...._Z.R......u.|
00000130  4a 8a c3 ee 42 ec 24 d0  3c 50 75 03 f8 eb 01 f9  |J...B.$.<Pu.....|
00000140  5a c3 51 8b 0e 6c 04 83  c1 12 81 c2 ff 01 ec 8a  |Z.Q..l..........|
00000150  e0 80 e4 d8 80 fc 58 74  06 3b 0e 6c 04 75 ef 81  |......Xt.;.l.u..|
00000160  ea ff 01 b9 00 20 e2 fe  59 c3 0d 0a 45 72 72 6f  |..... ..Y...Erro|
00000170  72 20 4c 6f 61 64 69 6e  67 20 4f 53 00 aa 55 00  |r Loading OS..U.|
00000180  00 e9 80 fe 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  4e bc 42 03 00 00 80 01  |........N.B.....|
000001c0  01 00 07 fe ff ff 3f 00  00 00 82 dd 49 17 00 00  |......?.....I...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by Polaris96 on 2009-06-04
ok i think i know what the problem is:

You did everything right installing the UBUNTU system.  The problem is your BIOS.  I believe the first drive booting from power on is your windows drive and that's why you can't get grub to load.

Restart your PC and watch the very first splash screen for a message saying "press xxx for setup"  Usually "xxx"  will be the DELETE key.  Hold it down until you get the Bios menu

somewhere in that menu (they're all a bit different, sorry) will be a menu item saying "device boot priority"  Select it and you will probably see CD-ROM as the first item, followed by some type of Hard drive.  

You need to know something about the ubuntu drive so you can discern it from the other hard drives available - usually the manufacturer will suffice because it normally displays in the bios menu.  Follow the directions in the setup utility (most have a help function) to alter the preference so that the Ubuntu drive has the second highest priority.  make sure the CD-ROM is always first or you will have to reset everything via setup if you need to boot off the cd-rom.

After you have finished editing the Bios setup, make sure you "save and exit" instead of just quitting or you will lose your changes.

Reboot.  you should be done.  

If you need bios help, write down the motherboard name (it should be displayed when you first power up)  and include it if you make another comment - i will try to find a pdf manual for you.

---

### Post by xxdjsethxx on 2009-06-04
k i will give this a try brb *cross fingers*

---

### Post by lindsay7 on 2009-06-04
Polaris96 is right on with is assessment. There are no problems with the install.

You may have to rotate thru the hard drives being set as the boot priority until you get the correct one.

---

### Post by xxdjsethxx on 2009-06-04
Yea I got the same issue , it kept trying to boot to cd and if I didn't have a CD in it , it kept saying invalid disk error, please insert a cd. I did go in and play with the bios (by turning the cd rom as 1st boot pri and the wd hd (which ubuntu is installed on) as the 2nd) and same issue, i changed it so the wd hd was the 1st and same issue, no matter which way I go even if I hit F11 to go to a boot selection and select the WD HD it does the same issue. I am looking for the MB info now, I believe it was a MSI MB, My Bios when booting up does not say for some reason, it does say Phoneix Award Bios 

I think the MB is a MSI K8N Neo, MS-7030

---

### Post by xxdjsethxx on 2009-06-04
It might be how I have 4 HDs in my system causing some type of error maybe during bootup w/ my bios?

I can still boot into Vista by hitting F11 and selecting the drive that Vista is on, and it boots perfectly fine.

---

### Post by PRC09 on 2009-06-04
Just a wild guess but are the drive jumpers set for master/slave/cable select for however you have them configured?

---

### Post by xxdjsethxx on 2009-06-04
I'd have to reopen it all to make sure to be honest, I am thinking of doing that anyhow and pulling out the 3 other drives and seeing if it will just boot like that, If I still have issues I have another 120gb HD sitting here which can be used for the OS. I'll give all this a try and post back.

---

### Post by Polaris96 on 2009-06-05
You can boot windows because the bios has a list of drives to peek at for OS's.  When it finds one that will run, it boots.  That's why utilities like grub and Lilo exist in the first place.  

First, BIOS looks at your CD-ROM.  IF that's empty, it checks your windows HDD, so you get windows, no prob.  BUT  Grub is on your LINUX drive, which is probably number 3 or 4 on the BIOS precedence list.  

Everything on the LINUX drives is probably cool esp since we've been going over it, here.  it looks fine to me, anyway.  but you can't GET there because BIOS sees the windows init files first and thinks, "aaahhhhhh. I should be a windows PC"  

By the way, get used to this, "first come first served," practice.  Almost all of the config files in /etc work on the same protocol.  When you start playing with IPTABLES, forgetting this rule will play hob with your internet.

The good news is you can alter this table in the bios setup utility.  Let us know where you hit the wall if this doesn't work.  I've seen this problem before (was ready to chuck a PC out the window, once ... ah, the good old days)

Don't start messing with jumpers, yet.  If your drives were incorrectly addressed, you most likely would not be able to see them at all.  Almost everything IDE uses "cable select" technology now, anyway.  This means you can tweak them from the Bios setup screen.  We'll revisit that if you can't alter the boot precedence.

---

### Post by utnubuuser on 2009-06-09
F12 at post should bring up a list of bootable drives.

---

### Post by Roxor on 2009-06-09
Hi, I'm a new user also and have the same problem.  I have 3 drives but have Windows XP and Ubuntu 9.04 (x64) installed on the same drive.  (didn't know whether to create new thread or not), followed some of the instructions so far and will post what i have.

**sudo fdisk -l**

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbdbdbdbd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24083   193446666    7  HPFS/NTFS
/dev/sda2           24084       30401    50749335    5  Extended
/dev/sda5           24084       30137    48628723+  83  Linux
/dev/sda6           30138       30401     2120548+  82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb19a9337

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121275   974141406    7  HPFS/NTFS

Disk /dev/sdc: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x42b2e01e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       48641   390708801    7  HPFS/NTFS

**boot_info_script032.sh results.txt**
```

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

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

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xbdbdbdbd

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   386,893,394   386,893,332   7 HPFS/NTFS
/dev/sda2         386,893,395   488,392,064   101,498,670   5 Extended
/dev/sda5         386,893,458   484,150,904    97,257,447  83 Linux
/dev/sda6         484,150,968   488,392,064     4,241,097  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb19a9337

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63 1,948,282,874 1,948,282,812   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x42b2e01e

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   781,417,664   781,417,602   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="14E4F53FE4F523A0" TYPE="ntfs" 
/dev/sda5: UUID="8613e443-17ac-4d2c-adb9-c757cb427b5d" TYPE="ext3" 
/dev/sda6: TYPE="swap" UUID="1b4c2aab-80ff-4a33-a63b-72d9e00d3fa3" 
/dev/sdb1: UUID="487CD0167CD0011C" LABEL="Beast" TYPE="ntfs" 
/dev/sdc1: UUID="00A8EBF6A8EBE85C" LABEL="NexStar3Drive" TYPE="ntfs" 

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
/dev/sdc1 on /media/NexStar3Drive type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda1 on /media/disk type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda5 on /media/disk-1 type ext3 (rw,nosuid,nodev,uhelper=hal)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=8613e443-17ac-4d2c-adb9-c757cb427b5d /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=1b4c2aab-80ff-4a33-a63b-72d9e00d3fa3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
=============================== StdErr Messages: ===============================

sed: can't read /media/disk-1/etc/issue: No such file or directory

```Pretty sure it hasn't written it to the MBR, but how do i go about fixing this please.  Thanks.

---

