---
title: "Ubuntu Intrepid, dual boot, Vista"
date: 2009-04-11
forum: Installation &amp; Upgrades
---

### Post by emavio on 2009-04-11
I installed Ubuntu 8.10 on my Dell 1535 (with Vista installed  by the vendor). The partitions are as follows:

```
 Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          18      144553+   6  FAT16
/dev/sda2              19        1324    10485760    7  HPFS/NTFS
/dev/sda3            1325       13481    97651102+   b  W95 FAT32
/dev/sda4           13482       30401   135909900    5  Extended
/dev/sda5           13482       29286   126953631   83  Linux
/dev/sda6           29287       30401     8956206   82  Linux swap / Solaris

```


I modified menu.lst:

```
title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		68f8a70f-276b-4fe2-a982-4809597b4a19
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=68f8a70f-276b-4fe2-a982-4809597b4a19 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title Microsoft Windows Vista
rootnoverify (hd0,1)
savedefault
makeactive
chainloader +1

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		68f8a70f-276b-4fe2-a982-4809597b4a19
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=68f8a70f-276b-4fe2-a982-4809597b4a19 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		68f8a70f-276b-4fe2-a982-4809597b4a19
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=68f8a70f-276b-4fe2-a982-4809597b4a19 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		68f8a70f-276b-4fe2-a982-4809597b4a19
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=68f8a70f-276b-4fe2-a982-4809597b4a19 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		68f8a70f-276b-4fe2-a982-4809597b4a19
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```
Choosing Windows Vista from Grub bootloader leads to the error message:

> bootmgr is missing, please press Ctrl+alt+del.

Following the advice given here to other users, encountering the same problem, I downloaded  the Boot Info Script boot_info_script30.sh ([https://sourceforge.net/projects/bootinfoscript]("https://sourceforge.net/projects/bootinfoscript")/
and got the Boot Info:

```
============================= Boot Info Summary: ========================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda2': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda2 sda2 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda2 sda2 ntfs-3g force 0 0
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda2': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda2 sda2 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda2 sda2 ntfs-3g force 0 0

sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf0000000

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       289,169       289,107   6 FAT16
/dev/sda2    *        290,816    21,262,335    20,971,520   7 HPFS/NTFS
/dev/sda3          21,270,060   216,572,264   195,302,205   b W95 FAT32
/dev/sda4         216,572,265   488,392,064   271,819,800   5 Extended
/dev/sda5         216,572,328   470,479,589   253,907,262  83 Linux
/dev/sda6         470,479,653   488,392,064    17,912,412  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D8-0911" TYPE="vfat" 
/dev/sda2: UUID="2E62C8EA62C8B83B" LABEL="RECOVERY" TYPE="ntfs" 
/dev/sda3: UUID="960F-E8B8" TYPE="vfat" 
/dev/sda5: UUID="68f8a70f-276b-4fe2-a982-4809597b4a19" TYPE="ext3" 
/dev/sda6: UUID="1b97392d-edb4-4d2a-843a-aa34fd543fbc" TYPE="swap" 

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
lrm on /lib/modules/2.6.27-11-generic/volatile type tmpfs (rw,mode=755)
/dev/sda3 on /windows type vfat (rw,utf8,umask=007,gid=46)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/epetrisor/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=epetrisor)


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
# kopt=root=UUID=68f8a70f-276b-4fe2-a982-4809597b4a19 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=68f8a70f-276b-4fe2-a982-4809597b4a19

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
uuid		68f8a70f-276b-4fe2-a982-4809597b4a19
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=68f8a70f-276b-4fe2-a982-4809597b4a19 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title Microsoft Windows Vista
rootnoverify (hd0,1)
savedefault
makeactive
chainloader +1

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		68f8a70f-276b-4fe2-a982-4809597b4a19
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=68f8a70f-276b-4fe2-a982-4809597b4a19 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		68f8a70f-276b-4fe2-a982-4809597b4a19
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=68f8a70f-276b-4fe2-a982-4809597b4a19 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		68f8a70f-276b-4fe2-a982-4809597b4a19
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=68f8a70f-276b-4fe2-a982-4809597b4a19 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		68f8a70f-276b-4fe2-a982-4809597b4a19
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=68f8a70f-276b-4fe2-a982-4809597b4a19 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=960F-E8B8  /windows        vfat    utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=1b97392d-edb4-4d2a-843a-aa34fd543fbc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 146.0GB: boot/grub/menu.lst
 146.0GB: boot/grub/stage2
 145.9GB: boot/initrd.img-2.6.27-11-generic
 146.0GB: boot/initrd.img-2.6.27-7-generic
 146.0GB: boot/vmlinuz-2.6.27-11-generic
 146.0GB: boot/vmlinuz-2.6.27-7-generic
 145.9GB: initrd.img
 146.0GB: initrd.img.old
 146.0GB: vmlinuz
 146.0GB: vmlinuz.old


```

My question is, how dangerous is to make the:

```
Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda2 sda2 -o force
```

that is, what could happen if I force the shutdown? 
Or there is another way to remove the bug?

Thanks,
Em

---

### Post by zvacet on 2009-04-11
First I will ad this in your menu list 


### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

title Microsoft Windows Vista
rootnoverify (hd0,1)
savedefault
makeactive
chainloader +1


And read [this]("http://ubuntuforums.org/showthread.php?t=319814&page=2") and see if it works for you.

---

### Post by emavio on 2009-04-11
well, I tried the following:

```
sudo ntfsfix /dev/sda2
```

Now the boot info is clean:

```
============================= Boot Info Summary: =======================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =======================
```

but trying to choose Vista I get the same error message:

> bootmgr is missing, please press CTRL+ALT+DEl

I read a lot of posts on different forums, but it seems that no one was successful in removing this error message, following the given suggestions.

I still hope that someone will discover "the secret" behind > bootmgr is missing
[http://ubuntuforums.org/images/smilies/smiley-faces-80.gif](http://ubuntuforums.org/images/smilies/smiley-faces-80.gif)

---

### Post by zvacet on 2009-04-11
Did you looked link I posted to you?

---

### Post by emavio on 2009-04-11
> **zvacet said:**
> Did you looked link I posted to you?

Yes I looked and moreover I performed what they said:
1) Restarted with the Vista DVD and chose "Repair your computer".

Bootinfo modified from

```
Boot files/dirs:   /Windows/System32/winload.exe
```

to

```
Boot files/dirs:   /Boot/BCD /Windows/System32/winload.exe
```

2) Booted from the Vista DVD again and chose "Repair your computer" and then "Startup Repair".

The predicted result in the given link was:

>  Vista will re-add the MBR to the correct partition this time, and restart.

but in my case the following error message was displayed:

```
Cannot repair automatically, Missing Boot Manager
```

---

### Post by meierfra. on 2009-04-11
The file "bootmgr" is still missing. So boot from the Vista DVD, after "Repair Computer" choose "Command Line".

Then type

```
diskpart 
list volume

```
to determine the drive letter of your CDrom drive and your Vista partition.

Then type

```

exit
copy E:\bootmgr C:\
```
but replace "E" by the drive letter of your cdrom drive and "C" by the drive letter of your Vista partition.

Then type "exit"  and do another "startup repair"

---

### Post by emavio on 2009-04-11
> **meierfra. said:**
> The file "bootmgr" is still missing. So boot from the Vista DVD, after "Repair Computer" choose "Command Line".

Then type

```
diskpart 
list volume

```
to determine the drive letter of your CDrom drive and your Vista partition.

Then type

```

exit
copy E:\bootmgr C:\
```
but replace "E" by the drive letter of your cdrom drive and "C" by the drive letter of your Vista partition.

Then type "exit"  and do another "startup repair"

I performed what you wrote above, the system reported successful action, but after restarting got the message:

```
Windows failed to start. The Windows Boot Config Data file does not contain a valid OS entry
```


I think that the unique solution is to format the hard-disk and install only Ubuntu. :lolflag:

---

### Post by meierfra. on 2009-04-11
> I think that the unique solution is to format the hard-disk and install only Ubuntu

Well, that of course is  the best solution. 
(But not the unique solution: I'm sure with a little bit of extra work, you can get Vista boot. Sometimes it's enough to run "startup repair" a few more times, it tends to fix only one thing at the time. After that try "bootrec /rebuildbcd" from the Vista DVD command line. And if  none of  this  works check out this [link]("http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD"))

---

