---
title: "Will This Work?"
date: 2009-01-26
forum: Installation &amp; Upgrades
---

### Post by 5BallJuggler on 2009-01-26
I'm trying to get my laptop to run with a few distros on it, and I'm wondering what is the best way.

I've previously tried to install linpus, but that seems to take away the ability to boot XP, so this is what I'm trying now.

Install DSL, linpus, Crunchbang onto different partitions on the hard drive, then insert the Windows XP disk, boot up and carry out the fixmbr command.
Then install Ubuntu 8.10, and modify the grub loader from there

Will this method work?

---

### Post by tripolitan on 2009-01-26
Whatever you do, you should always install Windows first and on the first partition. I've had no luck with installing Linpus but I think you should install distros that enable you to configure partitions and GRUB, so you don't lose, or hose, the other partitions or distros.

When I briefly ran two distros on one PC, I formatted one 512MB swap partition that they shared. I soon realized that there was no point in installing several distros on one PC when I could just use the LiveCD versions, for evaluation purposes. I also learned to only install stable, long-term supported versions of distros, such as Etch for Debian and 8.04 for Ubuntu. 

I don't know about your Laptop's processing power and resources but Crunchbang Lite looks promising:
[http://crunchbang.net/pub/linux/crunchbang-lite-8.04.02.i386.iso](http://crunchbang.net/pub/linux/crunchbang-lite-8.04.02.i386.iso)

---

### Post by 5BallJuggler on 2009-01-26
I'm at the point the point now that I need a little help, i've included the boot_info_script results for everyone to look at, and a screenshot of the partions 

If possible i'd like to be able to make 1 grub loader that will list every distro on the drive

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #11 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Boot file info:     
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Boot file info:     
    Operating System:  
    Boot files/dirs:   /boot/grub/grub.conf

sda7: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Boot file info:     
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Boot file info:     
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Boot file info:     
    Operating System:  
    Boot files/dirs:   

sda10: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Boot file info:     
    Operating System:  
    Boot files/dirs:   /boot/grub/menu.lst

sda11: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Boot file info:     
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda12: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda13: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Boot file info:     
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /etc/fstab

sda14: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9ca39ca3

Partition  Boot        Start          End         Size  Id System

/dev/sda1    *            63   30,780,539   30,780,477   7 HPFS/NTFS
/dev/sda2         30,780,540  117,210,239   86,429,700   5 Extended
/dev/sda5         30,780,603   31,150,034      369,432  83 Linux
/dev/sda6         51,343,803   71,906,939   20,563,137  83 Linux
/dev/sda7         71,907,003   72,276,434      369,432  83 Linux
/dev/sda8         92,470,203  100,711,484    8,241,282  83 Linux
/dev/sda9        100,711,548  108,952,829    8,241,282  83 Linux
/dev/sda10       108,952,893  117,210,239    8,257,347  83 Linux
/dev/sda11        72,276,498   91,506,239   19,229,742  83 Linux
/dev/sda12        91,506,303   92,470,139      963,837  82 Linux swap / Solaris
/dev/sda13        31,150,098   50,379,839   19,229,742  83 Linux
/dev/sda14        50,379,903   51,343,739      963,837  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/ramzswap0: TYPE="swap" 
/dev/sda1: UUID="FE1414DF14149CA9" TYPE="ntfs" 
/dev/sda5: UUID="6828cf56-a5ac-4827-a01d-66be3818bbeb" TYPE="ext2" 
/dev/sda6: UUID="301a7ec7-23a1-47fe-826c-2893512e7fb9" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: UUID="49c4cd51-dd3e-41f1-b852-5cb338b6e26e" TYPE="ext2" 
/dev/sda8: UUID="d06f9827-17c8-4f99-ab51-096b2a10e9de" TYPE="ext2" 
/dev/sda9: UUID="260b774f-a482-4369-865a-4b5db4021233" TYPE="ext2" 
/dev/sda10: UUID="a8efffdf-1ca1-4c74-8e30-8f561a25dbb0" TYPE="ext2" 
/dev/sda11: UUID="ac8706be-c710-405d-8ecc-0745a2abc115" TYPE="ext3" 
/dev/sda12: UUID="788d678a-e65a-462d-be87-388824ad3892" TYPE="swap" 
/dev/sda13: UUID="a587037f-79f0-4f23-a5cb-9eb8f8ef075d" TYPE="ext3" 
/dev/sda14: UUID="4c3ae1bd-b2ec-4865-8022-58c68dbdb4b0" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda11 on / type ext3 (rw,relatime,errors=remount-ro)
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
/dev/sda13 on /tmp/BootInfo/sda13 type ext3 (rw)

================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect


========================== sda6/boot/grub/grub.conf: ==========================


default=0
timeout=10
splashimage=(hd0,5)/boot/grub/splash.xpm.gz
#hiddenmenu

title Linpus Linux Lite
        rootnoverify (hd0,5)
        kernel /boot/bzImage changes=/dev/hda6 root=/dev/ram0 rw max_loop=255 init=linuxrc selinux=0 vga=0x311 splash=silent quiet loglevel=1 console=tty1 acpi=force load_ramdisk=1 prompt_ramdisk=0 ramdisk_size=14000 from=/dev/hda6 probeusb lang=en
        initrd /boot/initrd.gz

title Linpus Linux Lite(rescue)
        rootnoverify (hd0,5)
        kernel /boot/bzImage changes=/dev/hda6 root=/dev/ram0 rw max_loop=255 init=linuxrc selinux=0 vga=0x311 splash=silent quiet loglevel=1 console=tty1 acpi=force load_ramdisk=1 prompt_ramdisk=0 ramdisk_size=14000 from=/dev/hda6 probeusb rescue lang=en
        initrd /boot/initrd.gz

title Windows Xp
	rootnoverify (hd0,1)
	chainloader +1


=================== sda6: Location  of files loaded by Grub: ===================


  35.6GB: boot/grub/grub.conf
  35.5GB: boot/grub/stage2
  35.5GB: boot/initrd.gz

========================== sda10/boot/grub/menu.lst: ==========================

# This sets the default entry to boot. 
# Remember that GRUB counts from 0, so 1 is the second entry.

default 0
	
# This sets the length of time in seconds that grub will wait for the user to select an OS
# before it boots the default on. I reccommend at least 15 seconds.

timeout 15

# Enter the entry for DSL here. Something like this.

title DSL
kernel /boot/linux24 root=/dev/hda10 quiet vga=normal noacpi noapm nodma noscsi frugal 
initrd /boot/minirt24.gz  

title DSL fb800x600
kernel /boot/linux24 root=/dev/hda10 quiet vga=788 noacpi noapm nodma noscsi frugal 
initrd /boot/minirt24.gz  

title DSL fb1024x768
kernel /boot/linux24 root=/dev/hda10 quiet vga=791 noacpi noapm nodma noscsi frugal 
initrd /boot/minirt24.gz  

title DSL fb1280x1024
kernel /boot/linux24 root=/dev/hda10 quiet vga=794 noacpi noapm nodma noscsi frugal 
initrd /boot/minirt24.gz  

#title DSL with toram, mydsl, restore, hostname, and passwords
#kernel /boot/linux24 root=/dev/hda10 quiet vga=normal noacpi noapm noscsi frugal dma toram mydsl=hda5 restore=hda5 host=DSL1 secure
#initrd /boot/minirt24.gz

#title DSL with XFree86
#kernel /boot/linux24 root=/dev/hda10 quiet vga=normal noacpi noapm noscsi frugal dma toram mydsl=hda5/xfree restore=hda6 host=DSL1 secure
#initrd /boot/minirt24.gz

#title DSL with mydsl, restore, persistentancy, hostname, and passwords
#kernel /boot/linux24 root=/dev/hda10 quiet vga=normal noacpi noapm noscsi frugal dma toram mydsl=hda3 restore=hda3 home=hda3 opt=hda3 host=DSL1 secure
#initrd /boot/minirt24.gz

#title DSL Runlevel 2
#kernel /boot/linux24 root=/dev/hda10 quiet vga=normal noacpi noapm noscsi nodma frugal 2 base norestore
#initrd /boot/minirt24.gz

title DSL Check filesystem(s)
kernel /boot/linux24 root=/dev/hda10 quiet vga=normal noacpi noapm noscsi nodma frugal 2 base norestore legacy checkfs
initrd /boot/minirt24.gz

title Windows
root (hd0,0)
chainloader +1
makeactive
boot

================== sda10: Location  of files loaded by Grub: ==================


  56.5GB: boot/grub/menu.lst
  56.5GB: boot/grub/stage2

========================== sda11/boot/grub/menu.lst: ==========================

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
# kopt=root=UUID=ac8706be-c710-405d-8ecc-0745a2abc115 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=ac8706be-c710-405d-8ecc-0745a2abc115

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
uuid		ac8706be-c710-405d-8ecc-0745a2abc115
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=ac8706be-c710-405d-8ecc-0745a2abc115 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		ac8706be-c710-405d-8ecc-0745a2abc115
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=ac8706be-c710-405d-8ecc-0745a2abc115 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, memtest86+
uuid		ac8706be-c710-405d-8ecc-0745a2abc115
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sda11/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda11
UUID=ac8706be-c710-405d-8ecc-0745a2abc115 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda12
UUID=788d678a-e65a-462d-be87-388824ad3892 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================== sda11: Location  of files loaded by Grub: ==================


  45.1GB: boot/grub/menu.lst
  45.1GB: boot/grub/stage2
  44.6GB: boot/initrd.img-2.6.27-9-generic
  44.7GB: boot/vmlinuz-2.6.27-9-generic
  44.6GB: initrd.img
  44.7GB: vmlinuz

=============================== sda13/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda13
UUID=a587037f-79f0-4f23-a5cb-9eb8f8ef075d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda14
UUID=4c3ae1bd-b2ec-4865-8022-58c68dbdb4b0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================== sda13: Location  of files loaded by Grub: ==================


  17.5GB: boot/vmlinuz-2.6.27-7-generic
  17.5GB: vmlinuz

=============================== StdErr Messages: ===============================

No errors were reported.
```

The way I think I have the drive is 
Windows on sda1
ubuntu on sda13
linpus on sda6
crunchbang on sda11 and
dsl on sda10

.....well that's how it was intended anyway

---

### Post by theozzlives on 2009-01-26
I would recommend using VirtualBox.

---

### Post by 5BallJuggler on 2009-01-26
This is a copy of the current menu.lst file on the crunchbang partition

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
# kopt=root=UUID=ac8706be-c710-405d-8ecc-0745a2abc115 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=ac8706be-c710-405d-8ecc-0745a2abc115

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
uuid		ac8706be-c710-405d-8ecc-0745a2abc115
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=ac8706be-c710-405d-8ecc-0745a2abc115 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		ac8706be-c710-405d-8ecc-0745a2abc115
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=ac8706be-c710-405d-8ecc-0745a2abc115 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, memtest86+
uuid		ac8706be-c710-405d-8ecc-0745a2abc115
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

---

### Post by 5BallJuggler on 2009-01-27
Sorry Guys...

...I need help!

---

### Post by caljohnsmith on 2009-01-27
5BallJuggler, how about adding the following entries in your Crunchbang menu.lst:
```
title DSL
configfile (hd0,9)/boot/grub/menu.lst

title Linpus
configfile (hd0,5)/boot/grub/grub.conf
```
Also, it unfortunately looks like you can't boot Ubuntu on sda13 because Ubuntu is missing most of its boot files and Grub. Do you know how that might have happened?

---

### Post by 5BallJuggler on 2009-01-27
caljohnsmith,
   Thanks very much for your help, it works a treat, i'm going to change all of the boot scripts so i can boot between the front ends if I change my mind or make a mistake when booting.

   As for the Ubuntu install and the missing files, I don't know how it happened, i'm gonna try again again today before i get too much good stuff on the system, the only thing with any data is the XP partition and if that goes it's not a real issue.

   Once again, Thanks

---

