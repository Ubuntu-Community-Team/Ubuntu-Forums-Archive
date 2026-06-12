---
title: "Ububtu 8.04 Grub Error 17"
date: 2009-06-08
forum: Installation &amp; Upgrades
---

### Post by kunks112 on 2009-06-08
I had to re-install ubuntu due to an incompatible upgrade.
After re-installing ubuntu as I did before, my grub menu appears and when I try to load Ubuntu I get the following message:

Error 17: Cannot mount selected partition

Press any key to continue..._


If I try to boot into one of my windows drives I get the following error:

Error 13: Invalid or unsupported executable format


Before I had to reinstall, I have Ubuntu, Vista and Windows 7 loading perfectly.

I do not know what to do to fix this.
I am going to boot into ubuntu live disk and post the boot_menu_list on my next post.

Can I get help please. I really need it.

---

### Post by kunks112 on 2009-06-08
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04
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

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders, total 586072368 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1bf61bf5

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   586,051,199   586,051,137   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0009aac1

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   955,498,004   955,497,942  83 Linux
/dev/sdb2         955,498,005   976,768,064    21,270,060   5 Extended
/dev/sdb5         955,498,068   976,768,064    21,269,997  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xbe7e3d69

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *          2,048 2,930,274,303 2,930,272,256   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="40BC2AF2BC2AE1E0" TYPE="ntfs" 
/dev/sdb1: UUID="dd022a17-eb2f-458e-9037-cdc4eda4d3c2" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: TYPE="swap" UUID="62132145-d060-460c-afeb-3d7dd27bfadc" 
/dev/sdc1: UUID="F44029C940299380" TYPE="ntfs" 
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
# kopt=root=UUID=dd022a17-eb2f-458e-9037-cdc4eda4d3c2 ro

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
# defoptions=quiet splash xforcevesa

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
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=dd022a17-eb2f-458e-9037-cdc4eda4d3c2 ro quiet splash xforcevesa
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=dd022a17-eb2f-458e-9037-cdc4eda4d3c2 ro single
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
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=dd022a17-eb2f-458e-9037-cdc4eda4d3c2 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=62132145-d060-460c-afeb-3d7dd27bfadc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


 330.6GB: boot/grub/menu.lst
 330.6GB: boot/grub/stage2
 330.6GB: boot/initrd.img-2.6.24-16-generic
 330.6GB: boot/initrd.img-2.6.24-16-generic.bak
 330.6GB: boot/vmlinuz-2.6.24-16-generic
 330.6GB: initrd.img
 330.6GB: vmlinuz
```

if I try to locate my drives using 
```
gksudo gedit /boot/grub/menu.lst
```

I get the following 
```
     
```

Thats not a typo, nothing shows up

Can I get help please

---

### Post by lindsay7 on 2009-06-08
17 : Cannot mount selected partition
    This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB. 



This does not make sense to me, from your grub menu,

```
/dev/sdb1: UUID="dd022a17-eb2f-458e-9037-cdc4eda4d3c2" SEC_TYPE="ext2" TYPE="ext3" 

```


Can you post a screen shot of the drive with Ubuntu on it using Gparted, I can not imagine how it would be formated both ext3 and ext2 at the same time.

---

### Post by presence1960 on 2009-06-08
sometimes GRUB reads the order of your drives differently than BIOS. In BIOS my boot order is (160 GB) then (250 GB) but my sudo fdisk -l still shows the other way around

```
raz@raz-desktop:~$ sudo fdisk -l
[sudo] password for raz: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000d179

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4569    36700461    7  HPFS/NTFS
/dev/sda3            4570       29879   203302575   83  Linux
/dev/sda4           29880       30401     4192965   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa7a57e45

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14519   116623836   83  Linux
/dev/sdb2   *       16478       18389    15358140   83  Linux
/dev/sdb3           18390       19457     8578710    7  HPFS/NTFS
/dev/sdb4           14520       16477    15727635   83  Linux
```

But here is my menu.lst from jaunty for windows
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
rootnoverify	(hd1,0)
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader	+1

title           Hardy 8.04
rootnoverify    (hd0,1)
chainloader     +1
```

According to sudo fdisk -l my windows should be at (hd0,0) but it isn't because the boot order is different in BIOS. I didnt include jaunty's entries because jaunty uses UUID instead of (hdx,y). Go into your BIOS and note the order of booting for your hard disks and change the (hdx,y) accordingly in menu.lst. **First make a back up of your menu.lst just in case!**

---

### Post by kunks112 on 2009-06-08
Im not quite understanding what it is you wanted, so I would like clarify.

You would like to me type 
```
/dev/sdb1: UUID="dd022a17-eb2f-458e-9037-cdc4eda4d3c2" SEC_TYPE="ext2" TYPE="ext3"
```
from where? Do you want me to load a terminal and get into grub?

Second, I do not know how to take screen shots.

Please excuse me as for all that I posted before was data obtained from a post the first time I installed Ubuntu, otherwise I am a total newb at Linux

Thanks for the reply

---

### Post by presence1960 on 2009-06-08
> **lindsay7 said:**
> 17 : Cannot mount selected partition
    This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB. 



This does not make sense to me, from your grub menu,

```
/dev/sdb1: UUID="dd022a17-eb2f-458e-9037-cdc4eda4d3c2" SEC_TYPE="ext2" TYPE="ext3" 

```


Can you post a screen shot of the drive with Ubuntu on it using Gparted, I can not imagine how it would be formated both ext3 and ext2 at the same time.

I just checked mine and it is that way also: 
```
blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="762E5E3652B3BE78" LABEL="Windows" TYPE="ntfs" 
/dev/sda3: LABEL="Ubuntu home" UUID="c2ead461-b31c-40a6-aabd-ca0ad5a390fb" TYPE="ext4" 
/dev/sda4: UUID="6bd3d8d7-bcb4-428f-ae97-489230524dd8" TYPE="swap" 
/dev/sdb1: LABEL="backup & stuff" UUID="b4e4df17-df05-4a7e-a86c-9dc6483b398e" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb2: LABEL="Hardy 8.04" UUID="9ca2b239-ff96-4ecd-9815-119c7f93d590" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb3: UUID="2C8D67F3040784F1" LABEL="windows storage" TYPE="ntfs" 
/dev/sdb4: UUID="c94e2af2-c9a2-49b5-ba8f-357853bf3e23" TYPE="ext4" 

```
So I don't think that is the problem.

---

### Post by presence1960 on 2009-06-08
kunks, reboot and go into BIOS and see the order of boot for your hard disks. you have 300 GB, 500 GB and 1500 GB. let us know which boots 1st, 2nd & 3rd. Then I will give you the (hdx,y) to change in your menu.lst.

---

### Post by kunks112 on 2009-06-08
If I do 
```
sudo grub
```
then the command you listed I get 
Error 27:Unrecognized command.


Worse news, if unplug my Ubuntu drive keeping my Vista drive and Win 7 drive, I cannot load either of them without Grub.

I really need to fix this

---

### Post by lindsay7 on 2009-06-08
Do you have any idea why it would be stated like that. I checked my three computers and they all show just one type of format, either ext3 or ext4.

Also, is there anyway to know if ones bios is going to read the way it does in you example, i.e hd0 in grub is hd1 in bios.

---

### Post by kunks112 on 2009-06-08
> **presence1960 said:**
> kunks, reboot and go into BIOS and see the order of boot for your hard disks. you have 300 GB, 500 GB and 1500 GB. let us know which boots 1st, 2nd & 3rd. Then I will give you the (hdx,y) to change in your menu.lst.



Oh ok, this is easy, I have it set in the following order
500GB
300GB
1.5TB

---

### Post by kunks112 on 2009-06-08
> **lindsay7 said:**
> Do you have any idea why it would be stated like that. I checked my three computers and they all show just one type of format, either ext3 or ext4.

Also, is there anyway to know if ones bios is going to read the way it does in you example, i.e hd0 in grub is hd1 in bios.

My BIOS worked with this configuration before I had to do the re-install. What it did was opened GRUB, if I wanted Ubuntu I loaded that. If I wanted a Win OS I loaded Win and then Windows bootloader would ask which Win I wanted.

---

### Post by presence1960 on 2009-06-08
> **lindsay7 said:**
> Do you have any idea why it would be stated like that. I checked my three computers and they all show just one type of format, either ext3 or ext4.

Also, is there anyway to know if ones bios is going to read the way it does in you example, i.e hd0 in grub is hd1 in bios.

There is no way to know about BIOS reading one way. I found out just like kunks did when I booted. Got a GRUB error. Booted from Live CD and did sudo fdisk -l and that is when I noticed my disks were in reverse order in sudo fdisk -l. My 160 GB disk actually boots first but Ubuntu shows it as sdb. I also helped someone for the longest time on a thread until we discovered the same thing. changed it and his triple boot worked.

---

### Post by presence1960 on 2009-06-08
> **kunks112 said:**
> My BIOS worked with this configuration before I had to do the re-install. What it did was opened GRUB, if I wanted Ubuntu I loaded that. If I wanted a Win OS I loaded Win and then Windows bootloader would ask which Win I wanted.
 That was then, just go into BIOS and see the boot order of your disks. If they are the same then we'll have to look at another avenue. it will only take 1 minute. Do you want your system to boot or not?

---

### Post by kunks112 on 2009-06-08
> **presence1960 said:**
> sometimes GRUB reads the order of your drives differently than BIOS. In BIOS my boot order is (160 GB) then (250 GB) but my sudo fdisk -l still shows the other way around

```
raz@raz-desktop:~$ sudo fdisk -l
[sudo] password for raz: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000d179

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4569    36700461    7  HPFS/NTFS
/dev/sda3            4570       29879   203302575   83  Linux
/dev/sda4           29880       30401     4192965   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa7a57e45

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14519   116623836   83  Linux
/dev/sdb2   *       16478       18389    15358140   83  Linux
/dev/sdb3           18390       19457     8578710    7  HPFS/NTFS
/dev/sdb4           14520       16477    15727635   83  Linux
```

But here is my menu.lst from jaunty for windows
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
rootnoverify	(hd1,0)
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader	+1

title           Hardy 8.04
rootnoverify    (hd0,1)
chainloader     +1
```

According to sudo fdisk -l my windows should be at (hd0,0) but it isn't because the boot order is different in BIOS. I didnt include jaunty's entries because jaunty uses UUID instead of (hdx,y). Go into your BIOS and note the order of booting for your hard disks and change the (hdx,y) accordingly in menu.lst. **First make a back up of your menu.lst just in case!**


My menu list reads nothing.
Going to set-up like you listed.

---

### Post by presence1960 on 2009-06-08
you must be looking in the wrong place for menu.lst. 

here is yours from sdb1 which is taken from your post.
```

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
# kopt=root=UUID=dd022a17-eb2f-458e-9037-cdc4eda4d3c2 ro

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
# defoptions=quiet splash xforcevesa

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
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=dd022a17-eb2f-458e-9037-cdc4eda4d3c2 ro quiet splash xforcevesa
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=dd022a17-eb2f-458e-9037-cdc4eda4d3c2 ro single
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
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

---

### Post by lindsay7 on 2009-06-08
>  Re: Ububtu 8.04 Grub Error 17
Quote:
Originally Posted by presence1960 View Post
kunks, reboot and go into BIOS and see the order of boot for your hard disks. you have 300 GB, 500 GB and 1500 GB. let us know which boots 1st, 2nd & 3rd. Then I will give you the (hdx,y) to change in your menu.lst.


Oh ok, this is easy, I have it set in the following order
500GB
300GB
1.5TB
kunks112 is online now Report Post   	Reply With Quote


Hold on do not do anything, he is going to give the boot instructions and how to fix you grub menu.

---

### Post by presence1960 on 2009-06-08
> **lindsay7 said:**
> Hold on do not do anything, he is going to give the boot instructions and how to fix you grub menu.

Ok Kunks just to be 100% sure now run this command in terminal from the Live CD > sudo fdisk -l BTW that is a lowercase L. then we can compare your BIOS and Ubuntu disk order

P.S. Post the output here please.

---

### Post by kunks112 on 2009-06-08
> **presence1960 said:**
> That was then, just go into BIOS and see the boot order of your disks. If they are the same then we'll have to look at another avenue. it will only take 1 minute. Do you want your system to boot or not?

Whoooaaa, please dont take my shortness for belligerence. I greatly appreciate the help, especially the timely help. I had to make sure my thesis wasnt lost.

What you had suggested with changing my bios seems to have worked.

I have loaded into Ubuntu, and Win 7 already. Pretty sure Vista will load.

Your solution was correct, and I greatly appreciate the help.

Time to re-install all the drivers and Kile.

Thank you

---

### Post by presence1960 on 2009-06-08
> **kunks112 said:**
> Whoooaaa, please dont take my shortness for belligerence. I greatly appreciate the help, especially the timely help. I had to make sure my thesis wasnt lost.

What you had suggested with changing my bios seems to have worked.

I have loaded into Ubuntu, and Win 7 already. Pretty sure Vista will load.

Your solution was correct, and I greatly appreciate the help.

Time to re-install all the drivers and Kile.

Thank you

No problem, I know you want your system up. Enjoy!

---

### Post by presence1960 on 2009-06-08
> **lindsay7 said:**
> Hold on do not do anything, he is going to give the boot instructions and how to fix you grub menu.

lindsay,

if you look at his info from the beginning post #2 (sudo fdisk -l) and compare it to this :```
 Originally Posted by presence1960 View Post
kunks, reboot and go into BIOS and see the order of boot for your hard disks. you have 300 GB, 500 GB and 1500 GB. let us know which boots 1st, 2nd & 3rd. Then I will give you the (hdx,y) to change in your menu.lst.


Oh ok, this is easy, I have it set in the following order
500GB
300GB
1.5TB
kunks112 is online now Report Post Reply With Quote 
```

you will see his first 2 disks were in a different order in BIOS and Ubuntu. You can change the order in BIOS or change the (hdx,y) designations in GRUB to fix it. Either way will work. As long as we helped to get it working is all that matters.

---

### Post by lindsay7 on 2009-06-08
Thanks for the lesson. You do nice work!

---

