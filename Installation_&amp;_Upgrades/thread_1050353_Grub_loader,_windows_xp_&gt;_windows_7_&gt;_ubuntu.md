---
title: "Grub loader, windows xp &gt; windows 7 &gt; ubuntu 8.10."
date: 2009-01-25
forum: Installation &amp; Upgrades
---

### Post by dumble on 2009-01-25
Hello,

I have a triple boot with windows xp, windows 7 and ubuntu 8.10. When i boot my computer i can choose in grub-menu for ubuntu and vista/longhorn (loader]. When I press vista/longhorn it takes me to a Windows Boot Manager with options for:
- Earlier version of Windows
- Windows 7

I want to get rid of windows boot manager and place windows7 and windowsxp in the GRUB-menu. Here is my boot-info:
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     
    Operating System:  Windows Vista
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Boot file info:     
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Boot file info:     
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Schijf /dev/sda: 250.0 GB, 250059350016 bytes
255 koppen, 63 sectoren/spoor, 30401 cilinders, totaal 488397168 sectoren
Eenheid = sectoren van 1 * 512 = 512 bytes
Schijf-ID: 0x00067b7f

Partition  Boot        Start          End         Size  Id System

/dev/sda1    *            63  488,375,999  488,375,937   7 HPFS/NTFS


Drive sdb: _____________________________________________________________________

Schijf /dev/sdb: 250.0 GB, 250059350016 bytes
255 koppen, 63 sectoren/spoor, 30401 cilinders, totaal 488397168 sectoren
Eenheid = sectoren van 1 * 512 = 512 bytes
Schijf-ID: 0xb87eb87e

Partition  Boot        Start          End         Size  Id System

/dev/sdb1                 63  244,204,064  244,204,002   7 HPFS/NTFS
/dev/sdb2        244,204,065  305,251,064   61,047,000  83 Linux
/dev/sdb3        305,251,065  312,946,199    7,695,135  82 Linux wisselgeheugen
/dev/sdb4        312,946,200  488,392,064  175,445,865  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="E404EE7A04EE4F5C" TYPE="ntfs" 
/dev/sdb1: UUID="2E086290086256BD" TYPE="ntfs" 
/dev/sdb2: UUID="ce7e7404-fc20-4a27-888a-e71ca94632e7" TYPE="ext3" 
/dev/sdb3: UUID="c58dcc96-1b78-4ef5-8ea2-b7176a59312b" TYPE="swap" 
/dev/sdb4: UUID="6cad1e87-26db-4cbe-bf7a-f7dd375835ed" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/sdb2 on / type ext3 (rw,relatime,errors=remount-ro)
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
/dev/sdb4 on /home type ext3 (rw,relatime)
/dev/sdb1 on /windows7 type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda1 on /windowsxp type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/luuk/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=luuk)

================================ sda1/boot.ini: ================================

;

;Warning: Boot.ini is used on Windows XP and earlier operating systems.

;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.

;

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT


=========================== sdb2/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=ce7e7404-fc20-4a27-888a-e71ca94632e7 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=ce7e7404-fc20-4a27-888a-e71ca94632e7

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
uuid		ce7e7404-fc20-4a27-888a-e71ca94632e7
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=ce7e7404-fc20-4a27-888a-e71ca94632e7 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		ce7e7404-fc20-4a27-888a-e71ca94632e7
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=ce7e7404-fc20-4a27-888a-e71ca94632e7 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		ce7e7404-fc20-4a27-888a-e71ca94632e7
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=ce7e7404-fc20-4a27-888a-e71ca94632e7 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		ce7e7404-fc20-4a27-888a-e71ca94632e7
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=ce7e7404-fc20-4a27-888a-e71ca94632e7 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		ce7e7404-fc20-4a27-888a-e71ca94632e7
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


=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb2
UUID=ce7e7404-fc20-4a27-888a-e71ca94632e7 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb4
UUID=6cad1e87-26db-4cbe-bf7a-f7dd375835ed /home           ext3    relatime        0       2
# /dev/sdb1
UUID=2E086290086256BD /windows7       ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda1
UUID=E404EE7A04EE4F5C /windowsxp      ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb3
UUID=c58dcc96-1b78-4ef5-8ea2-b7176a59312b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb2: Location  of files loaded by Grub: ===================


 154.8GB: boot/grub/menu.lst
 154.8GB: boot/grub/stage2
 154.8GB: boot/initrd.img-2.6.27-7-generic
 154.8GB: boot/initrd.img-2.6.27-9-generic
 154.8GB: boot/vmlinuz-2.6.27-7-generic
 154.8GB: boot/vmlinuz-2.6.27-9-generic
 154.8GB: initrd.img
 154.8GB: initrd.img.old
 154.8GB: vmlinuz
 154.8GB: vmlinuz.old

=============================== StdErr Messages: ===============================

No errors were reported.
```

I hope someone can tell me what to do, thanks :D

---

### Post by caljohnsmith on 2009-01-25
OK, how about doing the following:
```
sudo cp -r /windowsxp/Boot /windowsxp/bootmgr /windows7
```
Let me know if that command returns any errors, but if it doesn't, then open your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And change your Windows entry to the two following entries:
```
title Windows XP
root (hd0,0)
chainloader +1

title Windows 7
root (hd1,0)
map (hd1) (hd0)
map (hd0) (hd1)
chainloader +1
```
Next boot your Windows 7 Install CD, go to the command line, and do:
```
diskpart
```
And at the diskpart prompt:
```
list volume
exit
```
Find the drive letter of your Windows 7 installation on sdb1, and then do:
```
bcdedit /store C:\boot\bcd /set {default} osdevice boot
bcdedit /store C:\boot\bcd /set {default} device boot
bcdedit /store C:\boot\bcd /set {bootmgr} device boot
bcdedit /store C:\boot\bcd /set {memdiag} device boot
```
And replace "C" in all the commands above with the drive letter of your Windows 7 install. Next find the drive letter of your Windows XP install on sda1 (using diskpart again), and then try:
```
E:\boot\bootsect.exe /nt52 C:
```
But replace "E" with the drive letter of the Windows 7 CD, and also replace "C" with the drive letter of the Windows XP install. If the Windows 7 CD does not have the "bootsect" command, let me know and we can work around it. After you are done with everything above, reboot, try booting XP and Win7 from your Grub menu, and let me know exactly what happens. We can work from there if you want.

---

### Post by dumble on 2009-01-25
Hi caljohnsmith, before i can begin i have to download and burn windows7 again. I was out of dvd's so i burned it on a RW-dvd and that dvd has been used for about 5 movies since i burned windows7 on it :p

The first command did not have any errors, so thats a good start :). I have one question though:
You said 'replace "C" in all the commands above with the drive letter of your Windows 7 install. Next find the drive letter of your Windows XP install on sda1 (using diskpart again)'

The problem is, when i am in windows7 the drive letter is C, and the driveletter of windowsXP is E. When i am booted in windowsXP the driveletter is C, and the driveletter of windows7 is E. Really confusing, i know..

---

### Post by caljohnsmith on 2009-01-25
> **dumble said:**
> 
The first command did not have any errors, so thats a good start :). I have one question though:
You said 'replace "C" in all the commands above with the drive letter of your Windows 7 install. Next find the drive letter of your Windows XP install on sda1 (using diskpart again)'

The problem is, when i am in windows7 the drive letter is C, and the driveletter of windowsXP is E. When i am booted in windowsXP the driveletter is C, and the driveletter of windows7 is E. Really confusing, i know..
That's fine, the drive letters may change depending on which Windows you boot into, but I'm referring to the drive letters that the Win 7 CD assigns to your NTFS partitions while you use the Win 7 CD. Those drive letters should not change at least while you are using the Win 7 CD, so if you check the drive letters with the "diskpart" method from my previous post while using the Win 7 CD, you should be OK.

---

### Post by hape65 on 2009-05-10
hi
i'm searching for a theme which is in the direction of this one. I have installed Grub with 2XPs and a few Ubuntus and 1 Win7. To this point everything works ok. Now i installed on the same machine a second Win7 and now i have no chance without the "bootmanager" from Win7 to get to the seond installed one. If i try to boot the second Win7 partition (out of Grub) directly there is a message "no bootmanager found". If i start the first installed Win7 i get the Win bootmanager and can start the second installed Win7.
So my finally question: can i get rid of the bcd and put this information to Grub so that i can start every Win7 out of Grub without the Win7 Bootmanager 
or something like this (not to say workaround)
thx a lot for help
hape65

---

