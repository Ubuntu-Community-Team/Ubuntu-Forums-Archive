---
title: "Not able to boot ubuntu"
date: 2009-03-18
forum: Installation &amp; Upgrades
---

### Post by bbsrmm on 2009-03-18
I have upgraded WubiUbuntu to clean install through LVPM yesterday. Today I have worked in Ubuntu environment and saved some files. but rebooting again after sometime i am not able access ubuntu.After system starts grub comes to the screen having list of Ubuntu version and also window operating system.Once I select and enter any of the Ubuntu verion it gives Error 17:"Can not mount selected partition". But when window is selected and entered window OS starts. please help as i don't want to go for fresh install of Ubuntu which will wipe out my all saved documents.

---

### Post by meierfra. on 2009-03-18
Try this:

At the grub menu at boot up, press 'c'. Type

```
   find /boot/grub/stage2 
```

The output is of the form (hdX,Y), where X and Y are some numbers. For example (hd2,3).
 (If you have a separated /boot partition, use  'find /grub/stage2')

Remember the output and press 'esc'  to get back to the Grub Menu.

Select Ubuntu. But don't press 'enter', press 'e' instead.  At the new screen press
'e'  again. Change 

root (hd?,?)

 to  

root (hdX,Y)    #use the numbers from  'find /boot/grub/stage2'

Press 'enter' and then  'b' to boot.


This should boot you into Ubuntu. Once you successfully booted into Ubuntu
you need to make these changes permanent. Open a terminal
(Application->Accessories->Terminal) and type


```
 cd /boot/grub
sudo cp menu.lst menu.lst.bu
gksudo gedit menu.lst

```

Look for the line 

#groot (hd?,?)


and change it to

#groot (hdX,Y)  #again, use the numbers from  'find /boot/grub/stage2'

Save the file. Back in the  terminal:

```
 sudo update-grub
```

---

### Post by bbsrmm on 2009-03-19
I have done this but ubuntu is not booting.when I have the find command it displayed two number hd0,6 and hd0,8.As per the suggestion i have done for hd0,6 and done the rest of the thing in the above code. when rebooted I have got Linux Mint screen and I can enter the system through Linux Mint.When browes the file system i can check the home of Ubuntu is available.when i open the menu.lst of ubuntu system it is seen that hd0,5 is booting address.But this address is not displayed when find command is given as per suggestion above,please help me to way out.

---

### Post by meierfra. on 2009-03-19
In order to get a clearer picture of your setup, I suggest to boot into Linux Mint and  download the Boot Info Script to  your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by bbsrmm on 2009-03-19
As per the suggestion i have genrated the result.txt and same is attached below

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #7 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr

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

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Linux Mint 6 Felicia
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda9: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.2
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda10: _________________________________________________________________________

    File system:       swap
    Boot sector type:  Unknown
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x31a431a3

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    64,259,999    64,259,937   7 HPFS/NTFS
/dev/sda2          64,260,000   234,420,479   170,160,480   f W95 Ext d (LBA)
/dev/sda5          64,260,063    76,822,829    12,562,767   7 HPFS/NTFS
/dev/sda6         146,175,498   234,420,479    88,244,982   7 HPFS/NTFS
/dev/sda7          76,822,893   112,294,349    35,471,457  83 Linux
/dev/sda8         143,235,603   146,175,434     2,939,832  82 Linux swap / Solaris
/dev/sda9         112,294,413   139,331,744    27,037,332  83 Linux
/dev/sda10        139,331,808   143,235,539     3,903,732  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="188CFF928CFF6920" TYPE="ntfs" 
/dev/sda5: UUID="6A84AD5984AD2891" TYPE="ntfs" 
/dev/sda6: UUID="AEDC0488DC044CD1" LABEL="New Volume" TYPE="ntfs" 
/dev/sda7: UUID="e57c57b1-8d9d-4007-be02-107c1374b081" TYPE="ext3" 
/dev/sda8: TYPE="swap" UUID="68fee6eb-e02b-4680-aaf7-b7e817324296" 
/dev/sda9: UUID="b5a0c308-6e0e-4ec0-9fda-28b0a553d6c6" TYPE="ext3" 
/dev/sda10: TYPE="swap" UUID="aa1aefc1-afc9-4316-8861-1650f0258777" 

=============================== "mount" output: ===============================

/dev/sda7 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/mukesh/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=mukesh)
/dev/sda9 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=15

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptOut



c:\ubnldr.mbr="UNetbootin-partitionmanagerrev146"


=========================== sda7/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## Graphical boot menu location
gfxmenu=/boot/gfxmenu/default.message

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=/dev/sda7 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,6)

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
##      altoptions=(single-user) single
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

title		Linux Mint 6, kernel 2.6.27-7-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.27-7-generic root=/dev/sda7 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Linux Mint 6, kernel 2.6.27-7-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.27-7-generic root=/dev/sda7 ro single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Linux Mint 6, kernel Last successful boot
root		(hd0,6)
kernel		/boot/last-good-boot/vmlinuz root=/dev/sda7 ro quiet splash  last-good-boot
quiet

title		Linux Mint 6, memtest86+
root		(hd0,6)
kernel		/boot/memtest86+.bin
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic

root		(hd0,5)/ubuntu/disks

kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=AEDC0488DC044CD1 loop=/ubuntu/disks/root.disk ro quiet splash

initrd		/boot/initrd.img-2.6.24-23-generic
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


=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=e57c57b1-8d9d-4007-be02-107c1374b081 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda8
UUID=1b58ef18-aaa0-4974-8859-1dcc2b41d17a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda7: Location of files loaded by Grub: ===================


  39.3GB: boot/grub/menu.lst
  39.3GB: boot/grub/stage2
  39.3GB: boot/initrd.img-2.6.27-7-generic
  39.3GB: boot/vmlinuz-2.6.27-7-generic
  39.3GB: initrd.img
  39.3GB: vmlinuz

=========================== sda9/boot/grub/menu.lst: ===========================

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
color blink-cyan/green blink-white/brown

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
# kopt=root=UUID=AEDC0488DC044CD1 loop=/ubuntu/disks/root.disk ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)/ubuntu/disks

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

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		(hd0,5)/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=AEDC0488DC044CD1 loop=/ubuntu/disks/root.disk ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,5)/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=AEDC0488DC044CD1 loop=/ubuntu/disks/root.disk ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.2, kernel 2.6.24-16-generic
root		(hd0,5)/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=AEDC0488DC044CD1 loop=/ubuntu/disks/root.disk ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.2, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,5)/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=AEDC0488DC044CD1 loop=/ubuntu/disks/root.disk ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.2, memtest86+
root		(hd0,5)/ubuntu/disks
kernel		/boot/memtest86+.bin

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
chainloader	+1


=============================== sda9/etc/fstab: ===============================

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc        defaults    0   0
# /dev/sda9
UUID=b5a0c308-6e0e-4ec0-9fda-28b0a553d6c6     /               ext3        defaults,errors=remount-ro    0   1
# /dev/sda6
UUID=AEDC0488DC044CD1       /media/drv0       ntfs-3g         defaults      0   0


# /dev/sda8
UUID=68fee6eb-e02b-4680-aaf7-b7e817324296      none            swap        sw          0   0


=================== sda9: Location of files loaded by Grub: ===================


  66.7GB: boot/grub/menu.lst
  66.8GB: boot/grub/stage2
  66.6GB: boot/initrd.img-2.6.24-16-generic
  66.6GB: boot/initrd.img-2.6.24-16-generic.bak
  60.1GB: boot/initrd.img-2.6.24-23-generic
  66.6GB: boot/initrd.img-2.6.24-23-generic.bak
  66.6GB: boot/vmlinuz-2.6.24-16-generic
  66.6GB: boot/vmlinuz-2.6.24-23-generic
  60.1GB: initrd.img
  66.6GB: initrd.img.old
  66.6GB: vmlinuz
  66.6GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda10

00000000  20 20 69 64 3d 22 6c 69  6e 65 61 72 47 72 61 64  |  id="linearGrad|
00000010  69 65 6e 74 36 35 34 32  22 0a 20 20 20 20 20 20  |ient6542".      |
00000020  20 78 31 3d 22 32 32 2e  38 37 35 30 30 31 22 0a  | x1="22.875001".|
00000030  20 20 20 20 20 20 20 79  31 3d 22 33 33 2e 30 33  |       y1="33.03|
00000040  31 35 33 38 22 0a 20 20  20 20 20 20 20 78 32 3d  |1538".       x2=|
00000050  22 34 35 2e 38 39 37 30  31 34 22 0a 20 20 20 20  |"45.897014".    |
00000060  20 20 20 79 32 3d 22 33  33 2e 30 33 31 35 33 38  |   y2="33.031538|
00000070  22 0a 20 20 20 20 20 20  20 67 72 61 64 69 65 6e  |".       gradien|
00000080  74 55 6e 69 74 73 3d 22  75 73 65 72 53 70 61 63  |tUnits="userSpac|
00000090  65 4f 6e 55 73 65 22 20  2f 3e 0a 20 20 20 20 3c  |eOnUse" />.    <|
000000a0  72 61 64 69 61 6c 47 72  61 64 69 65 6e 74 0a 20  |radialGradient. |
000000b0  20 20 20 20 20 20 69 6e  6b 73 63 61 70 65 3a 63  |      inkscape:c|
000000c0  6f 6c 6c 65 63 74 3d 22  61 6c 77 61 79 73 22 0a  |ollect="always".|
000000d0  20 20 20 20 20 20 20 78  6c 69 6e 6b 3a 68 72 65  |       xlink:hre|
000000e0  66 3d 22 23 6c 69 6e 65  61 72 47 72 61 64 69 65  |f="#linearGradie|
000000f0  6e 74 36 35 35 38 22 0a  20 20 20 20 20 20 20 69  |nt6558".       i|
00000100  64 3d 22 72 61 64 69 61  6c 47 72 61 64 69 65 6e  |d="radialGradien|
00000110  74 35 38 38 39 22 0a 20  20 20 20 20 20 20 63 78  |t5889".       cx|
00000120  3d 22 33 30 2e 38 38 39  31 33 33 22 0a 20 20 20  |="30.889133".   |
00000130  20 20 20 20 63 79 3d 22  33 30 2e 32 31 38 36 33  |    cy="30.21863|
00000140  32 22 0a 20 20 20 20 20  20 20 66 78 3d 22 33 30  |2".       fx="30|
00000150  2e 38 38 39 31 33 33 22  0a 20 20 20 20 20 20 20  |.889133".       |
00000160  66 79 3d 22 33 30 2e 32  31 38 36 33 32 22 0a 20  |fy="30.218632". |
00000170  20 20 20 20 20 20 72 3d  22 36 2e 37 35 32 39 33  |      r="6.75293|
00000180  38 33 22 0a 20 20 20 20  20 20 20 67 72 61 64 69  |83".       gradi|
00000190  65 6e 74 54 72 61 6e 73  66 6f 72 6d 3d 22 6d 61  |entTransform="ma|
000001a0  74 72 69 78 28 30 2e 38  30 32 32 37 39 32 2c 30  |trix(0.8022792,0|
000001b0  2c 30 2c 30 2e 34 31 38  39 39 35 33 2c 36 2e 31  |,0,0.4189953,6.1|
000001c0  30 37 34 32 34 37 2c 31  34 2e 37 30 33 36 30 34  |074247,14.703604|
000001d0  29 22 0a 20 20 20 20 20  20 20 67 72 61 64 69 65  |)".       gradie|
000001e0  6e 74 55 6e 69 74 73 3d  22 75 73 65 72 53 70 61  |ntUnits="userSpa|
000001f0  63 65 4f 6e 55 73 65 22  20 2f 3e 0a 20 20 20 20  |ceOnUse" />.    |
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb

---

### Post by meierfra. on 2009-03-19
Just to make sure: The Grub menu which appears at boot up is the Linux Mint menu. It has various Linux Mint entries, one for Ubuntu and one for Windows. You can boot into Linux Mint and Windows, but the  Ubuntu entry gives you a grub error. Is that correct?

Anyway this should solve your problem:


Boot into Linux Mint. Open the Linux Mint menu.lst via

```
gksudo gedit /boot/grub/menu.lst
```

Replace 

```
title Ubuntu 8.04.2, kernel 2.6.24-23-generic

root (hd0,5)/ubuntu/disks

kernel /boot/vmlinuz-2.6.24-23-generic root=UUID=AEDC0488DC044CD1 loop=/ubuntu/disks/root.disk ro quiet splash

initrd /boot/initrd.img-2.6.24-23-generic
quiet
```

by

```
title Ubuntu
root (hd0,8)
kernel /boot/vmlinuz root=/dev/sda9  ro quiet splash
initrd /initrd.img
quiet
```


Save the file and reboot. The new Ubuntu entry on the Grub menu should allow you to boot into Ubuntu.

---

### Post by bbsrmm on 2009-03-19
I have changed as per the above suggestion but i get the message Error no 15: File not found.Previously I was getting Error No 17: partition does not exsit

---

### Post by meierfra. on 2009-03-19
My bad.  I meant

```
title Ubuntu
root (hd0,8)
kernel [COLOR="Red"]/vmlinuz[/COLOR] root=/dev/sda9  ro quiet splash
initrd /initrd.img
quiet
```

---

### Post by bbsrmm on 2009-03-20
Thanks a lot and it works now.But as I am very new to linux i will be grateful if you can explain the root cause of the problem.Further i want to remove linux mint from the system now,only ubuntu and Windows Xp remaining.Is this possible as I am now accessing Ubuntu through Linux min Grub menu?

---

### Post by meierfra. on 2009-03-20
> But as I am very new to linux i will be grateful if you can explain the root cause of the problem. 

Wubi stores  the boot files in  different directories than a Ubuntu. Also Wubi uses Grub4Dos instead of Grub. As a result the file /boot/grub/menu.lst needed to be edited. But this never happened.


> Is this possible as I am now accessing Ubuntu through Linux min Grub menu? 

No.  So let's put the Ubuntu grub in charge of booting.
Open  a terminal in Ubuntu  and generate a new menu.lst

```

cd /boot/grub
sudo mv menu.lst menu.lst.wubi
sudo update-grub
```


There are a few more steps, but  since you converted from Wubi, I'm not 100% that update-grub generates  the correct "menu.lst".
So please post the output of 

```
cat /boot/grub/menu.lst
```

before we continue.

---

### Post by bbsrmm on 2009-03-21
As per suggestion I am providing the menu.lst below.But before that I want to mention something.When I opened the menu.lst in some area below Ubuntu it is written (hd0,5) with some other stuff.For the first entry I have changed as per your code mentioned earlier(marked as RED),Others I have not touched.Secondly for the safety purpose I have copied the first entry of menu.lst of linux mint OS and pasted it in the last of this menu.lst(marked as RED).You can verify the same.
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
# kopt=root=UUID=AEDC0488DC044CD1 loop=/ubuntu/disks/root.disk ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)/ubuntu/disks

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

[COLOR="Red"]title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		(hd0,8)
kernel		/vmlinuz root=/dev/sda9  ro quiet splash
initrd		/initrd.img
quiet
[/COLOR]
title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,5)/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=AEDC0488DC044CD1 loop=/ubuntu/disks/root.disk ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.2, kernel 2.6.24-16-generic
root		(hd0,5)/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=AEDC0488DC044CD1 loop=/ubuntu/disks/root.disk ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.2, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,5)/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=AEDC0488DC044CD1 loop=/ubuntu/disks/root.disk ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.2, memtest86+
root		(hd0,5)/ubuntu/disks
kernel		/boot/memtest86+.bin

[COLOR="Red"]title		Linux Mint 6, kernel 2.6.27-7-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.27-7-generic root=/dev/sda7 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet[/COLOR]

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
chainloader	+1

```

---

### Post by meierfra. on 2009-03-21
I think  something went wrong, since menu.lst doesn't seem to have changed.  Anyway,  I edited menu.lst myself.

This is what I changed:

1) changed the "#kopt" line to

# kopt=root=UUID=b5a0c308-6e0e-4ec0-9fda-28b0a553d6c6  ro

2)  changed to  "#groot" line to

# groot=b5a0c308-6e0e-4ec0-9fda-28b0a553d6c6

3)   changed "#howmany=7" to

# howmany=2

(This change was optional. It makes sure that only  the two most recent kernel will be listed on the Grub menu)

4)  changed all the "root" lines to

uuid		b5a0c308-6e0e-4ec0-9fda-28b0a553d6c6

5)  changed all the kernel lines to

kernel		/boot/vmlinuz-2.6.24-23-generic  root=UUID=b5a0c308-6e0e-4ec0-9fda-28b0a553d6c6  ro quiet splash

6) Replacd the item  you had copied from the Linux Mint menu.lst by one using UUID.   But I didn't deleted that item, I moved it do the end of the file instead.  
(If you don't use uuids, you  might  run in problems then you delete the linux mint partition).

8 )  Moved the Linux Mint item towards the end of the file.  It probably does not matter in your case, since you will deleted Linux Mint anyway. But in general  other OSs should not be placed in the "automatic kernel list" area. Otherwise they will be removed during  the next kernel update.


Download the attached file "menu.txt" to your desktop.  Then

```

sudo cp ~/Desktop/menu.txt /boot/grub/menu.lst
sudo grub-install /dev/sda
``` 

Reboot and you should get the Ubuntu Grub menu.

---

### Post by bbsrmm on 2009-03-23
Thanks alot. I have copied the menu.lst as suggested above.It is working now. In the next step How I will delete the linux mint OS and add that space to Ubuntu?

---

### Post by crusaderbond on 2009-03-23
You can install gparted in ubuntu, and delete the partition linuxmint is on, then expand your ubuntu partition to fill the remaining space. That always works for me.

---

### Post by bbsrmm on 2009-03-23
how to install Gparted in ubuntu? is there is any chance of harm to system when linux mint partition is deleted? How I will know that said partition is meant of Linux Mint OS?

---

### Post by meierfra. on 2009-03-23
You won't be able to delete Linux Mint from Ubuntu, because Ubuntu cannot be mounted at the time. So  you will have the use a Live CD. gparted is already install on the Ubuntu LiveCD. But you can also use the gparted LiveCD, which sometimes works a little bit better. 

Resizing a partiton from the start point does take a long time and carries a small risk of Data loss. So you should backup all your valuable Data before hand.

Instead, I recommend to use the freed space for a Home  or Data partition.

I assume you also want to delete the swap partition (/dev/sda8 ).

Once are done partitioning you most likely have the reinstall grub. 

Just open a terminal in the LiveCD and type

```
sudo grub
```
and at the "grub" prompt

```
root (hd0,X)
setup (hd0)
quit
```

Here X is some number. Since Grub starts counting at zero, it as to be one less than the partition Ubuntu is on. So if Ubuntu is on /dev/sda7, use X=6, for /dev/sda8 use X=7 and for /dev/sda9 use X=8 (although in the last case you won't have to reinstall grub)



> How I will know that said partition is meant of Linux Mint OS?

Linux Mint is an /dev/sda7 and the Linux Mint swap partition is /dev/sda8

---

### Post by bbsrmm on 2009-03-26
Sorry for the late reply as I was out of station. The guidence you have given for deleting Linux Mint as well as adding space to Ubuntu is not understable.May I request you to guide me in the step by step manner. In the mean time I have upgraded my Ubuntu 8.04LTS to 8.10.I request you give me a step by step guide if possible screenshot for deleting linux mint and adding space to ubuntu.

---

### Post by meierfra. on 2009-03-28
** Step 1 Change the UUID of your /dev/sda10 Swap partition**

Open a terminal in Ubuntu and type:

```
sudo mkswap -U 68fee6eb-e02b-4680-aaf7-b7e817324296 /dev/sda10
```


[COLOR="Red"][SIZE="4"]Boot from the Ubuntu Live CD
[/SIZE][/COLOR]


**Step 2  Repartitioning**

Go to "System->Administration->Partition Editor" to open gparted

Right Click /dev/sda7 and choose  Unmount
Right Click /dev/sda8  and choose Swapoff
Right Click /dev/sda9 and choose  Unmount
Right Click /dev/sda10  and choose Swapoff

(If you dont have an option to "Unmount" or "Swapoff" just skip the step)

RightClick /dev/sda7 and choose "delete
RightClick  the partion which is now called /dev/sda7  (and used to be /dev/sda8 )  and choose "delete"  
RightClick the unallocated space you just created and choose "New".
  In the PopUp window under "Filesystem" choose "Ext3".
  Click on "Add"
In the  main  Gparted Window in the "Edit Menu" choose "Apply all Operations.
Close Gparted.


**Step 3 Reinstall Grub**

Open a terminal in the live CD and type 

```
sudo grub

```

and at the "grub>" prompt:

```
 
find /boot/grub/stage2 

```

This should return (hd0,6). But in the next line, use whatever was returned.

```
root (hd0,6)
setup (hd0)
quit
``` 


[COLOR="Red"][SIZE="4"]Boot into Ubuntu.[/SIZE][/COLOR]

** Step 4  Create a Mount Point for your Data partition and edit fstab**

Open a terminal and type:

```
mkdir ~/Data
sudo blkid -c /dev/null 
mount | grep /dev/sd 
```

Looking at the output of blkid and mount you should be able to determine the device name and uuid of your data partition (The Data partition should be /dev/sda9) If your are not sure what the UUID is just post the output of those two commands for help.

Open the file "fstab" via

```
gksudo gedit /etc/fstab
```

Add this line to the end of the file:

```
UUID=<the_uuid_of_your_data_partition>   /home/<your_username>/Data  ext3   realtime  0  2
```

Save the file.

Type

```
 sudo mount -a
```

and you should be able to access your new Data partition in the folder "Data" in your home folder.
Also reboot, and see whether your Data partition was automatically mounted.

---

### Post by bbsrmm on 2009-03-30
Thank you for your guidence.I have some doubt.Is it necessary to boot from the live CD to access gpart? I have already installed Gpart in the Ubuntu,can I use that without booting from the live CD?

---

### Post by meierfra. on 2009-03-30
> I have already installed Gpart in the Ubuntu,can I use that without booting from the live CD? 

To delete a logical partition, all partitions after that logical partition must be unmounted. When you are booted into Ubuntu, you cannot unmount the Ubuntu partition.
So the answer is  "no", you won't be able to deleted the Linux Mint partition from Ubuntu.

---

### Post by bbsrmm on 2009-03-31
Thank you for your response. I will try to do the above through live CD and let you know the result.

---

### Post by bbsrmm on 2009-03-31
[QUOTE=meierfra.;6973384]** Step 1 Change the UUID of your /dev/sda10 Swap partition**


[COLOR="Red"][SIZE="4"]I have made this swap partition .[/SIZE]
[/COLOR]

Open a terminal in Ubuntu and type:

```
sudo mkswap -U 68fee6eb-e02b-4680-aaf7-b7e817324296 /dev/sda10
```


[COLOR="Red"][SIZE="4"]Boot from the Ubuntu Live CD
[/SIZE][/COLOR]


**Step 2  Repartitioning**

Go to "System->Administration->Partition Editor" to open gparted

Right Click /dev/sda7 and choose  Unmount

[COLOR="Red"][SIZE="5"]Unmount option is not there.[/SIZE][/COLOR]

Right Click /dev/sda8  and choose Swapoff

[COLOR="Red"][SIZE="5"]Swapoff option is there.[/SIZE][/COLOR]

Right Click /dev/sda9 and choose  Unmount

[COLOR="Red"][SIZE="5"]Unmount option is not there.[/SIZE][/COLOR]

Right Click /dev/sda10  and choose Swapoff

[COLOR="Red"][SIZE="5"]Swapoff option is there.[/SIZE]
[/COLOR]

(If you dont have an option to "Unmount" or "Swapoff" just skip the step)

RightClick /dev/sda7 and choose "delete"

[COLOR="Red"][SIZE="5"]When I tried to delete there is a message Unable to delete /dev/sda7.Please unmount any logical partition having a number higher than 7.Then since there is a swapoff option i have made sda8 and sda10 swapoff.Then I was able to delete sda7.Once I deleted sda7 numbering of sda changed i.e sda8 became sda7,sda9 became sda8 and sda10 became sda9.In your next line you have advised to delete sda8 whether it means sda7 after deletion of original sda7 or sda8 after deletion of sda7.Ithink after deletion of sda7 which was previously sda9 became sda8 where Ubuntu is located.I was confused so i have undo every thing and waiting for your guidance[/SIZE].[/COLOR]

RightClick /dev/sda8 and choose "delete"

[COLOR="Red"][SIZE="5"]Is this original sda8 which became sda7 after deletion of original sda7?[/SIZE][/COLOR]

---

### Post by meierfra. on 2009-03-31
> Is this original sda8 which became sda7 after deletion of original sda7?

 Yes. (so it will be a swap partition)

Sorry for the confusion (I should have made that clear in my  direction)

---

### Post by bbsrmm on 2009-03-31
ok i will try again and inform you.

---

### Post by bbsrmm on 2009-03-31
After doing as per your above i have received this out put.Please suggest what to do next


```
/dev/sda1: UUID="188CFF928CFF6920" TYPE="ntfs" 
/dev/sda5: UUID="6A84AD5984AD2891" TYPE="ntfs" 
/dev/sda6: UUID="AEDC0488DC044CD1" LABEL="New Volume" TYPE="ntfs" 
/dev/sda7: UUID="b5a0c308-6e0e-4ec0-9fda-28b0a553d6c6" TYPE="ext3" 
/dev/sda8: TYPE="swap" UUID="68fee6eb-e02b-4680-aaf7-b7e817324296" 
/dev/sda9: UUID="ad5a0236-656f-463e-8923-43efca4205dc" SEC_TYPE="ext2" TYPE="ext3" 
mukeshmishra@mukeshmishra-laptop:~$ mount | grep /dev/sd
/dev/sda7 on / type ext3 (rw,relatime,errors=remount-ro)
/dev/sda6 on /media/drv0 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
mukeshmishra@mukeshmishra-laptop:~$ sudo mount -a
mount: wrong fs type, bad option, bad superblock on /dev/sda9,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

---

### Post by bbsrmm on 2009-03-31
I am sending the fstab lines also
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc        defaults    0   0
# /dev/sda9
UUID=b5a0c308-6e0e-4ec0-9fda-28b0a553d6c6     /               ext3        defaults,errors=remount-ro,relatime    0   1
# /dev/sda6
UUID=AEDC0488DC044CD1       /media/drv0       ntfs-3g         defaults      0   0


# /dev/sda8
UUID=68fee6eb-e02b-4680-aaf7-b7e817324296      none            swap        sw          0   0
UUID=ad5a0236-656f-463e-8923-43efca4205dc   /home/mukeshmishra/Data  ext3   realtime  0  2
```

---

### Post by meierfra. on 2009-03-31
My bad, there is a  typo in my instructions. The fstab line needs to say

"relatime"   (and not realtime)

In case the wrong entry in "fstab"  prevents you from booting into Ubuntu, you can fix the typo from the Live CD. Boot in the LiveCD, open a terminal, type
```
sudo mount /dev/sda7 /mnt
gksudo gedit /mnt/etc/fstab
```
Fix the typo. Reboot.


One more thing. Let's check  whether you swap partition is  being recognized. Type  "free" in a terminal in Ubuntu.
The last line of the output will look like

Swap:      3582444          0    3582444

The first number  needs to be  different from 0. So if the first number is 0, let me know.

---

### Post by bbsrmm on 2009-04-01
I have changed the realtime to relatime and is working now.Further to access that partition i have also used chmod command. Regarding swap it is written 1951856  16856 1935000.can I now delete linux mint entry from menu.lst?

---

### Post by bbsrmm on 2009-04-01
Is there any way to automatically direct a file created or saved to that Data partition like any pdf file directly goes to pdf directory in the home folder?

---

### Post by meierfra. on 2009-04-01
> Further to access that partition i have also used chmod command. 

Strange. Did you use "sudo mkdir ~/Data" to create the directory or just "mkdir ~/Data"


> swap it is written 1951856 16856 1935000.
Good. That means your Swap partition is configured correctly.  Just curious: How much ram to your  have?  Usually, if you have enough ram the swap gets hardly ever used. 


> Is there any way to automatically direct a file created or saved to that Data partition like any pdf file directly goes to pdf directory in the home folder?


Depends on the application you are using. Many applications remember the last folder you  used for savings. Others let you specify a default location for saving. Firefox for example lets you choose a default folder for downloading.

If your pdf application does not let you change the default folder  you could move the folder pdf to  the folder Data   and then  make ~/pdf a symlink to ~/Data/pdf:


```
cd
mv pdf Data
ln -s Data/pdf pdf
```

---

### Post by bbsrmm on 2009-04-01
I am attaching a screenshot of my disk space taken from partition editor.It can be seen that there are two unallocated space 1.4GB and 7.84 MB.How this space can be utilized or can be added to some other partition[ATTACH]108248[/ATTACH]

---

### Post by bbsrmm on 2009-04-01
> Strange. Did you use "sudo mkdir ~/Data" to create the directory or just "mkdir ~/Data"

sudo mkdir ~/Data


> How much ram to your  have?  

512 MB RAM



> If your pdf application does not let you change the default folder  you could move the folder pdf to  the folder Data   and then  make ~/pdf a symlink to ~/Data/pdf:


```
cd
mv pdf Data
ln -s Data/pdf pdf
```
 I could not follow this point

---

### Post by meierfra. on 2009-04-01
> sudo mkdir ~/Data
That explains it. My instruction said "mkdir ~/Data". The "sudo" caused the folder to be owned by "root"/ So you had to use "chown" to make yourself the owner.

> 512 MB RAM
You can run Ubuntu on 512 MBR, but getting more ram will improve  the performance.


> cd
mv pdf Data
ln -s Data/pdf pdf


"cd" just makes sure that you are working in your home directory.

"mv pdf Data" moves the folder "pdf" in your home directory to the Data partition.

"ln -s Data/pdf pdf" creates a link with the name "pdf" in your home directory. This link points to the folder "pdf" on your Data partition. So everything which is placed into "pdf" in your home directory, really ends up in the folder "pdf" on your Data partition.


> it can be seen that there are two unallocated space 1.4GB and 7.84 MB.

Don't worry about the 7.84 MB.  Its best to keep partition on "cylindrical bounds" and that sometimes causes very small amount of disk space to be wasted

You could create another partition from the 1.4 GB. But I'm not a fan of small partition. So I suggest to add the space to your Ubuntu  partition.

Boot from the Ubuntu Live CD.
Go to "System->Administration->Partition Editor" to open gparted

Right Click /dev/sda7 and choose Unmount
Right Click /dev/sda8 and choose Swapoff
Right Click /dev/sda6 and choose Unmount
(If you dont have an option to "Unmount" or "Swapoff" just skip the step)

RightClick /dev/sda8 and choose "Resize/Move.
In the PopUp window:
 click in the middle of the slider and move  the slider all the way to the right
 click on "Resize/Move"
In the main Gparted Window:
RightClick /dev/sda7 and choose "Resize/Move.
 In the PopUp window:
 click on the right end point of the slider and drag the right end point of the slider all the way to the right
 click on "Resize/Move"
In the main Gparted Window in the "Edit Menu" choose "Apply all Operations".

Since you are moving  your swap partition, the operations will take  a while to completed.

---

### Post by bbsrmm on 2009-04-01
After doing above again other commands like sudo grub etc is to be repeated as advised earlier?

---

### Post by meierfra. on 2009-04-01
> After doing above again other commands like sudo grub etc is to be repeated as advised earlier?

No. Just follow the instruction from post 33, and you should be all set.

---

### Post by bbsrmm on 2009-04-01
OK i will do now and let you know

---

### Post by bbsrmm on 2009-04-01
I have done the thing as per your advise.Screenshot after modification is attached for your comment[ATTACH]108361[/ATTACH].Thank you very much for pain taken and giving advise.For any advancement please suggest me.

---

### Post by meierfra. on 2009-04-02
Well, you increased the size of the swap partition, rather than just move it to the right.  So I suggest to shrink it:

Boot from the Ubuntu Live CD.
Go to "System->Administration->Partition Editor" to open gparted

Right Click /dev/sda7 and choose Unmount
Right Click /dev/sda8 and choose Swapoff
Right Click /dev/sda6 and choose Unmount
(If you dont have an option to "Unmount" or "Swapoff" just skip the step)

RightClick /dev/sda8 and choose "Resize/Move.
In the PopUp window:
click on the left end point of the slider and move the left end point of  slider  to the right so the the Swap partition is about 1.5GB.
Click on "Resize/Move"
In the main Gparted Window:
RightClick /dev/sda7 and choose "Resize/Move.
In the PopUp window:
click on the right end point of the slider and drag the right end point of the slider all the way to the right
click on "Resize/Move"
In the main Gparted Window in the "Edit Menu" choose "Apply all Operations".

Since you are shrinking your swap partition, the operations will take a while to completed.

---

### Post by bbsrmm on 2009-04-04
I have done as per your above advise.Now swap partition is 1.52GB and sda7 partition is 14.64GB.I am attaching the screen shot of the same.[ATTACH]108652[/ATTACH], here I have a question dev/sda5 have 5.99GB which is a very small partition.Can it be merged with sda1 or sda9 (either with windows or linux Data partition)?

---

### Post by meierfra. on 2009-04-04
To merge  /dev/sd5 with another partition, you will have to deleted it. (so you should move anything from that partition, which you want to keep, to a different partition)

Again you will have to use LiveCD to do the partitioning:

Use Unmount/Swapoff on all  the partition.

Delete /dev/sda5/

**To merge /dev/sda5 with your home partition:**  Just enlarge the home partition.

**To merge /dev/sda5 with /dev/sda1:** 
Shrink  the extended partition  dev/sda2 as much as possible.
Then enlarge /dev/sda1.


In either case, reinstall grub with the method from Step 3 in post #18

---

### Post by bbsrmm on 2009-04-04
ok i will do like that and let you know

---

### Post by bbsrmm on 2009-04-04
another question how to numlock on during login.I am using ubuntu8.04 in my home computer

---

