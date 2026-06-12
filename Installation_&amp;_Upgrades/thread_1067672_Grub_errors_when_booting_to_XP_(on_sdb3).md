---
title: "Grub errors when booting to XP (on sdb3)"
date: 2009-02-12
forum: Installation &amp; Upgrades
---

### Post by Ubuntiac on 2009-02-12
Hi there,

I have XP installed on sdb3. It booted just fine.

Since installing Kubuntu on sdb1 GRUB doesn't seem able to boot it at all.
I can mount it just fine from inside Kubuntu. I didn't change any of the partitioning when I installed Kubuntu. 


My fdisk -l looks like:
```

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x20b320b3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda4   *           1           1           0    0  Empty
Partition 4 does not end on cylinder boundary.

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdebf17c9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       11473    92156841   83  Linux
/dev/sdb2           11474       12744    10209307+  82  Linux swap / Solaris
/dev/sdb3   *       12745       24321    92992252+   7  HPFS/NTFS

Disk /dev/sdc: 4007 MB, 4007657472 bytes
61 heads, 21 sectors/track, 6110 cylinders
Units = cylinders of 1281 * 512 = 655872 bytes
Disk identifier: 0x000690e3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        6111     3913727+   c  W95 FAT32 (LBA)

```

and my menu.lst entry looks like:
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb3
title		Microsoft Windows XP Professional
rootnoverify	(hd1,2)
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
```

I've also tried removing daveddefault and changing rootnoverify to 0,0 0,1
 0,2 1,0 1,1 1,2 2,0 2,1 and 2,2

Most just complain that the partition doesn't exist. A couple say that it's an unrecognized file format. 0,2 says "Starting up..." but stays that way forever.

I know that there's many GRUB posts (and I've read a few), but not many dealing with XP being on neither the first disk, nor the first partition.

Any ideas appreciated!

Thanks.

---

### Post by NuttyMonk on 2009-02-12
I've got a similar problem as you Ubuntiac although my copy of Win XP is on the first partition of a secondary SATA drive (not Raided).  I've also tried all of the combinations i can think of for the "rootnoverify" command
and i get the same "Starting..." message as you on one of the combinations but it doesn't load.

my fdisk -l

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x94469446

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x94939493

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        3187    25599546    7  HPFS/NTFS
/dev/sdb2            3188       14593    91618695    7  HPFS/NTFS

Disk /dev/sdc: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0b2244ac

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       36483   293049666    7  HPFS/NTFS
```

my menu.lst which i've altered a lot recently trying diff combinations
```

title Microsoft Windows XP Home Edition
#map (hd0) (hd1)
#map (hd1) (hd0)
rootnoverify (hd1,1)
makeactive
chainloader +1
boot
```

I'd like to see if there is any way we can both get our grubs working.  I've been to the grub website and looked at the docs but with little success.

NM

---

### Post by DerHesse on 2009-02-12
Hi Ubuntiac,
 
as I can see your Windows located on  /dev/sdc1  should be (hd2) in menue.list
 
(sda --> hd0, sdb --> hd1)

---

### Post by NuttyMonk on 2009-02-12
is the following correct?

sda = hd0
sdb = hd1
sdc = hd2
sdd = hd3
etc...

NM

---

### Post by DerHesse on 2009-02-12
> **NuttyMonk said:**
> is the following correct?
 
sda = hd0
sdb = hd1
sdc = hd2
sdd = hd3
etc...
 
NM
 
yes.
 
..and sda1 is hd(0,1)
        sda2 is hd(0,2)
...
        sdd5 is hd(3,5)

---

### Post by caljohnsmith on 2009-02-12
**Ubuntiac**, which entry you use for Windows in your Grub menu depends on which drive you are booting on start up, and since we don't yet know that, how about trying the following entries:
```
title       Windows XP (hd0)
root       (hd0,2)
chainloader +1

title       Windows XP (hd1)
rootnoverify     (hd1,2)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

title       Windows XP (hd2)
rootnoverify     (hd2,2)
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader +1
```
Please let me know exactly what happens when you try each entry from the Grub menu. We can work from there if you want.

---

### Post by Ubuntiac on 2009-02-12
Thanks so much for the suggestions everyone. With all your help I managed to figure this one out. It ended up being a couple of things needed changing.

The first was to go with caljohnsmith's first suggestion:
```
rootnoverify hd(0,2)
chainloader+1
```

Plus I needed to edit Windows' boot.ini file to say that its on disk 0, partition 3. Bizzarely windows seems to start counting hard drives from 0, but partitions from 1. Go figure.

Anyway hd0,3 on windows corresponds with 0,2 on GRUB, so together it boots fine now.

Thanks again to the most supportive tech community I know.

[CENTER]:KS:popcorn::KS[/CENTER]

---

### Post by caljohnsmith on 2009-02-12
Glad to hear you got Windows booting OK; cheers and enjoy your dual-boot between Ubuntu and Windows.

---

### Post by NuttyMonk on 2009-02-12
I've managed to get WinXP to load (or start to load) with Grub now but i'm getting an error about hal.dll (to do with boot.ini apparently).

I've read all of the posts i can find but i'm still not having any luck.

As far as i'm aware, the grub command "map" means that you can map one drive to another drive number so that windows doesn't have any problems loading (i.e. to do with the boot.ini file).  Whether i use the map command or not, the drive number i have to use to start to boot WinXP is always the same.  Does the map command only work for the windows side of things and not change the grub drive numbers?

e.g.

title Microsoft Windows XP Home Edition
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1,0)
savedefault
makeactive
chainloader +1
boot

If i remove those map commands, the drive number i have to use in rootnoverify is still always (hd1,0).  All of the other drive/partition numberings just give me errors.

Any help would be appreciated.

Cheers

NM

---

### Post by caljohnsmith on 2009-02-12
NuttyMonk, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your Windows booting problem might be.

---

### Post by NuttyMonk on 2009-02-12
Here's the data from the boot_info_script.

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
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

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

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
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x94469446

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   149,838,254   149,838,192  83 Linux
/dev/sda2         149,838,255   156,296,384     6,458,130   5 Extended
/dev/sda5         149,838,318   156,296,384     6,458,067  82 Linux swap / Solaris


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x94939493

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    51,199,154    51,199,092   7 HPFS/NTFS
/dev/sdb2          51,199,155   234,436,544   183,237,390   7 HPFS/NTFS


Drive sdc: _____________________________________________________________________

Disk /dev/sdc: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders, total 586114704 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0b2244ac

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   586,099,394   586,099,332   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="1af92474-067f-4605-8f30-64fef835460d" TYPE="ext3" 
/dev/sda5: UUID="5c50582a-5750-448d-857e-4dfc01a8e929" TYPE="swap" 
/dev/sdb1: UUID="823CB6873CB6762F" TYPE="ntfs" 
/dev/sdb2: UUID="54542B60542B43D8" LABEL="Art" TYPE="ntfs" 
/dev/sdc1: UUID="B2FC8F13FC8ED151" LABEL="Music" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
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
/dev/sdb2 on /media/Art type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdc1 on /media/Music type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/bone/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=bone)

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
# hiddenmenu

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
# kopt=root=UUID=1af92474-067f-4605-8f30-64fef835460d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=1af92474-067f-4605-8f30-64fef835460d

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
uuid		1af92474-067f-4605-8f30-64fef835460d
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=1af92474-067f-4605-8f30-64fef835460d ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		1af92474-067f-4605-8f30-64fef835460d
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=1af92474-067f-4605-8f30-64fef835460d ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		1af92474-067f-4605-8f30-64fef835460d
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=1af92474-067f-4605-8f30-64fef835460d ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		1af92474-067f-4605-8f30-64fef835460d
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=1af92474-067f-4605-8f30-64fef835460d ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		1af92474-067f-4605-8f30-64fef835460d
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Microsoft Windows XP Home Edition
map (hd0) (hd1)
map (hd1) (hd0)
root (hd1,0)
savedefault
makeactive
chainloader +1
boot

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=1af92474-067f-4605-8f30-64fef835460d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=5c50582a-5750-448d-857e-4dfc01a8e929 none swap sw 0 0
/dev/sdb2 /media/Art ntfs defaults 0 0
/dev/sdc1 /media/Music ntfs defaults 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

=================== sda1: Location of files loaded by Grub: ===================


  14.7GB: boot/grub/menu.lst
  14.6GB: boot/grub/stage2
  14.6GB: boot/initrd.img-2.6.27-11-generic
  14.6GB: boot/initrd.img-2.6.27-7-generic
  14.6GB: boot/vmlinuz-2.6.27-11-generic
  14.7GB: boot/vmlinuz-2.6.27-7-generic
  14.6GB: initrd.img
  14.6GB: initrd.img.old
  14.6GB: vmlinuz
  14.7GB: vmlinuz.old

================================ sdb1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect

================================ sdc1/boot.ini: ================================

[boot loader]

timeout=1

default=multi(0)disk(0)rdisk(2)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(2)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect
```

sdb1 is where my WinXP is located.  I'm not sure why it's saying i also have WinXP on sdc1 because i'm pretty sure that disk never had an operating system on it since i bought it.  Even if it did, it would have been formatted since then.  Odd.

Hope that's helpful, CJS.

Cheers

NM

---

### Post by caljohnsmith on 2009-02-12
OK, how about trying the following entry instead:
```
title       Windows XP
rootnoverify     (hd2,0)
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader +1
```
Let me know exactly what happens when you try it from the Grub menu, and we can work from there.

---

### Post by NuttyMonk on 2009-02-12
lol.  it took you five minutes to fix something which has been bugging me for days.

How come it's hd2 and not hd1?  Also, i'm sure i tried that before (hd2,0) so why wouldn't it have worked then and it did now?

Thanks for your help CJS.  :D

Cheers

NM

---

### Post by caljohnsmith on 2009-02-12
> **NuttyMonk said:**
> 
How come it's hd2 and not hd1?
That's because in Grub's Convoluted World, Grub determines the order of drives differently on start up than when you are in Ubuntu. On start up, Grub sees the order of drives as your BIOS boot order (so this is relevant for your menu.lst):
```
(hd0) = 1st boot drive
(hd1) = 2nd boot drive
(hd2) = 3rd boot drive
...etc.
```
But when you are in Ubuntu using Grub commands, Grub sees the order of drives as you are familiar with:
```
(hd0) = sda
(hd1) = sdb
(hd2) = sdc 
...etc.
```
So the bottom line is, since (hd2) worked to boot your sdb drive, that means your sdb drive must be 3rd in the BIOS boot order. That would also mean that sdc would then have to be 2nd in the BIOS boot order or (hd1). As you can see, there is no relationship between how Ubuntu orders the drives as sda, sdb, sdc, etc. and how Grub sees them on start up, because you can change your BIOS boot order as you please. Anyway, glad you can boot Windows now; cheers and enjoy Ubuntu and Windows. :)

---

