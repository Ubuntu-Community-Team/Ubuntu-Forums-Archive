---
title: "Error 12 when booting Windows 7"
date: 2009-10-09
forum: Installation &amp; Upgrades
---

### Post by Buddhist_Brother on 2009-10-09
I recently installed Windows 7 to dual boot with ubuntu. When I installed Ubuntu I had to reinstall grub and now when I try to boot Windows I get Error 12 

[php]============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x20000000

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    57,673,349    57,673,287  83 Linux
/dev/sda2    *     57,673,350   149,533,019    91,859,670   7 HPFS/NTFS
/dev/sda3         149,838,255   156,296,384     6,458,130   5 Extended
/dev/sda5         149,838,318   156,296,384     6,458,067  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="1cb32471-cd42-4086-90cc-13ea46b87e25" TYPE="ext3" 
/dev/sda2: UUID="3ABC08963BC419AE" TYPE="ntfs" 
/dev/sda5: UUID="3476ae8f-3881-469c-bfd8-1bc5bbd53976" TYPE="swap" 

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
lrm on /lib/modules/2.6.28-15-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/michael/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=michael)


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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
#password --md5 $1$REdr0/$kOyJtydnVhIEQHEF7D2a41
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
# kopt=root=UUID=1cb32471-cd42-4086-90cc-13ea46b87e25 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=1cb32471-cd42-4086-90cc-13ea46b87e25

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
# defoptions=quiet splash vga=789

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

title        Windows 7 Ultimate
root        (hd0,2)
makeactive
chainloader    +1

title        Ubuntu 9.04, kernel 2.6.28-15-generic
uuid        1cb32471-cd42-4086-90cc-13ea46b87e25
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=1cb32471-cd42-4086-90cc-13ea46b87e25 ro quiet splash vga=789 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid        1cb32471-cd42-4086-90cc-13ea46b87e25
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=1cb32471-cd42-4086-90cc-13ea46b87e25 ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.28-14-generic
uuid        1cb32471-cd42-4086-90cc-13ea46b87e25
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=1cb32471-cd42-4086-90cc-13ea46b87e25 ro quiet splash vga=789 
initrd        /boot/initrd.img-2.6.28-14-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid        1cb32471-cd42-4086-90cc-13ea46b87e25
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=1cb32471-cd42-4086-90cc-13ea46b87e25 ro  single
initrd        /boot/initrd.img-2.6.28-14-generic

title        Ubuntu 9.04, kernel 2.6.28-13-generic
uuid        1cb32471-cd42-4086-90cc-13ea46b87e25
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=1cb32471-cd42-4086-90cc-13ea46b87e25 ro quiet splash vga=789 
initrd        /boot/initrd.img-2.6.28-13-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid        1cb32471-cd42-4086-90cc-13ea46b87e25
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=1cb32471-cd42-4086-90cc-13ea46b87e25 ro  single
initrd        /boot/initrd.img-2.6.28-13-generic

title        Ubuntu 9.04, kernel 2.6.28-12-generic
uuid        1cb32471-cd42-4086-90cc-13ea46b87e25
kernel        /boot/vmlinuz-2.6.28-12-generic root=UUID=1cb32471-cd42-4086-90cc-13ea46b87e25 ro quiet splash vga=789 
initrd        /boot/initrd.img-2.6.28-12-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-12-generic (recovery mode)
uuid        1cb32471-cd42-4086-90cc-13ea46b87e25
kernel        /boot/vmlinuz-2.6.28-12-generic root=UUID=1cb32471-cd42-4086-90cc-13ea46b87e25 ro  single
initrd        /boot/initrd.img-2.6.28-12-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        1cb32471-cd42-4086-90cc-13ea46b87e25
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=1cb32471-cd42-4086-90cc-13ea46b87e25 ro quiet splash vga=789 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        1cb32471-cd42-4086-90cc-13ea46b87e25
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=1cb32471-cd42-4086-90cc-13ea46b87e25 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        1cb32471-cd42-4086-90cc-13ea46b87e25
kernel        /boot/memtest86+.bin
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
UUID=1cb32471-cd42-4086-90cc-13ea46b87e25 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=3476ae8f-3881-469c-bfd8-1bc5bbd53976 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

tmpfs /dev/shm tmpfs defaults 0 0 

=================== sda1: Location of files loaded by Grub: ===================


   8.7GB: boot/grub/menu.lst
  10.9GB: boot/grub/stage2
   8.7GB: boot/initrd.img-2.6.28-11-generic
   8.6GB: boot/initrd.img-2.6.28-12-generic
   8.6GB: boot/initrd.img-2.6.28-13-generic
   8.6GB: boot/initrd.img-2.6.28-14-generic
   8.7GB: boot/initrd.img-2.6.28-15-generic
   8.7GB: boot/vmlinuz-2.6.28-11-generic
   8.7GB: boot/vmlinuz-2.6.28-12-generic
   8.6GB: boot/vmlinuz-2.6.28-13-generic
   8.6GB: boot/vmlinuz-2.6.28-14-generic
   8.7GB: boot/vmlinuz-2.6.28-15-generic
   8.7GB: initrd.img
   8.6GB: initrd.img.old
   8.7GB: vmlinuz
   8.6GB: vmlinuz.old[/php]Could someone help me out ?

---

### Post by lindsay7 on 2009-10-09
It looks like there are two thing that are not correct.

1. the windows boot lines need to be below the line
### END DEBIAN AUTOMAGIC KERNELS LIST


2. Windows is on (hd0,1) so the lines should read


title        Windows 7 Ultimate
root        (hd0,1)
makeactive
chainloader    +1


Cut and past the changes to  below the ### End Debian line in your grub menu.

type this in the terminal

sudo /boot/grub/menu.lst  (that is the lower case letter L), make the changes and save the file.

---

### Post by presence1960 on 2009-10-09
> **lindsay7 said:**
> It looks like there are two thing that are not correct.

1. the windows boot lines need to be below the line
### END DEBIAN AUTOMAGIC KERNELS LIST


2. Windows is on (hd0,1) so the lines should read


title        Windows 7 Ultimate
root        (hd0,1)
makeactive
chainloader    +1


Cut and past the changes to  below the ### End Debian line in your grub menu.

type this in the terminal

sudo /boot/grub/menu.lst  (that is the lower case letter L), make the changes and save the file.

+1

can't go wrong there!

---

### Post by Mark Phelps on 2009-10-10
> **lindsay7 said:**
> 
type this in the terminal

sudo /boot/grub/menu.lst  (that is the lower case letter L), make the changes and save the file.

What you want is "gksudo gedit /boot/grub/menu.lst" -- to invoke the gedit text editor for making changes to the menu.lst file.

---

### Post by presence1960 on 2009-10-10
> **Mark Phelps said:**
> What you want is "gksudo gedit /boot/grub/menu.lst" -- to invoke the gedit text editor for making changes to the menu.lst file.

good catch Mark, I didn't notice the sudo prefacing the command. I use gksu whenever running a graphical app as root such as gedit, gparted or nautilus.

---

### Post by lindsay7 on 2009-10-10
Sorry about the typo! I normally just use sudo gedit, what does the use of gksudo or gksu do that is better or recomended?

---

### Post by presence1960 on 2009-10-10
> **lindsay7 said:**
> Sorry about the typo! I normally just use sudo gedit, what does the use of gksudo or gksu do that is better or recomended?

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by lindsay7 on 2009-10-11
To:  presence1960

Thanks!

---

### Post by dustoashes on 2010-01-18
Hi,

I have the very same problem which I can't fix on my own. Here is my output:

**fdisk -l**
```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x06cd1510

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3187    25599546   83  Linux
/dev/sda3   *        3188       29762   213463687+   7  HPFS/NTFS
/dev/sda4           29763       30401     5132767+   f  W95 Ext'd (LBA)
/dev/sda5           29763       30401     5132736   82  Linux swap / Solaris

```

**menu.lst**

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
# kopt=root=UUID=c426a7a4-8085-4083-a540-049e4f78a229 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=c426a7a4-8085-4083-a540-049e4f78a229

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

title		Ubuntu 9.04, kernel 2.6.28-17-generic
uuid		c426a7a4-8085-4083-a540-049e4f78a229
kernel		/boot/vmlinuz-2.6.28-17-generic root=UUID=c426a7a4-8085-4083-a540-049e4f78a229 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-17-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-17-generic (recovery mode)
uuid		c426a7a4-8085-4083-a540-049e4f78a229
kernel		/boot/vmlinuz-2.6.28-17-generic root=UUID=c426a7a4-8085-4083-a540-049e4f78a229 ro  single
initrd		/boot/initrd.img-2.6.28-17-generic

title		Ubuntu 9.04, kernel 2.6.28-16-generic
uuid		c426a7a4-8085-4083-a540-049e4f78a229
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=c426a7a4-8085-4083-a540-049e4f78a229 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-16-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
uuid		c426a7a4-8085-4083-a540-049e4f78a229
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=c426a7a4-8085-4083-a540-049e4f78a229 ro  single
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		c426a7a4-8085-4083-a540-049e4f78a229
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=c426a7a4-8085-4083-a540-049e4f78a229 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		c426a7a4-8085-4083-a540-049e4f78a229
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=c426a7a4-8085-4083-a540-049e4f78a229 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		c426a7a4-8085-4083-a540-049e4f78a229
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows 7
rootnoverify	(hd0,1)
savedefault
makeactive
chainloader	+1

```

And results.txt from boot info script:

```
============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x06cd1510

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    51,199,154    51,199,092  83 Linux
/dev/sda3    *     51,199,155   478,126,529   426,927,375   7 HPFS/NTFS
/dev/sda4         478,126,530   488,392,064    10,265,535   f W95 Ext d (LBA)
/dev/sda5         478,126,593   488,392,064    10,265,472  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="c426a7a4-8085-4083-a540-049e4f78a229" TYPE="ext3" 
/dev/sda3: UUID="7085201B54987A10" TYPE="ntfs" 
/dev/sda5: TYPE="swap" UUID="e68cd560-713a-45ba-905b-a8e9194607d4" 
/dev/sda5: UUID="e68cd560-713a-45ba-905b-a8e9194607d4" TYPE="swap" 

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
lrm on /lib/modules/2.6.28-17-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/hamza/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=hamza)


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
# kopt=root=UUID=c426a7a4-8085-4083-a540-049e4f78a229 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=c426a7a4-8085-4083-a540-049e4f78a229

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

title		Ubuntu 9.04, kernel 2.6.28-17-generic
uuid		c426a7a4-8085-4083-a540-049e4f78a229
kernel		/boot/vmlinuz-2.6.28-17-generic root=UUID=c426a7a4-8085-4083-a540-049e4f78a229 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-17-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-17-generic (recovery mode)
uuid		c426a7a4-8085-4083-a540-049e4f78a229
kernel		/boot/vmlinuz-2.6.28-17-generic root=UUID=c426a7a4-8085-4083-a540-049e4f78a229 ro  single
initrd		/boot/initrd.img-2.6.28-17-generic

title		Ubuntu 9.04, kernel 2.6.28-16-generic
uuid		c426a7a4-8085-4083-a540-049e4f78a229
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=c426a7a4-8085-4083-a540-049e4f78a229 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-16-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
uuid		c426a7a4-8085-4083-a540-049e4f78a229
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=c426a7a4-8085-4083-a540-049e4f78a229 ro  single
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		c426a7a4-8085-4083-a540-049e4f78a229
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=c426a7a4-8085-4083-a540-049e4f78a229 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		c426a7a4-8085-4083-a540-049e4f78a229
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=c426a7a4-8085-4083-a540-049e4f78a229 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		c426a7a4-8085-4083-a540-049e4f78a229
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista (loader)
rootnoverify	(hd0,1)
savedefault
makeactive
chainloader	+1


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
UUID=c426a7a4-8085-4083-a540-049e4f78a229 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=eb414a89-40a9-4f73-9cde-c1c9f2a8c4fc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .7GB: boot/grub/menu.lst
    .7GB: boot/grub/stage2
    .8GB: boot/initrd.img-2.6.28-11-generic
    .7GB: boot/initrd.img-2.6.28-16-generic
    .8GB: boot/initrd.img-2.6.28-17-generic
    .7GB: boot/vmlinuz-2.6.28-11-generic
    .7GB: boot/vmlinuz-2.6.28-16-generic
    .7GB: boot/vmlinuz-2.6.28-17-generic
    .8GB: initrd.img
    .7GB: initrd.img.old
    .7GB: vmlinuz
    .7GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb 
```

---

### Post by presence1960 on 2010-01-18
> **dustoashes said:**
> Hi,

I have the very same problem which I can't fix on my own. Here is my output:

**fdisk -l**
```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x06cd1510

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3187    25599546   83  Linux
/dev/sda3   *        3188       29762   213463687+   7  HPFS/NTFS
/dev/sda4           29763       30401     5132767+   f  W95 Ext'd (LBA)
/dev/sda5           29763       30401     5132736   82  Linux swap / Solaris

```

**menu.lst**

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
# kopt=root=UUID=c426a7a4-8085-4083-a540-049e4f78a229 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=c426a7a4-8085-4083-a540-049e4f78a229

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

title		Ubuntu 9.04, kernel 2.6.28-17-generic
uuid		c426a7a4-8085-4083-a540-049e4f78a229
kernel		/boot/vmlinuz-2.6.28-17-generic root=UUID=c426a7a4-8085-4083-a540-049e4f78a229 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-17-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-17-generic (recovery mode)
uuid		c426a7a4-8085-4083-a540-049e4f78a229
kernel		/boot/vmlinuz-2.6.28-17-generic root=UUID=c426a7a4-8085-4083-a540-049e4f78a229 ro  single
initrd		/boot/initrd.img-2.6.28-17-generic

title		Ubuntu 9.04, kernel 2.6.28-16-generic
uuid		c426a7a4-8085-4083-a540-049e4f78a229
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=c426a7a4-8085-4083-a540-049e4f78a229 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-16-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
uuid		c426a7a4-8085-4083-a540-049e4f78a229
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=c426a7a4-8085-4083-a540-049e4f78a229 ro  single
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		c426a7a4-8085-4083-a540-049e4f78a229
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=c426a7a4-8085-4083-a540-049e4f78a229 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		c426a7a4-8085-4083-a540-049e4f78a229
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=c426a7a4-8085-4083-a540-049e4f78a229 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		c426a7a4-8085-4083-a540-049e4f78a229
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows 7
rootnoverify	(hd0,1)
savedefault
makeactive
chainloader	+1

```

And results.txt from boot info script:

```
============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x06cd1510

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    51,199,154    51,199,092  83 Linux
/dev/sda3    *     51,199,155   478,126,529   426,927,375   7 HPFS/NTFS
/dev/sda4         478,126,530   488,392,064    10,265,535   f W95 Ext d (LBA)
/dev/sda5         478,126,593   488,392,064    10,265,472  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="c426a7a4-8085-4083-a540-049e4f78a229" TYPE="ext3" 
/dev/sda3: UUID="7085201B54987A10" TYPE="ntfs" 
/dev/sda5: TYPE="swap" UUID="e68cd560-713a-45ba-905b-a8e9194607d4" 
/dev/sda5: UUID="e68cd560-713a-45ba-905b-a8e9194607d4" TYPE="swap" 

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
lrm on /lib/modules/2.6.28-17-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/hamza/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=hamza)


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
# kopt=root=UUID=c426a7a4-8085-4083-a540-049e4f78a229 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=c426a7a4-8085-4083-a540-049e4f78a229

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

title		Ubuntu 9.04, kernel 2.6.28-17-generic
uuid		c426a7a4-8085-4083-a540-049e4f78a229
kernel		/boot/vmlinuz-2.6.28-17-generic root=UUID=c426a7a4-8085-4083-a540-049e4f78a229 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-17-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-17-generic (recovery mode)
uuid		c426a7a4-8085-4083-a540-049e4f78a229
kernel		/boot/vmlinuz-2.6.28-17-generic root=UUID=c426a7a4-8085-4083-a540-049e4f78a229 ro  single
initrd		/boot/initrd.img-2.6.28-17-generic

title		Ubuntu 9.04, kernel 2.6.28-16-generic
uuid		c426a7a4-8085-4083-a540-049e4f78a229
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=c426a7a4-8085-4083-a540-049e4f78a229 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-16-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
uuid		c426a7a4-8085-4083-a540-049e4f78a229
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=c426a7a4-8085-4083-a540-049e4f78a229 ro  single
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		c426a7a4-8085-4083-a540-049e4f78a229
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=c426a7a4-8085-4083-a540-049e4f78a229 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		c426a7a4-8085-4083-a540-049e4f78a229
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=c426a7a4-8085-4083-a540-049e4f78a229 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		c426a7a4-8085-4083-a540-049e4f78a229
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista (loader)
rootnoverify	(hd0,1)
savedefault
makeactive
chainloader	+1


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
UUID=c426a7a4-8085-4083-a540-049e4f78a229 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=eb414a89-40a9-4f73-9cde-c1c9f2a8c4fc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .7GB: boot/grub/menu.lst
    .7GB: boot/grub/stage2
    .8GB: boot/initrd.img-2.6.28-11-generic
    .7GB: boot/initrd.img-2.6.28-16-generic
    .8GB: boot/initrd.img-2.6.28-17-generic
    .7GB: boot/vmlinuz-2.6.28-11-generic
    .7GB: boot/vmlinuz-2.6.28-16-generic
    .7GB: boot/vmlinuz-2.6.28-17-generic
    .8GB: initrd.img
    .7GB: initrd.img.old
    .7GB: vmlinuz
    .7GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb 
```

No need to post the output of menu.lst & fdisk as they are included in the boot info script output.

Boot into Ubuntu and open a terminal and run ```
gksu gedit /boot/grub/menu.lst
```
That is a lowercase L in .lst

Scroll down to this:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista (loader)
rootnoverify	(hd0,1)
savedefault
makeactive
chainloader	+1
```

change it to this:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda[COLOR="Red"]3[/COLOR]
title		Windows Vista (loader)
rootnoverify	(hd0,[COLOR="Red"]2[/COLOR])
chainloader	+1
```

Click Save on top toolbar & close file. reboot and try booting windows.

---

