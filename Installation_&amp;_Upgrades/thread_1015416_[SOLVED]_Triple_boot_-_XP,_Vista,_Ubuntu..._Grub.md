---
title: "[SOLVED] Triple boot - XP, Vista, Ubuntu... Grub?"
date: 2008-12-18
forum: Installation &amp; Upgrades
---

### Post by greenman1313 on 2008-12-18
Hello everyone, First things first, i just installed Ubuntu yesterday, and already I think I enjoy it more than XP Pro, which I've been using for years!! Now I just need to figure out how to play my video games on it...

Also, I'm hesitant to post this question, as I've searched through many, many similar threads, but alas, I haven't found the answers I need - so here I go.

I have two hard drives. I have XP Pro on one hard drive, and Vista 64 Ultimate on the other. When it was just those two OS's, I would use the default Windows boot loader (I think it is a part of Vista - and thus, it might be on the Vista partition, I would assume?). When I would start up the computer, it would state something like: "boot into Vista or an earlier version of Windows"  (something like that).

I put Ubuntu on a partition on the Vista hard drive. When I installed it, I put grub on (hd0). I believe that is the XP hard drive.

Now, if I just boot up the computer, I get the Grub boot loader, and it allows me to select ubuntu just fine, but it also has an option to select "Longhorn". When I select that, I get some error, and it won't boot into Windows.

I can use GAG, which I placed on a CD yesterday, and that gives me the option to select the Windows OS, and when I boot, it gives me the boot choices which I've historically had (Vista or an earlier version of Windows).

SOOO... if I want to boot into Ubuntu, I don't use GAG - the computer just boots up into Grub, and I can start Ubuntu. If I want to use Vista or XP, I just insert the GAG disc, and I can boot into the boot loader that gives me the option of the two Windows OS's. 


My question: Is there a way to use Grub (or GAG), to be able to load all three operating systems from one screen? Or at least, without having to put the GAG disc in to boot into Windows?


I typed "sudo fdisk -lu" into the Ubuntu terminal, and here's what I get:




[PHP]Disk /dev/sda: 320.0 GB, 320072933376 bytes
154 heads, 29 sectors/track, 139978 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x83d67900

 Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          29   625137281   312568626+   7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd985e7a2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   502257342   251128640    7  HPFS/NTFS
/dev/sdb2       502257664   594422568    46082452+  83  Linux
/dev/sdb3       594437130   625137344    15350107+  82  Linux swap / Solaris[/PHP]






Sorry about the LONG post, I just want to make myself clear. Please, I am new to Ubuntu, and any instructions you may give me must be spelled out, as I'm not familiar with all the lingo yet.


Thanks!

---

### Post by upchucky on 2008-12-18
look for advanced supergrub, and knoppix.

supergrub will set up all os's and knoppix can fix broken windows if needed.

there is a slight small learning curve to use supergrub but if you learn you will be a bootloader guru.

---

### Post by caljohnsmith on 2008-12-18
> **greenman1313 said:**
> 
My question: Is there a way to use Grub (or GAG), to be able to load all three operating systems from one screen? Or at least, without having to put the GAG disc in to boot into Windows?

Yes, you can use Grub to boot all your OSes, including XP and Vista. If you want to boot XP and Vista separately from the Grub menu, you will have to move their boot files back to their respective partitions and maybe fix their boot sectors. It's not too big of a deal, and I can help you with that if you want. But in order to get a clearer picture of your setup, how about booting your Live CD, open a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "boot_info_results.txt" file on your desktop; please copy/paste the contents of that file to your next post. That will help clarify your setup and what it might take to boot XP and Vista separately. :)

---

### Post by greenman1313 on 2008-12-18
Caljohnsmith: Ok, here it is. I hope this is what you wanted, it's a HUGE file!!

[PHP]Grub is installed in the MBR of /dev/sda and looks on boot drive #2 in partition #2 for its boot files.
Windows is installed in the MBR of /dev/sdb

sda1:
    File system:  ntfs
    Boot sector  type:  Vista
    Boot sector  info:  According to the info in the boot sector, sda1 starts at sector 29
    Operating System: XP
    Boot files/directories present:  /boot.ini /bootmgr /ntldr /NTDETECT.COM /Boot

sdb1:
    File system:  ntfs
    Boot sector  type:  Unknown
    Boot sector  info:  According to the info in the boot sector, sdb1 starts at sector 63
    Operating System: Vista
    Boot files/directories present: 

sdb2:
    File system:  ext3
    Boot sector  type:  Unknown
    Boot sector  info:  
    Operating System: Linux
    Boot files/directories present:  /boot/grub/menu.lst /boot /boot/grub

sdb3:
    File system:  swap


Disk /dev/sda: 320.0 GB, 320072933376 bytes
154 heads, 29 sectors/track, 139978 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x83d67900

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          29   625137281   312568626+   7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd985e7a2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   502257342   251128640    7  HPFS/NTFS
/dev/sdb2       502257664   594422568    46082452+  83  Linux
/dev/sdb3       594437130   625137344    15350107+  82  Linux swap / Solaris
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       29, size=625137253, Id= 7, bootable
/dev/sda2 : start=        0, size=        0, Id= 0
/dev/sda3 : start=        0, size=        0, Id= 0
/dev/sda4 : start=        0, size=        0, Id= 0
# partition table of /dev/sdb
unit: sectors

/dev/sdb1 : start=       63, size=502257280, Id= 7
/dev/sdb2 : start=502257664, size= 92164905, Id=83
/dev/sdb3 : start=594437130, size= 30700215, Id=82
/dev/sdb4 : start=        0, size=        0, Id= 0

sda1/boot.ini

;

;Warning: Boot.ini is used on Windows XP and earlier operating systems.

;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.

;

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT


sda1/Boot

total 528
drwxrwxrwx 1 root root   4096 2008-03-18 18:34 .
drwxrwxrwx 1 root root  12288 2008-12-19 03:01 ..
-rwxrwxrwx 1 root root  24576 2008-12-14 18:10 BCD
-rwxrwxrwx 1 root root  21504 2008-12-14 17:42 BCD.LOG
-rwxrwxrwx 2 root root      0 2008-03-05 02:56 BCD.LOG1
-rwxrwxrwx 2 root root      0 2008-03-05 02:56 BCD.LOG2
-rwxrwxrwx 1 root root  65536 2008-03-05 02:56 bootstat.dat
drwxrwxrwx 1 root root      0 2008-03-18 18:34 cs-CZ
drwxrwxrwx 1 root root      0 2008-03-18 18:34 da-DK
drwxrwxrwx 1 root root      0 2008-03-18 18:34 de-DE
drwxrwxrwx 1 root root      0 2008-03-18 18:34 el-GR
drwxrwxrwx 1 root root      0 2008-03-18 18:34 en-US
drwxrwxrwx 1 root root      0 2008-03-18 18:34 es-ES
drwxrwxrwx 1 root root      0 2008-03-18 18:34 fi-FI
drwxrwxrwx 1 root root      0 2008-03-18 18:34 Fonts
drwxrwxrwx 1 root root      0 2008-03-18 18:34 fr-FR
drwxrwxrwx 1 root root      0 2008-03-18 18:34 hu-HU
drwxrwxrwx 1 root root      0 2008-03-18 18:34 it-IT
drwxrwxrwx 1 root root      0 2008-03-18 18:34 ja-JP
drwxrwxrwx 1 root root      0 2008-03-18 18:34 ko-KR
-rwxrwxrwx 1 root root 406584 2008-01-19 07:43 memtest.exe
drwxrwxrwx 1 root root      0 2008-03-18 18:34 nb-NO
drwxrwxrwx 1 root root      0 2008-03-18 18:34 nl-NL
drwxrwxrwx 1 root root      0 2008-03-18 18:34 pl-PL
drwxrwxrwx 1 root root      0 2008-03-18 18:34 pt-BR
drwxrwxrwx 1 root root      0 2008-03-18 18:34 pt-PT
drwxrwxrwx 1 root root      0 2008-03-18 18:34 ru-RU
drwxrwxrwx 1 root root      0 2008-03-18 18:34 sv-SE
drwxrwxrwx 1 root root      0 2008-03-18 18:34 tr-TR
drwxrwxrwx 1 root root      0 2008-03-18 18:34 zh-CN
drwxrwxrwx 1 root root      0 2008-03-18 18:34 zh-HK
drwxrwxrwx 1 root root      0 2008-03-18 18:34 zh-TW

sdb2/boot/grub/menu.lst

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
# kopt=root=UUID=cad6ec78-ac39-4e06-8065-53dff3693e1a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=cad6ec78-ac39-4e06-8065-53dff3693e1a

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
uuid		cad6ec78-ac39-4e06-8065-53dff3693e1a
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=cad6ec78-ac39-4e06-8065-53dff3693e1a ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		cad6ec78-ac39-4e06-8065-53dff3693e1a
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=cad6ec78-ac39-4e06-8065-53dff3693e1a ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		cad6ec78-ac39-4e06-8065-53dff3693e1a
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=cad6ec78-ac39-4e06-8065-53dff3693e1a ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		cad6ec78-ac39-4e06-8065-53dff3693e1a
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=cad6ec78-ac39-4e06-8065-53dff3693e1a ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		cad6ec78-ac39-4e06-8065-53dff3693e1a
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


sdb2/boot

total 25524
drwxr-xr-x  3 root root    4096 2008-12-17 18:56 .
drwxr-xr-x 21 root root    4096 2008-12-18 03:17 ..
-rw-r--r--  1 root root  503560 2008-11-04 20:53 abi-2.6.27-7-generic
-rw-r--r--  1 root root  503560 2008-11-20 23:30 abi-2.6.27-9-generic
-rw-r--r--  1 root root   85316 2008-11-04 20:53 config-2.6.27-7-generic
-rw-r--r--  1 root root   85316 2008-11-20 23:30 config-2.6.27-9-generic
drwxr-xr-x  2 root root    4096 2008-12-17 18:56 grub
-rw-r--r--  1 root root 8669816 2008-12-17 18:56 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root 8669315 2008-12-17 18:56 initrd.img-2.6.27-9-generic
-rw-r--r--  1 root root  124152 2008-09-11 20:11 memtest86+.bin
-rw-r--r--  1 root root 1352144 2008-11-04 20:53 System.map-2.6.27-7-generic
-rw-r--r--  1 root root 1352144 2008-11-20 23:30 System.map-2.6.27-9-generic
-rw-r--r--  1 root root    1130 2008-11-04 20:57 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root    1130 2008-11-20 23:32 vmcoreinfo-2.6.27-9-generic
-rw-r--r--  1 root root 2339552 2008-11-04 20:53 vmlinuz-2.6.27-7-generic
-rw-r--r--  1 root root 2339712 2008-11-20 23:30 vmlinuz-2.6.27-9-generic

sdb2/boot/grub

total 224
drwxr-xr-x 2 root root   4096 2008-12-17 18:56 .
drwxr-xr-x 3 root root   4096 2008-12-17 18:56 ..
-rw-r--r-- 1 root root    197 2008-12-17 18:37 default
-rw-r--r-- 1 root root     30 2008-12-17 18:37 device.map
-rw-r--r-- 1 root root   8108 2008-12-17 18:37 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2008-12-17 18:37 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-12-17 18:37 installed-version
-rw-r--r-- 1 root root   8712 2008-12-17 18:37 jfs_stage1_5
-rw-r--r-- 1 root root   5101 2008-12-17 18:56 menu.lst
-rw-r--r-- 1 root root   5017 2008-12-17 18:56 menu.lst~
-rw-r--r-- 1 root root   7352 2008-12-17 18:37 minix_stage1_5
-rw-r--r-- 1 root root   9756 2008-12-17 18:37 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-12-17 18:37 stage1
-rw-r--r-- 1 root root 121460 2008-12-17 18:37 stage2
-rw-r--r-- 1 root root   9556 2008-12-17 18:37 xfs_stage1_5

StdErr Messages 

cat: /tmp/BootInfo/Unknown_MBR: No such file or directory[/PHP]






Thanks for the help. I really appreciate it!   :D

---

### Post by caljohnsmith on 2008-12-19
OK, great, that helps clarify your setup quite a bit. :) How about doing the following:
```
sudo mkdir /mnt/sda1 /mnt/sdb1
sudo mount /dev/sda1 /mnt/sda1
sudo mount /dev/sdb1 /mnt/sdb1
sudo mv /mnt/sda1/Boot /mnt/sda1/bootmgr /mnt/sdb1
```
Next you'll need to boot your Windows XP Install CD, go to the "recovery console", and do:
```
map
```
That will show the drive letters for your Windows partitions. Choose whichever is Windows XP (probably will be "C"), which should be the single partition on your sda drive. Then do:
```
fixboot [COLOR="Blue"]<drive letter>[/COLOR]:
```
And replace <drive letter> with C or D or whichever is the XP partition. After you are done with that, next thing to do would be to boot your Windows Vista Install CD, go to the command line and do:
```
diskpart
```
And at the diskpart prompt type:
```
list volume
exit
```
Find the drive letter for Vista from the above commands, for instance it might be "D", which we will assume in the next commands, so change it if the drive letter is different:
```
bcdedit /store [COLOR="Blue"]D:[/COLOR]\boot\bcd /set {default} osdevice boot
bcdedit /store [COLOR="Blue"]D:[/COLOR]\boot\bcd /set {default} device boot
bcdedit /store [COLOR="Blue"]D:[/COLOR]\boot\bcd /set {bootmgr} device boot
bcdedit /store [COLOR="Blue"]D:[/COLOR]\boot\bcd /set {memdiag} device boot
```
Next open up your menu.lst in Ubuntu:
```
gksudo gedit /boot/grub/menu.lst
```
And at the bottom, replace your existing Windows entry with the following two entries:
```
title Windows XP
root (hd0,0)
chainloader +1

title Windows Vista
root (hd1,0)
map  (hd0) (hd1)
map  (hd1) (hd0)
chainloader +1
```
And finally reboot, try to boot XP and Vista from the Grub menu, and let me know exactly what happens. It might be that we will need to repair the Vista boot sector, because the script you ran was not able to properly identify it. But first give the above steps a try and let me know what happens. :)

P.S. Many thanks to forum member meierfra for providing the above Vista bcdedit hack.

---

### Post by greenman1313 on 2008-12-20
Well, I was going through the list that you gave me, and while I was trying to access the command line from the Vista install CD, I somehow ended up re-installing Vista altogether (I never did figure out how to access command line in the Vista install CD, by the way). :confused:

So at this point, I am thinking about re-installing XP as well, as I've been having some blue screen issues on that OS for a few months. I believe it is due to registry issues, but that's not really relevant to the issue at hand. 

I ended up reinstalling Vista on the same partition as it was on before, so nothing has changed there. 

I'm going to reinstall XP on my main hard drive, and report back here once I get that squared away. I would hate to get the bootloading issue taken care of, and have to reinstall XP anyway, so I'm going to pre-emptively install XP before I go any further with the bootloading stuff. 

Thanks again for all your help. I'll let you know when XP has been "reborn". :)

---

### Post by greenman1313 on 2008-12-22
Okay, I reinstalled Vista on my second hard drive the other day, and I reinstalled Xp on my primary hard drive today.

When I start my computer up, I boot right into XP - no option for Vista whatsoever. I did install Vista first, and XP last. I completely erased Ubuntu and the swap off of the Vista drive the other night as well. Now I just have my XP on my FULL HD, and Vista on a HD with two partitions (the area where I plan to put Ubuntu is still "raw - unformatted", and is about 60GB). I will need to reinstall Ubuntu and the swap space on the partitioned area on my Vista HD... when I figure out exactly what I'm supposed to do of course.

Anyways, since we're pretty much starting over from scratch, here's the results for "sudo fdisk -lu" from booting into Live disk.

[PHP]Disk /dev/sda: 320.0 GB, 320072933376 bytes
154 heads, 29 sectors/track, 139978 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x83d67900

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          29   625137281   312568626+   7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd985e7a2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   502257342   251128640    7  HPFS/NTFS
[/PHP]






Also, since I was told to do this before, here is the results of Caljohnsmith's "boot_info_results.txt" file, that I just re-ran:

[PHP]Windows is installed in the MBR of /dev/sda
Windows is installed in the MBR of /dev/sdb

sda1:
    File system:  ntfs
    Boot sector  type:  XP
    Boot sector  info:  According to the info in the boot sector, sda1 starts at sector 29.
    Operating System: XP
    Boot files/directories present:  /boot.ini /ntldr /NTDETECT.COM

sdb1:
    File system:  ntfs
    Boot sector  type:  XP
    Boot sector  info:  According to the info in the boot sector, sdb1 starts at sector 63.
    Operating System: Vista
    Boot files/directories present:  /bootmgr /Boot


Disk /dev/sda: 320.0 GB, 320072933376 bytes
154 heads, 29 sectors/track, 139978 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x83d67900

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          29   625137281   312568626+   7  HPFS/NTFS

Warning: partition 1 does not end at a cylinder boundary


Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd985e7a2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   502257342   251128640    7  HPFS/NTFS

Warning: partition 1 does not end at a cylinder boundary
Warning: partition 1 does not end at a cylinder boundary

/dev/sda1: UUID="CAD0DDA5D0DD97D1" TYPE="ntfs" 
/dev/sdb1: UUID="4410EAE810EADFC2" LABEL="Vista Disk" TYPE="ntfs" 
/dev/loop0: TYPE="squashfs" 

sda1/boot.ini

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


sdb1/Boot

total 540
drwxrwxrwx 1 root root   4096 2008-03-18 18:34 .
drwxrwxrwx 1 root root  24576 2008-12-22 08:31 ..
-rwxrwxrwx 1 root root  24576 2008-12-14 18:10 BCD
-rwxrwxrwx 1 root root  21504 2008-12-14 17:42 BCD.LOG
-rwxrwxrwx 1 root root      0 2008-03-05 02:56 BCD.LOG1
-rwxrwxrwx 1 root root      0 2008-03-05 02:56 BCD.LOG2
-rwxrwxrwx 1 root root  65536 2008-03-05 02:56 bootstat.dat
drwxrwxrwx 1 root root      0 2008-03-18 18:34 cs-CZ
drwxrwxrwx 1 root root      0 2008-03-18 18:34 da-DK
drwxrwxrwx 1 root root      0 2008-03-18 18:34 de-DE
drwxrwxrwx 1 root root      0 2008-03-18 18:34 el-GR
drwxrwxrwx 1 root root      0 2008-03-18 18:34 en-US
drwxrwxrwx 1 root root      0 2008-03-18 18:34 es-ES
drwxrwxrwx 1 root root      0 2008-03-18 18:34 fi-FI
drwxrwxrwx 1 root root      0 2008-03-18 18:34 Fonts
drwxrwxrwx 1 root root      0 2008-03-18 18:34 fr-FR
drwxrwxrwx 1 root root      0 2008-03-18 18:34 hu-HU
drwxrwxrwx 1 root root      0 2008-03-18 18:34 it-IT
drwxrwxrwx 1 root root      0 2008-03-18 18:34 ja-JP
drwxrwxrwx 1 root root      0 2008-03-18 18:34 ko-KR
-rwxrwxrwx 1 root root 406584 2008-01-19 07:43 memtest.exe
drwxrwxrwx 1 root root      0 2008-03-18 18:34 nb-NO
drwxrwxrwx 1 root root      0 2008-03-18 18:34 nl-NL
drwxrwxrwx 1 root root      0 2008-03-18 18:34 pl-PL
drwxrwxrwx 1 root root      0 2008-03-18 18:34 pt-BR
drwxrwxrwx 1 root root      0 2008-03-18 18:34 pt-PT
drwxrwxrwx 1 root root      0 2008-03-18 18:34 ru-RU
drwxrwxrwx 1 root root      0 2008-03-18 18:34 sv-SE
drwxrwxrwx 1 root root      0 2008-03-18 18:34 tr-TR
drwxrwxrwx 1 root root      0 2008-03-18 18:34 zh-CN
drwxrwxrwx 1 root root      0 2008-03-18 18:34 zh-HK
drwxrwxrwx 1 root root      0 2008-03-18 18:34 zh-TW

StdErr Messages [/PHP]






Ultimately, I want to be able to boot into all three OS's from one main boot screen on start-up. Any ideas on where to start?

Thanks so much for your time everybody!

:)

---

### Post by caljohnsmith on 2008-12-22
OK, your situation is actually as expected; since you installed XP after Vista, XP took over the booting process, but since XP doesn't know how to handle Vista, you can't boot Vista now as you well know. It would have been better if you would have installed XP first, then Vista, and then when Vista takes over the booting process, Vista will give you the option to boot Vista or XP. But that's OK the way you have it now; how about going ahead and reinstalling Ubuntu, and afterwards post the output of that script again, and then we can work from there to boot all three of your OSes from the Grub menu.

---

### Post by greenman1313 on 2008-12-22
I finally installed Ubuntu - it gave me some trouble, as it was telling me that it couldn't install it for some reason, but I re-checked the disc, and it came back 100% fine. I finally got it to load and now I get error 18 from Grub, and I can't boot into any OS without first using GAG, and even then I can only boot into XP.


Ok, here are the "sudo fdisk -lu" results:

[PHP]Disk /dev/sda: 320.0 GB, 320072933376 bytes
154 heads, 29 sectors/track, 139978 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x83d67900

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          29   625137281   312568626+   7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd985e7a2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   502257342   251128640    7  HPFS/NTFS
/dev/sdb2       502272225   625137344    61432560    5  Extended
/dev/sdb5       502272288   504987209     1357461   82  Linux swap / Solaris
/dev/sdb6       505180053   625137344    59978646   83  Linux
[/PHP]





Here are the results of the "boot_info_results.txt":

[PHP]Grub is installed in the MBR of /dev/sda and looks on boot drive #2 in partition #6 for its boot files.
Windows is installed in the MBR of /dev/sdb
No known boot loader is installed in the MBR of /dev/sdc
No known boot loader is installed in the MBR of /dev/sdd

sda1:
    File system:  ntfs
    Boot sector  type:  XP
    Boot sector  info:  According to the info in the boot sector, sda1 starts at sector 29.
    Operating System: XP
    Boot files/directories present:  /boot.ini /ntldr /NTDETECT.COM /Boot

sdb1:
    File system:  ntfs
    Boot sector  type:  XP
    Boot sector  info:  According to the info in the boot sector, sdb1 starts at sector 63.
    Operating System: Vista
    Boot files/directories present:  /bootmgr /Boot

sdb2:
    File system:  Extended Partition

sdb5:
    File system:  swap

sdb6:
    File system:  ext3
    Boot sector  type:  No Boot Loader
    Boot sector  info:  
    Operating System: Ubuntu 8.10 \n \l
    Boot files/directories present:  /boot/grub/menu.lst /etc/fstab /boot /boot/grub


Disk /dev/sda: 320.0 GB, 320072933376 bytes
154 heads, 29 sectors/track, 139978 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x83d67900

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          29   625137281   312568626+   7  HPFS/NTFS

Warning: partition 1 does not end at a cylinder boundary


Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd985e7a2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   502257342   251128640    7  HPFS/NTFS
/dev/sdb2       502272225   625137344    61432560    5  Extended
/dev/sdb5       502272288   504987209     1357461   82  Linux swap / Solaris
/dev/sdb6       505180053   625137344    59978646   83  Linux

Warning: partition 1 does not end at a cylinder boundary
Warning: partition 1 does not end at a cylinder boundary


Warning: partition 1 does not end at a cylinder boundary
Warning: partition 1 does not end at a cylinder boundary
/dev/sdc: No medium found

sfdisk: cannot open /dev/sdc for reading


Warning: partition 1 does not end at a cylinder boundary
Warning: partition 1 does not end at a cylinder boundary
/dev/sdc: No medium found

sfdisk: cannot open /dev/sdc for reading
/dev/sdd: No medium found

sfdisk: cannot open /dev/sdd for reading

/dev/sda1: UUID="CAD0DDA5D0DD97D1" TYPE="ntfs" 
/dev/sdb1: UUID="4410EAE810EADFC2" LABEL="Vista Disk" TYPE="ntfs" 
/dev/sdb5: UUID="920f3d86-a5a9-44c4-8240-dd3b011b3917" TYPE="swap" 
/dev/sdb6: UUID="d6d632ac-b44c-44dc-8587-d43bc2ce4f36" SEC_TYPE="ext2" TYPE="ext3" 
/dev/loop0: TYPE="squashfs" 

sda1/boot.ini

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


sda1/Boot

total 32
drwxrwxrwx 1 root root     0 2008-12-22 19:43 .
drwxrwxrwx 1 root root  8192 2008-12-22 19:43 ..
-rwxrwxrwx 1 root root 12288 2008-12-22 19:43 BCD
-rwxrwxrwx 1 root root  9216 2008-12-22 19:43 BCD.LOG

sdb1/Boot

total 540
drwxrwxrwx 1 root root   4096 2008-03-18 18:34 .
drwxrwxrwx 1 root root  24576 2008-12-22 18:34 ..
-rwxrwxrwx 1 root root  24576 2008-12-14 18:10 BCD
-rwxrwxrwx 1 root root  21504 2008-12-14 17:42 BCD.LOG
-rwxrwxrwx 1 root root      0 2008-03-05 02:56 BCD.LOG1
-rwxrwxrwx 1 root root      0 2008-03-05 02:56 BCD.LOG2
-rwxrwxrwx 1 root root  65536 2008-03-05 02:56 bootstat.dat
drwxrwxrwx 1 root root      0 2008-03-18 18:34 cs-CZ
drwxrwxrwx 1 root root      0 2008-03-18 18:34 da-DK
drwxrwxrwx 1 root root      0 2008-03-18 18:34 de-DE
drwxrwxrwx 1 root root      0 2008-03-18 18:34 el-GR
drwxrwxrwx 1 root root      0 2008-03-18 18:34 en-US
drwxrwxrwx 1 root root      0 2008-03-18 18:34 es-ES
drwxrwxrwx 1 root root      0 2008-03-18 18:34 fi-FI
drwxrwxrwx 1 root root      0 2008-03-18 18:34 Fonts
drwxrwxrwx 1 root root      0 2008-03-18 18:34 fr-FR
drwxrwxrwx 1 root root      0 2008-03-18 18:34 hu-HU
drwxrwxrwx 1 root root      0 2008-03-18 18:34 it-IT
drwxrwxrwx 1 root root      0 2008-03-18 18:34 ja-JP
drwxrwxrwx 1 root root      0 2008-03-18 18:34 ko-KR
-rwxrwxrwx 1 root root 406584 2008-01-19 07:43 memtest.exe
drwxrwxrwx 1 root root      0 2008-03-18 18:34 nb-NO
drwxrwxrwx 1 root root      0 2008-03-18 18:34 nl-NL
drwxrwxrwx 1 root root      0 2008-03-18 18:34 pl-PL
drwxrwxrwx 1 root root      0 2008-03-18 18:34 pt-BR
drwxrwxrwx 1 root root      0 2008-03-18 18:34 pt-PT
drwxrwxrwx 1 root root      0 2008-03-18 18:34 ru-RU
drwxrwxrwx 1 root root      0 2008-03-18 18:34 sv-SE
drwxrwxrwx 1 root root      0 2008-03-18 18:34 tr-TR
drwxrwxrwx 1 root root      0 2008-03-18 18:34 zh-CN
drwxrwxrwx 1 root root      0 2008-03-18 18:34 zh-HK
drwxrwxrwx 1 root root      0 2008-03-18 18:34 zh-TW

sdb6/boot/grub/menu.lst

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
# kopt=root=UUID=d6d632ac-b44c-44dc-8587-d43bc2ce4f36 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=d6d632ac-b44c-44dc-8587-d43bc2ce4f36

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
uuid		d6d632ac-b44c-44dc-8587-d43bc2ce4f36
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=d6d632ac-b44c-44dc-8587-d43bc2ce4f36 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		d6d632ac-b44c-44dc-8587-d43bc2ce4f36
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=d6d632ac-b44c-44dc-8587-d43bc2ce4f36 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		d6d632ac-b44c-44dc-8587-d43bc2ce4f36
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


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows Vista/Longhorn (loader)
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


sdb6/etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb6
UUID=d6d632ac-b44c-44dc-8587-d43bc2ce4f36 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=920f3d86-a5a9-44c4-8240-dd3b011b3917 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

sdb6/boot

total 12816
drwxr-xr-x  3 root root    4096 2008-12-22 19:14 .
drwxr-xr-x 20 root root    4096 2008-12-22 19:14 ..
-rw-r--r--  1 root root  503560 2008-10-24 07:55 abi-2.6.27-7-generic
-rw-r--r--  1 root root   85316 2008-10-24 07:55 config-2.6.27-7-generic
drwxr-xr-x  2 root root    4096 2008-12-22 19:14 grub
-rw-r--r--  1 root root 8652340 2008-12-22 19:14 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root  124152 2008-09-11 20:11 memtest86+.bin
-rw-r--r--  1 root root 1352144 2008-10-24 07:55 System.map-2.6.27-7-generic
-rw-r--r--  1 root root    1130 2008-10-24 07:57 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root 2339712 2008-10-24 07:55 vmlinuz-2.6.27-7-generic

sdb6/boot/grub

total 216
drwxr-xr-x 2 root root   4096 2008-12-22 19:14 .
drwxr-xr-x 3 root root   4096 2008-12-22 19:14 ..
-rw-r--r-- 1 root root    197 2008-12-22 19:14 default
-rw-r--r-- 1 root root     30 2008-12-22 19:14 device.map
-rw-r--r-- 1 root root   8108 2008-12-22 19:14 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2008-12-22 19:14 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-12-22 19:14 installed-version
-rw-r--r-- 1 root root   8712 2008-12-22 19:14 jfs_stage1_5
-rw-r--r-- 1 root root   4839 2008-12-22 19:14 menu.lst
-rw-r--r-- 1 root root   7352 2008-12-22 19:14 minix_stage1_5
-rw-r--r-- 1 root root   9756 2008-12-22 19:14 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-12-22 19:14 stage1
-rw-r--r-- 1 root root 121460 2008-12-22 19:14 stage2
-rw-r--r-- 1 root root   9556 2008-12-22 19:14 xfs_stage1_5

StdErr Messages 

Unknown MBR on /dev/sdc


Unknown MBR on /dev/sdd


hexdump: /dev/sdc: No medium found
hexdump: /dev/sdc: No medium found
hexdump: /dev/sdd: No medium found
hexdump: /dev/sdd: No medium found[/PHP]





I'm curious why I have sdb1, sdb2, and then sdb5, and sdb6... where are the intermediates? 

I know I'm beyond my skill level here - hopefully you can help me out?

---

### Post by maybeway36 on 2008-12-22
sdb5 and above are actually logical partitions inside sdb2.

---

### Post by greenman1313 on 2008-12-22
Oh, well that makes sense then. I was thinking I had some "missing" partitions hiding out on the hard drive or something.

:)

---

### Post by caljohnsmith on 2008-12-22
OK, thanks, that helps clarify your setup quite a bit. Can you set your BIOS to boot the sdb drive on start up? If so, that would be ideal, and then you can install Grub to its MBR to make it bootable by doing:
```
sudo grub
grub> root (hd1,0)
grub> makeactive
grub> root (hd1,5)
grub> setup (hd1)
grub> quit
```
Next you'll need to repair your Vista sdb1 boot sector, so how about booting your Vista Install CD, go to the command line and do:
```
diskpart
```
And at the diskpart prompt do:
```
list volume
exit
```
And find the drive letter for your Vista install, for example "D", and then do:
```
[COLOR="Blue"]E:[/COLOR]\boot\bootsect.exe /nt60 [COLOR="Blue"]D:[/COLOR]
```
So replace "D" above if the Vista drive letter is different, and the E: should be the drive letter of your Vista CD, so replace that if it is different too. After that reboot, set your BIOS to boot the sdb drive, and you should get the Grub menu on start up. Let me know exactly what happens about booting the OSes in your Grub menu. Also, the XP and Vista Grub menu entries will actually be the opposite of what they say; when you choose to boot XP, you will actually be trying to boot Vista, and when you choose Vista to boot, you will be booting XP. We can fix your menu.lst after you boot into Ubuntu, but try the above steps and let me know how far you get. :)

---

### Post by greenman1313 on 2008-12-22
One question (and maybe it's just me being crazy): I can't find/access the command line using the Vista install CD. When it boots up, I have no options that give me command line capabilities, as far as I can tell. Do you know where exactly to find it?

:confused:


Also, I can access BIOS and change the boot order to the sdb drive if needed. Should I do that FIRST? And then follow your list? 



I apologize for my naivete; I'm so new to this stuff.

---

### Post by caljohnsmith on 2008-12-22
Is your Vista Install CD an OEM CD from your computer manufacturer, or do you have a genuine Vista Install CD from Microsoft? If it is OEM, that would be the issue. You could instead download a Vista Recovery CD from [here]("http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/") and use that to run the commands. Also, it's OK to change the BIOS boot order at any time to boot the sdb drive, but just keep in mind that until you run the Grub commands from my previous post, you won't be able to boot the sdb drive.

---

### Post by greenman1313 on 2008-12-22
I have an OEM Vista install disc, but I just burned a copy of the Vista recovery disc. I booted into it, and voila - I have command line access!



I used the 'diskpart' and 'list volume' commands, and found that the Vista disk is assigned to letter "D", and the Vista install CD is assigned to letter "F".

I tried entering "F: \boot\bootsect.exe /nt60 D:" into the same command line window (in the Vista repair disc's command line), and it said "'F: \boot\bootsect.exe' is not recognized as an internal or external command, operable program or batch file."

Am I entering in the command in the wrong area? Should I enter it into the Terminal in the Ubuntu Live Disc or something?

---

### Post by caljohnsmith on 2008-12-22
That's interesting, I thought that Vista Recovery CD would have that bootsect.exe command, but I must be wrong. When you get the command line from that CD, how about doing:
```
cd F:\
dir
```
And see if it lists the "boot" directory, and if so, do:
```
cd boot
dir
```
And see if it has any program that remotely resembles the bootsect.exe program (look at all the programs that begin with "b"). If it doesn't, how about running instead:
```
bootrec /fixboot
```
And let me know the output. Then reboot, and try booting XP and Vista from the Grub menu.

---

### Post by greenman1313 on 2008-12-22
OK, I'll go take a look right now. In the meantime, take a look at this: [http://thevistaforums.com/index.php?showtopic=5646&mode=threaded&pid=53984]("http://thevistaforums.com/index.php?showtopic=5646&mode=threaded&pid=53984")

*Not sure if linking to outside is OK, if not, I will edit & remove*


Do you think any of that could pertain to this situation?


-- I'll let you know what I find out when I run those commands you gave me in just a few minutes.
:)

---

### Post by greenman1313 on 2008-12-22
When I enter
[PHP]cd F:\
dir[/PHP]
it gives me:

"Volume in drive X is Boot 
Directory of X: \ Sources
...and then a bunch of files..." 

Nothing that says "boot" except for "Volume in drive X is Boot"

When I tried 
[PHP]cd boot
dir[/PHP]
it said "The system cannot find the path specified" when I typed 'cd boot'. When I type 'dir', it gives me the same directory info as when I did it before.


I have NOT tried this yet:
[PHP]bootrec /fixboot[/PHP]
Should I try that now?

---

### Post by caljohnsmith on 2008-12-22
Yes, please try the "bootrec /fixboot" command, and let me know the output. :)

---

### Post by greenman1313 on 2008-12-22
When I ran "bootrec /fixboot", it said 'operation completed successfully'. 

When I rebooted, it went to Grub, of course, but I got Error 18 when I tried to boot any OS.


I just booted into Ubuntu Live disc, and here's "sudo fdisk -lu":
[PHP]Disk /dev/sda: 320.0 GB, 320072933376 bytes
154 heads, 29 sectors/track, 139978 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x83d67900

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          29   625137281   312568626+   7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd985e7a2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   502257342   251128640    7  HPFS/NTFS
/dev/sdb2       502272225   625137344    61432560    5  Extended
/dev/sdb5       502272288   504987209     1357461   82  Linux swap / Solaris
/dev/sdb6       505180053   625137344    59978646   83  Linux
[/PHP]




And here's the result of the "boot_info_results.txt":
[PHP]/dev/sdc has no valid partition table.
/dev/sdd has no valid partition table.
Grub is installed in the MBR of /dev/sda and looks on boot drive #2 in partition #6 for its boot files.
Grub is installed in the MBR of /dev/sdb and looks on the same drive in partition #6 for its boot files.

sda1:
    File system:  ntfs
    Boot sector  type:  Vista
    Boot sector  info:  According to the info in the boot sector, sda1 starts at sector 29.
    Operating System: XP
    Boot files/directories present:  /boot.ini /ntldr /NTDETECT.COM /Boot

sdb1:
    File system:  ntfs
    Boot sector  type:  XP
    Boot sector  info:  According to the info in the boot sector, sdb1 starts at sector 63.
    Operating System: Vista
    Boot files/directories present:  /bootmgr /Boot

sdb2:
    File system:  Extended Partition

sdb5:
    File system:  swap

sdb6:
    File system:  ext3
    Boot sector  type:  No Boot Loader
    Boot sector  info:  
    Operating System: Ubuntu 8.10 \n \l
    Boot files/directories present:  /boot/grub/menu.lst /etc/fstab /boot /boot/grub


Disk /dev/sda: 320.0 GB, 320072933376 bytes
154 heads, 29 sectors/track, 139978 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x83d67900

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          29   625137281   312568626+   7  HPFS/NTFS

Warning: partition 1 does not end at a cylinder boundary


Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd985e7a2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   502257342   251128640    7  HPFS/NTFS
/dev/sdb2       502272225   625137344    61432560    5  Extended
/dev/sdb5       502272288   504987209     1357461   82  Linux swap / Solaris
/dev/sdb6       505180053   625137344    59978646   83  Linux

Warning: partition 1 does not end at a cylinder boundary
Warning: partition 1 does not end at a cylinder boundary

/dev/sda1: UUID="CAD0DDA5D0DD97D1" TYPE="ntfs" 
/dev/sdb1: UUID="4410EAE810EADFC2" LABEL="Vista Disk" TYPE="ntfs" 
/dev/sdb5: UUID="920f3d86-a5a9-44c4-8240-dd3b011b3917" TYPE="swap" 
/dev/sdb6: UUID="d6d632ac-b44c-44dc-8587-d43bc2ce4f36" SEC_TYPE="ext2" TYPE="ext3" 
/dev/loop0: TYPE="squashfs" 

sda1/boot.ini

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


sda1/Boot

total 32
drwxrwxrwx 1 root root     0 2008-12-22 19:43 .
drwxrwxrwx 1 root root  8192 2008-12-22 19:43 ..
-rwxrwxrwx 1 root root 12288 2008-12-22 23:38 BCD
-rwxrwxrwx 1 root root  9216 2008-12-22 23:38 BCD.LOG

sdb1/Boot

total 540
drwxrwxrwx 1 root root   4096 2008-03-18 18:34 .
drwxrwxrwx 1 root root  24576 2008-12-22 18:34 ..
-rwxrwxrwx 1 root root  24576 2008-12-14 18:10 BCD
-rwxrwxrwx 1 root root  21504 2008-12-14 17:42 BCD.LOG
-rwxrwxrwx 1 root root      0 2008-03-05 02:56 BCD.LOG1
-rwxrwxrwx 1 root root      0 2008-03-05 02:56 BCD.LOG2
-rwxrwxrwx 1 root root  65536 2008-03-05 02:56 bootstat.dat
drwxrwxrwx 1 root root      0 2008-03-18 18:34 cs-CZ
drwxrwxrwx 1 root root      0 2008-03-18 18:34 da-DK
drwxrwxrwx 1 root root      0 2008-03-18 18:34 de-DE
drwxrwxrwx 1 root root      0 2008-03-18 18:34 el-GR
drwxrwxrwx 1 root root      0 2008-03-18 18:34 en-US
drwxrwxrwx 1 root root      0 2008-03-18 18:34 es-ES
drwxrwxrwx 1 root root      0 2008-03-18 18:34 fi-FI
drwxrwxrwx 1 root root      0 2008-03-18 18:34 Fonts
drwxrwxrwx 1 root root      0 2008-03-18 18:34 fr-FR
drwxrwxrwx 1 root root      0 2008-03-18 18:34 hu-HU
drwxrwxrwx 1 root root      0 2008-03-18 18:34 it-IT
drwxrwxrwx 1 root root      0 2008-03-18 18:34 ja-JP
drwxrwxrwx 1 root root      0 2008-03-18 18:34 ko-KR
-rwxrwxrwx 1 root root 406584 2008-01-19 07:43 memtest.exe
drwxrwxrwx 1 root root      0 2008-03-18 18:34 nb-NO
drwxrwxrwx 1 root root      0 2008-03-18 18:34 nl-NL
drwxrwxrwx 1 root root      0 2008-03-18 18:34 pl-PL
drwxrwxrwx 1 root root      0 2008-03-18 18:34 pt-BR
drwxrwxrwx 1 root root      0 2008-03-18 18:34 pt-PT
drwxrwxrwx 1 root root      0 2008-03-18 18:34 ru-RU
drwxrwxrwx 1 root root      0 2008-03-18 18:34 sv-SE
drwxrwxrwx 1 root root      0 2008-03-18 18:34 tr-TR
drwxrwxrwx 1 root root      0 2008-03-18 18:34 zh-CN
drwxrwxrwx 1 root root      0 2008-03-18 18:34 zh-HK
drwxrwxrwx 1 root root      0 2008-03-18 18:34 zh-TW

sdb6/boot/grub/menu.lst

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
# kopt=root=UUID=d6d632ac-b44c-44dc-8587-d43bc2ce4f36 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=d6d632ac-b44c-44dc-8587-d43bc2ce4f36

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
uuid		d6d632ac-b44c-44dc-8587-d43bc2ce4f36
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=d6d632ac-b44c-44dc-8587-d43bc2ce4f36 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		d6d632ac-b44c-44dc-8587-d43bc2ce4f36
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=d6d632ac-b44c-44dc-8587-d43bc2ce4f36 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		d6d632ac-b44c-44dc-8587-d43bc2ce4f36
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


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows Vista/Longhorn (loader)
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


sdb6/etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb6
UUID=d6d632ac-b44c-44dc-8587-d43bc2ce4f36 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=920f3d86-a5a9-44c4-8240-dd3b011b3917 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

sdb6/boot

total 12816
drwxr-xr-x  3 root root    4096 2008-12-22 19:14 .
drwxr-xr-x 20 root root    4096 2008-12-22 19:14 ..
-rw-r--r--  1 root root  503560 2008-10-24 07:55 abi-2.6.27-7-generic
-rw-r--r--  1 root root   85316 2008-10-24 07:55 config-2.6.27-7-generic
drwxr-xr-x  2 root root    4096 2008-12-22 19:14 grub
-rw-r--r--  1 root root 8652340 2008-12-22 19:14 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root  124152 2008-09-11 20:11 memtest86+.bin
-rw-r--r--  1 root root 1352144 2008-10-24 07:55 System.map-2.6.27-7-generic
-rw-r--r--  1 root root    1130 2008-10-24 07:57 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root 2339712 2008-10-24 07:55 vmlinuz-2.6.27-7-generic

sdb6/boot/grub

total 216
drwxr-xr-x 2 root root   4096 2008-12-22 19:14 .
drwxr-xr-x 3 root root   4096 2008-12-22 19:14 ..
-rw-r--r-- 1 root root    197 2008-12-22 19:14 default
-rw-r--r-- 1 root root     30 2008-12-22 19:14 device.map
-rw-r--r-- 1 root root   8108 2008-12-22 19:14 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2008-12-22 19:14 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-12-22 19:14 installed-version
-rw-r--r-- 1 root root   8712 2008-12-22 19:14 jfs_stage1_5
-rw-r--r-- 1 root root   4839 2008-12-22 19:14 menu.lst
-rw-r--r-- 1 root root   7352 2008-12-22 19:14 minix_stage1_5
-rw-r--r-- 1 root root   9756 2008-12-22 19:14 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-12-22 19:14 stage1
-rw-r--r-- 1 root root 121460 2008-12-22 19:14 stage2
-rw-r--r-- 1 root root   9556 2008-12-22 19:14 xfs_stage1_5

StdErr Messages 

/dev/sdc: No medium found

sfdisk: cannot open /dev/sdc for reading
/dev/sdd: No medium found

sfdisk: cannot open /dev/sdd for reading[/PHP]




Did I screw something up? :confused:

---

### Post by caljohnsmith on 2008-12-22
I see that unfortunately the "bootrec /fixboot" fixed the boot sector of the wrong partition, namely your sda1 Windows XP partition. I was afraid that might happen, but since the Vista CD didn't have the bootsect.exe command, we had to take our chances with the "bootrec /fixboot" command. I was curious to know for sure whether the Vista Recovery CD you downloaded had the bootsect.exe command or not, so I downloaded that CD and you're definitely right, that Recovery CD doesn't have the bootsect.exe command that I could find. But the Grub error 18 is going to complicate things; did you get the Grub error 18 even when trying to boot Ubuntu from the Grub menu? How about posting the output of the following commands:
```
sudo grub
grub> root (hd1,5)
grub> blocklist /boot/grub/menu.lst
grub> blocklist /boot/grub/stage2
grub> blocklist /boot/vmlinuz-2.6.27-7-generic
grub> blocklist /boot/initrd.img-2.6.27-7-generic 
grub> quit
```

---

### Post by greenman1313 on 2008-12-22
First off, I'd like to say that you've been a HUGE help - you can imagine that I have no idea what I'm doing with all of this stuff... I really appreciate it! :)


Well, I was getting Error 18 no matter what I tried to load, even Ubuntu from the Grub menu. The very first error I got was Error 29 (when I tried to open Vista/Longhorn), but after that, it was all Error 18, even when I tried to boot into Vista?longhorn again.


Here are the results of what you asked me to run:
[PHP]Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> root (hd1,5)
root (hd1,5)
grub> blocklist /boot/grub/menu.lst
blocklist /boot/grub/menu.lst
(hd1,5)29261824+10
grub> blocklist /boot/grub/stage2
blocklist /boot/grub/stage2
(hd1,5)29139432+96,29139536+142
grub> blocklist /boot/vmlinuz-2.6.27-7-generic
blocklist /boot/vmlinuz-2.6.27-7-generic
(hd1,5)29134848+96,29134952+4474
grub> blocklist /boot/initrd.img-2.6.27-7-generic
blocklist /boot/initrd.img-2.6.27-7-generic
(hd1,5)29196288[10-512],29196289+15,29196304[0-10],29196304[10-512],29196305+15,29196320[0-10],29196320[10-512],29196321+15,29196336[0-10],29196336[10-512],29196337+15,29196352[0-10],29196352[10-512],29196353+15,29196368[0-10],29196368[10-512],29196369+15,29196392[0-10],29196392[10-512],29196393+15,29196408[0-10],29196408[10-512],29196409+15,29196424[0-10],29196424[10-512],29196425+15,29196440[0-10],29196440[10-512],29196441+15,29196456[0-10],29196456[10-512],29196457+15,29196472[0-10],29196472[10-512],29196473+15,29196488[0-10],29196488[10-512],29196489+15,29196504[0-10],29196504[10-512],29196505+15,29196520[0-10],29196520[10-512],29196521+15,29196536[0-10],29196536[10-512],29196537+15,29196552[0-10],29196552[10-512],29196553+15,29196568[0-10],29196568[10-512],29196569+15,29196584[0-10],29196584[10-512],29196585+15,29196600[0-10],29196600[10-512],29196601+15,29196616[0-10],29196616[10-512],29196617+15,29196632[0-10],29196632[10-512],29196633+15,29196648[0-10],29196648[10-512],29196649+15,29196664[0-10],29196664[10-512],29196665+15,29196680[0-10],29196680[10-512],29196681+15,29196696[0-10],29196696[10-512],29196697+15,29196712[0-10],29196712[10-512],29196713+15,29196728[0-10],29196728[10-512],29196729+15,29196744[0-10],29196744[10-512],29196745+15,29196760[0-10],29196760[10-512],29196761+15,29196776[0-10],29196776[10-512],29196777+15,29196792[0-10],29196792[10-512],29196793+15,29196808[0-10],29196808[10-512],29196809+15,29196824[0-10],29196824[10-512],29196825+15,29196840[0-10],29196840[10-512],29196841+15,29196856[0-10],29196856[10-512],29196857+15,29196872[0-10],29196872[10-512],29196873+15,29196888[0-10],29196888[10-512],29196889+15,29196904[0-10],29196904[10-512],29196905+15,29196920[0-10],29196920[10-512],29196921+15,29196936[0-10],29196936[10-512],29196937+15,29196952[0-10],29196952[10-512],29196953+15,29196968[0-10],29196968[10-512],29196969+15,29196984[0-10],29196984[10-512],29196985+15,29197000[0-10],29197000[10-512],29197001+15,29197016[0-10],29197016[10-512],29197017+15,29197032[0-10],29197032[10-512],29197033+15,29197048[0-10],29197048[10-512],29197049+15,29197064[0-10],29197064[10-512],29197065+15,29197080[0-10],29197080[10-512],29197081+15,29197096[0-10],29197096[10-512],29197097+15,29197112[0-10],29197112[10-512],29197113+15,29197128[0-10],29197128[10-512],29197129+15,29197144[0-10],29197144[10-512],29197145+15,29197160[0-10],29197160[10-512],29197161+15,29197176[0-10],29197176[10-512],29197177+15,29197192[0-10],29197192[10-512],29197193+15,29197208[0-10],29197208[10-512],29197209+15,29197224[0-10],29197224[10-512],29197225+15,29197240[0-10],29197240[10-512],29197241+15,29197256[0-10],29197256[10-512],29197257+15,29197272[0-10],29197272[10-512],29197273+15,29197288[0-10],29197288[10-512],29197289+15,29197304[0-10],29197304[10-512],29197305+15,29197320[0-10],29197320[10-512],29197321+15,29197336[0-10],29197336[10-512],29197337+15,29197352[0-10],29197352[10-512],29197353+15,29197368[0-10],29197368[10-512],29197369+15,29197384[0-10],29197384[10-512],29197385+15,29197400[0-10],29197400[10-512],29197401+15,29197416[0-10],29197416[10-512],29197417+15,29197432[0-10],29197432[10-512],29197433+15,29197448[0-10],29197448[10-512],29197449+15,29197464[0-10],29197464[10-512],29197465+15,29197480[0-10],29197480[10-512],29197481+15,29197496[0-10],29197496[10-512],29197497+15,29197512[0-10],29197512[10-512],29197513+15,29197528[0-10],29197528[10-512],29197529+15,29197544[0-10],29197544[10-512],29197545+15,29197560[0-10],29197560[10-512],29197561+15,29197576[0-10],29197576[10-512],29197577+15,29197592[0-10],29197592[10-512],29197593+15,29197608[0-10],29197608[10-512],29197609+15,29197624[0-10],29197624[10-512],29197625+15,29197640[0-10],29197640[10-512],29197641+15,29197656[0-10],29197656[10-512],29197657+15,29197672[0-10],29197672[10-512],29197673+15,29197688[0-10],29197688[10-512],29197689+15,29197704[0-10],29197704[10-512],29197705+15,29197720[0-10],29197720[10-512],29197721+15,29197736[0-10],29197736[10-512],29197737+15,29197752[0-10],29197752[10-512],29197753+15,29197768[0-10],29197768[10-512],29197769+15,29197784[0-1Segmentation fault (core dumped)
[/PHP]


On the last one, Ubuntu said something crashed, and I just checked and it said "Sorry, the program "Grub" has closed unexpectedly". 


Hmmmm... the plot thickens.

---

### Post by caljohnsmith on 2008-12-22
> **greenman1313 said:**
> First off, I'd like to say that you've been a HUGE help - you can imagine that I have no idea what I'm doing with all of this stuff... I really appreciate it! :)

You're welcome, and I hope we can get your setup booting OK. :) But you're unfortunately right, the plot has thickened; all your boot files, including the Grub stage2 and menu.lst files are physically located at about 273 GB from the beginning of your drive. The reason why that matters is because a Grub error 18 is:
> **Official Grub Manual]**Error 18**: Selected cylinder exceeds maximum supported by BIOS
This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB in general).[/QUOTE]
So you typically would get a Grub error 18 if your BIOS has the limitation where it can't access anything on the HDD past either 8.4 GB or 137 GB. But the strange thing in your situation is all of your boot files are outside of either of those ranges, and yet you are able to get the Grub menu on start up said:**
> **Error 29**: Disk write error
This error is returned if there is a disk write error when trying to write to a particular disk. This would generally only occur during an install of set active partition command.
So that's a really bad sign. I think at this point you should do a HDD diagnostic test on the sdb drive to check its health. So in order to do that, please do the following:
```
sudo apt-get install smartmontools
```
First do the following to save the current health status parameters of your HDD to a file on your desktop:
```
sudo smartctl -a /dev/sdb > ~/Desktop/sdb_health_before_test.txt
```
Then run:
```
sudo smartctl -t long /dev/sdb
```
That command will immediately terminate while the HDD begins its self-test, and it could take quite a while. You can monitor the progress with:
```
sudo smartctl -a /dev/sdb | grep -A 1 -i "self-test execution status"
```
Once the above command says the test is done, then do:
```
sudo smartctl -a /dev/sdb > ~/Desktop/sdb_health_after_test.txt
sudo smartctl -H /dev/sdb
```
And please post the contents of the two files on your desktop so I can see the results.

---

### Post by greenman1313 on 2008-12-22
It's done. 



Here's the results of the code that I entered into the Terminal; in case you want to see that: 
[PHP]ubuntu@ubuntu:~$ sudo apt-get install smartmontools
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  bsd-mailx exim4 exim4-base exim4-config exim4-daemon-light mailx
Suggested packages:
  eximon4 exim4-doc-html exim4-doc-info libmail-spf-query-perl swaks
The following NEW packages will be installed:
  bsd-mailx exim4 exim4-base exim4-config exim4-daemon-light mailx
  smartmontools
0 upgraded, 7 newly installed, 0 to remove and 0 not upgraded.
Need to get 2267kB of archives.
After this operation, 4977kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com intrepid/main exim4-config 4.69-5ubuntu2 [312kB]
Get:2 http://archive.ubuntu.com intrepid/main exim4-base 4.69-5ubuntu2 [987kB]
Get:3 http://archive.ubuntu.com intrepid/main exim4-daemon-light 4.69-5ubuntu2 [452kB]
Get:4 http://archive.ubuntu.com intrepid/main exim4 4.69-5ubuntu2 [6354B]
Get:5 http://archive.ubuntu.com intrepid/main bsd-mailx 8.1.2-0.20071201cvs-3 [166kB]
Get:6 http://archive.ubuntu.com intrepid/main mailx 1:20071201-3 [8296B]
Get:7 http://archive.ubuntu.com intrepid/main smartmontools 5.38-1ubuntu2 [336kB]
Fetched 2267kB in 3s (624kB/s)     
Preconfiguring packages ...
Selecting previously deselected package exim4-config.
(Reading database ... 100452 files and directories currently installed.)
Unpacking exim4-config (from .../exim4-config_4.69-5ubuntu2_all.deb) ...
Selecting previously deselected package exim4-base.
Unpacking exim4-base (from .../exim4-base_4.69-5ubuntu2_amd64.deb) ...
Selecting previously deselected package exim4-daemon-light.
Unpacking exim4-daemon-light (from .../exim4-daemon-light_4.69-5ubuntu2_amd64.deb) ...
Selecting previously deselected package exim4.
Unpacking exim4 (from .../exim4_4.69-5ubuntu2_all.deb) ...
Selecting previously deselected package bsd-mailx.
Unpacking bsd-mailx (from .../bsd-mailx_8.1.2-0.20071201cvs-3_amd64.deb) ...
Selecting previously deselected package mailx.
Unpacking mailx (from .../mailx_1%3a20071201-3_all.deb) ...
Selecting previously deselected package smartmontools.
Unpacking smartmontools (from .../smartmontools_5.38-1ubuntu2_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for doc-base ...
Processing 23 changed, 4 added doc-base file(s)...
Registering documents with scrollkeeper...
Setting up exim4-config (4.69-5ubuntu2) ...
Adding system-user for exim (v4)

Setting up exim4-base (4.69-5ubuntu2) ...

Setting up exim4-daemon-light (4.69-5ubuntu2) ...
 * Starting MTA                                                          [ OK ] 

Setting up exim4 (4.69-5ubuntu2) ...

Setting up bsd-mailx (8.1.2-0.20071201cvs-3) ...

Setting up mailx (1:20071201-3) ...
Setting up smartmontools (5.38-1ubuntu2) ...

ubuntu@ubuntu:~$ sudo smartctl -a /dev/sdb > ~/Desktop/sdb_health_before_test.txt
ubuntu@ubuntu:~$ sudo smartctl -t long /dev/sdb
smartctl version 5.38 [x86_64-unknown-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF OFFLINE IMMEDIATE AND SELF-TEST SECTION ===
Sending command: "Execute SMART Extended self-test routine immediately in off-line mode".
Drive command "Execute SMART Extended self-test routine immediately in off-line mode" successful.
Testing has begun.
Please wait 115 minutes for test to complete.
Test will complete after Mon Dec 22 21:07:57 2008

Use smartctl -X to abort test.
ubuntu@ubuntu:~$ sudo smartctl -a /dev/sdb | grep -A 1 -i "self-test execution status"
Self-test execution status:      ( 249)	Self-test routine in progress...
					90% of test remaining.
ubuntu@ubuntu:~$ sudo smartctl -a /dev/sdb | grep -A 1 -i "self-test execution status"
Self-test execution status:      ( 247)	Self-test routine in progress...
					70% of test remaining.
ubuntu@ubuntu:~$ sudo smartctl -a /dev/sdb | grep -A 1 -i "self-test execution status"
Self-test execution status:      ( 246)	Self-test routine in progress...
					60% of test remaining.
ubuntu@ubuntu:~$ sudo smartctl -a /dev/sdb | grep -A 1 -i "self-test execution status"
Self-test execution status:      ( 245)	Self-test routine in progress...
					50% of test remaining.
ubuntu@ubuntu:~$ sudo smartctl -a /dev/sdb | grep -A 1 -i "self-test execution status"
Self-test execution status:      ( 245)	Self-test routine in progress...
					50% of test remaining.
ubuntu@ubuntu:~$ sudo smartctl -a /dev/sdb | grep -A 1 -i "self-test execution status"
Self-test execution status:      ( 243)	Self-test routine in progress...
					30% of test remaining.
ubuntu@ubuntu:~$ sudo smartctl -a /dev/sdb | grep -A 1 -i "self-test execution status"
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
ubuntu@ubuntu:~$ sudo smartctl -a /dev/sdb > ~/Desktop/sdb_health_after_test.txtubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ sudo smartctl -H /dev/sdb
smartctl version 5.38 [x86_64-unknown-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED
[/PHP]






Here is the "pre" file:
[PHP]smartctl version 5.38 [x86_64-unknown-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Barracuda 7200.10 family
Device Model:     ST3320620AS
Serial Number:    6QF3HYFK
Firmware Version: 3.AAK
User Capacity:    320,072,933,376 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Mon Dec 22 19:12:25 2008 UTC
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82)	Offline data collection activity
					was completed without error.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		 ( 430) seconds.
Offline data collection
capabilities: 			 (0x5b) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					Offline surface scan supported.
					Self-test supported.
					No Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					General Purpose Logging supported.
Short self-test routine 
recommended polling time: 	 (   1) minutes.
Extended self-test routine
recommended polling time: 	 ( 115) minutes.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   107   085   006    Pre-fail  Always       -       201412919
  3 Spin_Up_Time            0x0003   096   095   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       980
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   086   060   030    Pre-fail  Always       -       444447758
  9 Power_On_Hours          0x0032   091   091   000    Old_age   Always       -       7923
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       66
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   077   066   045    Old_age   Always       -       23 (Lifetime Min/Max 22/25)
194 Temperature_Celsius     0x0022   023   040   000    Old_age   Always       -       23 (0 15 0 0)
195 Hardware_ECC_Recovered  0x001a   056   053   000    Old_age   Always       -       172949474
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0000   100   253   000    Old_age   Offline      -       0
202 TA_Increase_Count       0x0032   100   253   000    Old_age   Always       -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1

SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.[/PHP]






Here is the "after" file:
[PHP]smartctl version 5.38 [x86_64-unknown-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Barracuda 7200.10 family
Device Model:     ST3320620AS
Serial Number:    6QF3HYFK
Firmware Version: 3.AAK
User Capacity:    320,072,933,376 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Mon Dec 22 20:39:39 2008 UTC
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82)	Offline data collection activity
					was completed without error.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		 ( 430) seconds.
Offline data collection
capabilities: 			 (0x5b) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					Offline surface scan supported.
					Self-test supported.
					No Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					General Purpose Logging supported.
Short self-test routine 
recommended polling time: 	 (   1) minutes.
Extended self-test routine
recommended polling time: 	 ( 115) minutes.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   107   085   006    Pre-fail  Always       -       201412919
  3 Spin_Up_Time            0x0003   096   095   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       980
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   086   060   030    Pre-fail  Always       -       444962002
  9 Power_On_Hours          0x0032   091   091   000    Old_age   Always       -       7925
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       66
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   076   066   045    Old_age   Always       -       24 (Lifetime Min/Max 22/26)
194 Temperature_Celsius     0x0022   024   040   000    Old_age   Always       -       24 (0 15 0 0)
195 Hardware_ECC_Recovered  0x001a   060   053   000    Old_age   Always       -       45336405
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0000   100   253   000    Old_age   Offline      -       0
202 TA_Increase_Count       0x0032   100   253   000    Old_age   Always       -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%      7925         -

SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.[/PHP]




Boy there's alot of data in there!!

---

### Post by caljohnsmith on 2008-12-23
OK, that's great, it looks like your HDD is in good health. But the bad news is we still don't know then what is causing the inconsistent Grub errors. Can you first make sure that the HDD cable is secure and snug? I would reseat the HDD cable connection (pull it out and put it back in) just to make sure the connection is OK; I've seen strange Grub behavior in the forums before when that turned out to be the problem. Also, what are the HDD-related BIOS settings you have for that drive? If you can, please go into your BIOS and let me know what HDD-related settings you have like "auto-detect", LBA, CHS, RAID, AHCI/HCI/EHCI vs. IDE, IDE-emulation, ACPI, DMA, etc. Also, from post #9 you said:
[QUOTE=greenman1313]I finally installed Ubuntu - it gave me some trouble, as it was telling me that it couldn't install it for some reason, but I re-checked the disc, and it came back 100% fine. I finally got it to load and now I get error 18 from Grub, and I can't boot into any OS without first using GAG, and even then I can only boot into XP.[/QUOTE]
So what problems did you have installing Ubuntu, and what happened that you were finally able to install it? Also, when you boot the Ubuntu CD, have you tried doing the "check CD for defects" type option from the main menu? Is that the disk check you are referring to, or do you mean you checked the Ubuntu ISO md5sum?

---

### Post by meierfra. on 2008-12-23
> we still don't know then what is causing the inconsistent Grub errors. 

Couple of possibilities:

Grub Error 29 can be caused by "savedefault"  (If "savedefault" is used, grub tries to write  the partition number for the OS, which is currently booted, into the file /boot/grub/default, if this fails grub reports error 29.) So removing "savedefault" from the Vista  item in menu.lst should cure this problem.


Grub Error 18 can be influenced by "logical partition" versus "primary partition" (I personally have not seen such a case, but hermanzone grub page mentions this) Before you reinstalled, Ubuntu was on a primary partition, now it is on a logical partitions. So you might convert Ubuntu back to a primary partition.
But before you try that, follow caljohnsmith's advice and check on your bios settings.

---

### Post by greenman1313 on 2008-12-23
BASIC HARDWARE SPECS --

- e8400 pcu
- Zalman CNPS9700 NT cpu fan
- 4GB (2x2) OCZ Reaper ram
- Asus Maximus Formula Mobo - 0907 BIOS
- Corsair TX750W Powersupply
- (Two) 320 GB Seagate Barricuda  hard drives

All connections to hard drives and mobo are secure.





HARD DRIVE SPECS --

** all specs are EXACTLY the same for SATA disk 1 & SATA disk 2 **


Info as presented in BIOS (all data is exactly the same for SATA 1 & SATA 2):

STAS3320620AS
LBA: supported
Block Mode: 16 Sectors
PIO Mode: 4
Async DMA: Multiword DMA-2
Ultra DMA: Ultra DMA-5
SMART Monitoring: supported
-----------------------------
Type: Auto
LBA/Large Mode: Auto
Block (Multi-Sector Transfer): Auto
PIO Mode: Auto
DMA Mode: Auto
SMART Monitoring: Auto
32 Bit data transfer: Enabled
------------------------------
------------------------------
SATA Conifguration-
     SATA Conifiguration: Enhanced
           Configure SATA as: IDE
     Hard Disk Write Protect: Enabled




PROBLEMS LOADING UBUNTU --

 - The very first time I installed Ubuntu (a few days ago) I had to install it manually. It worked fine. Then (after I reinstalled Vista 64 - which is on the same HD as Ubuntu) the other day, I reformatted the HD, and thus, had to reinstall Ubuntu. When I tried to install it, I also had to do it manually as before, and I used the same basic methodology as before (build a small swap file and then a large ext3 partition for Ubuntu). When the built in partition program tried to format, it gave me some sort of error, which I cannot remember. I checked the Ubuntu disc, and it says it's fine. I tried to load Ubuntu again, and got some error when Ubuntu was trying to install - again, not sure of what the error was, but it wasn't during the partitioning process... I think it was when the process was 30ish percent completed. I again rebooted the computer, and started over, using manual install again, and it stated the install was successful. When I tried to reboot into Ubuntu, however, I then encountered the Grub errors.

Is it possible that the manual install process somehow threw a spanner in the works by placing the MBR of one or more OSes into the wrong spot? I read something about this in my internet searches (which I've been doing A LOT of lately, regarding this issue).



Is that all the info that you needed?


Also, do you think it would be best to just start from scratch and reload all three OSes, or is there still a reasonable chance of being able to get this thing fixed?

I admit, if nothing else, this is a good learning experience.  :)

---

### Post by caljohnsmith on 2008-12-23
> **greenman1313]Is it possible that the manual install process somehow threw a spanner in the works by placing the MBR of one or more OSes into the wrong spot? I read something about this in my internet searches (which I've been doing A LOT of lately, regarding this issue).
[/QUOTE]
Fortunately meierfra's script that you ran will show just about everything you need to know to diagnose boot loader problems, so if a boot loader gets put in the wrong spot, you can usually easily figure it out with the help of that script. 
[QUOTE=greenman1313 said:**
> 
Also, do you think it would be best to just start from scratch and reload all three OSes, or is there still a reasonable chance of being able to get this thing fixed?

I admit, if nothing else, this is a good learning experience.  :)
I guess it's really a matter of how much you would like to experiment to try and get your present setup to to work, because I agree with you, I think it might be a great opportunity for us all to learn something new in the process. :) I'm really interested to know what might be causing the Grub error 18 in your case, so if you want to continue to do some more experiments to get it working, I'm all for it. My vote is that we convert your Ubuntu logical partition into a primary partition and see if that actually makes a difference, considering that you did have Ubuntu on a primary partition before and it worked, and also because neither meierfra nor I have seen any cases where it makes a difference; yet Herman claims it does. So if you are game, how about posting the output of:
```
sudo sfdisk -d /dev/sdb
```
And we can work from there. :)

---

### Post by greenman1313 on 2008-12-23
I'm always game to learn something new. Besides, it's just my luck to have novel "experiences" - I could tell you a few times about how I've broken the mold... but that's for another time. Let's see what we can do! :)



Here are the results:
[PHP]# partition table of /dev/sdb
unit: sectors

/dev/sdb1 : start=       63, size=502257280, Id= 7, bootable
/dev/sdb2 : start=502272225, size=122865120, Id= 5
/dev/sdb3 : start=        0, size=        0, Id= 0
/dev/sdb4 : start=        0, size=        0, Id= 0
/dev/sdb5 : start=502272288, size=  2714922, Id=82
/dev/sdb6 : start=505180053, size=119957292, Id=83
[/PHP]

---

### Post by caljohnsmith on 2008-12-23
OK, how about downloading the attached "partition_table.txt" to your desktop, and then do:
```
sudo sfdisk --force /dev/sdb < ~/Desktop/partition_table.txt
```
That will produce a lot of output which you can ignore. Next try the following:
```
sudo grub
grub> root (hd1,2)
grub> setup (hd1)
grub> quit
```
If you get any errors with the above Grub commands, then instead boot your Live CD and run the commands from there. After that, reboot, make sure your BIOS is set to boot the sdb drive, and let me know what happens. Also, after rebooting, if you aren't able to boot into Ubuntu, please boot your Live CD again and post the output of:
```
sudo fdisk -lu
```
And we can work from there. :)

---

### Post by greenman1313 on 2008-12-23
I am already booting from the Live CD, as I cannot boot into an OS via Grub. (Although, I do believe I can boot into XP using GAG).
I downloaded the .txt file, and ran your scripts, here's the result:
[PHP]To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo sfdisk --force /dev/sdb < ~/Desktop/partition_table.txt
Checking that no-one is using this disk right now ...
BLKRRPART: Device or resource busy

This disk is currently in use - repartitioning is probably a bad idea.
Umount all file systems, and swapoff all swap partitions on this disk.
Use the --no-reread flag to suppress this check.

Disk /dev/sdb: 38913 cylinders, 255 heads, 63 sectors/track
Old situation:
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sdb1   *      0+  31264-  31265- 251128640    7  HPFS/NTFS
/dev/sdb2      31265   38912    7648   61432560    5  Extended
/dev/sdb3          0       -       0          0    0  Empty
/dev/sdb4          0       -       0          0    0  Empty
/dev/sdb5      31265+  31433     169-   1357461   82  Linux swap / Solaris
/dev/sdb6      31446+  38912    7467-  59978646   83  Linux

sfdisk: input error: unexpected character   after Id field
ubuntu@ubuntu:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> root (hd1,2)
root (hd1,2)

Error 22: No such partition
grub> 
[/PHP]

I wasn't sure if I could (or should) go any farther?

---

### Post by caljohnsmith on 2008-12-23
[QUOTE=greenman1313]sfdisk: input error: unexpected character   after Id field [/QUOTE]
From the above error, it looks like there was something wrong in the partition_table.txt file, but I can't figure out what it is after re-examining it; so maybe meierfra will jump in and correct me again. But in the meantime, how about instead copy and paste the following into your text editor:
```
# partition table of /dev/sdb
unit: sectors

/dev/sdb1 : start=       63, size=502257280, Id= 7, bootable
/dev/sdb2 : start=502272225, size=  2714985, Id= 5
/dev/sdb3 : start=505180053, size=119957292, Id=83  
/dev/sdb4 : start=        0, size=        0, Id= 0
/dev/sdb5 : start=502272288, size=  2714922, Id=82

```
Then save it to your Ubuntu desktop as "partition_table.txt", and again run:
```
sudo sfdisk --force /dev/sdb < ~/Desktop/partition_table.txt 
```
And please post the output. If that produces the same error as before, then I'm obviously missing something.

EDIT: Also please do the following:
```
sudo dd if=/dev/sda1 count=20 | gzip -c > ~/Desktop/sda1.gz
sudo dd if=/dev/sdb1 count=20 | gzip -c > ~/Desktop/sdb1.gz
```
That will create "sda1.gz" and "sdb1.gz" on your desktop. Please attach those two small files to your next post.

---

### Post by greenman1313 on 2008-12-23
Here are the results:
[PHP]ubuntu@ubuntu:~$ sudo sfdisk --force /dev/sdb < ~/Desktop/partition_table.txt
Checking that no-one is using this disk right now ...
BLKRRPART: Device or resource busy

This disk is currently in use - repartitioning is probably a bad idea.
Umount all file systems, and swapoff all swap partitions on this disk.
Use the --no-reread flag to suppress this check.

Disk /dev/sdb: 38913 cylinders, 255 heads, 63 sectors/track
Old situation:
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sdb1   *      0+  31264-  31265- 251128640    7  HPFS/NTFS
/dev/sdb2      31265   38912    7648   61432560    5  Extended
/dev/sdb3          0       -       0          0    0  Empty
/dev/sdb4          0       -       0          0    0  Empty
/dev/sdb5      31265+  31433     169-   1357461   82  Linux swap / Solaris
/dev/sdb6      31446+  38912    7467-  59978646   83  Linux

sfdisk: input error: unexpected character   after Id field
ubuntu@ubuntu:~$ sudo dd if=/dev/sda1 count=20 | gzip -c > ~/Desktop/sda1.gz
20+0 records in
20+0 records out
10240 bytes (10 kB) copied, 0.0080116 s, 1.3 MB/s
ubuntu@ubuntu:~$ sudo dd if=/dev/sdb1 count=20 | gzip -c > ~/Desktop/sdb1.gz
20+0 records in
20+0 records out
10240 bytes (10 kB) copied, 0.0244547 s, 419 kB/s
[/PHP]



I have also attached the files.

---

### Post by caljohnsmith on 2008-12-23
OK, same error again I see, so I'm obviously missing something. How about as a quick sanity check, please post:
```
cat -A ~/Desktop/partition_table.txt
```
And don't be alarmed by the funny characters at the end of the lines, using the "-A" flag with cat will show the line ending types.

---

### Post by greenman1313 on 2008-12-23
Here you go: 
[PHP]# partition table of /dev/sdb$
unit: sectors$
$
/dev/sdb1 : start=       63, size=502257280, Id= 7, bootable$
/dev/sdb2 : start=502272225, size=  2714985, Id= 5$
/dev/sdb3 : start=505180053, size=119957292, Id=83  $
/dev/sdb4 : start=        0, size=        0, Id= 0$
/dev/sdb5 : start=502272288, size=  2714922, Id=82$
[/PHP]




I think my computer is possesed. Have you ever seen a problem like this before?  :-k

---

### Post by caljohnsmith on 2008-12-23
OK, for some reason sda3 has extra spaces after the file system ID number, so that might be the problem. I've corrected it and attached a new partition_table.txt file; please download it again to your desktop, do the same sfdisk command, and post the results.

---

### Post by greenman1313 on 2008-12-23
The results:
[PHP]ubuntu@ubuntu:~$ sudo sfdisk --force /dev/sdb < ~/Desktop/partition_table.txt 
Checking that no-one is using this disk right now ...
BLKRRPART: Device or resource busy

This disk is currently in use - repartitioning is probably a bad idea.
Umount all file systems, and swapoff all swap partitions on this disk.
Use the --no-reread flag to suppress this check.

Disk /dev/sdb: 38913 cylinders, 255 heads, 63 sectors/track
Old situation:
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sdb1   *      0+  31264-  31265- 251128640    7  HPFS/NTFS
/dev/sdb2      31265   38912    7648   61432560    5  Extended
/dev/sdb3          0       -       0          0    0  Empty
/dev/sdb4          0       -       0          0    0  Empty
/dev/sdb5      31265+  31433     169-   1357461   82  Linux swap / Solaris
/dev/sdb6      31446+  38912    7467-  59978646   83  Linux
New situation:
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sdb1   *        63 502257342  502257280   7  HPFS/NTFS
/dev/sdb2     502272225 504987209    2714985   5  Extended
/dev/sdb3     505180053 625137344  119957292  83  Linux
/dev/sdb4             0         -          0   0  Empty
/dev/sdb5     502272288 504987209    2714922  82  Linux swap / Solaris
Warning: partition 1 does not end at a cylinder boundary
Successfully wrote the new partition table

Re-reading the partition table ...
BLKRRPART: Device or resource busy
The command to re-read the partition table failed
Reboot your system now, before using mkfs

If you created or changed a DOS partition, /dev/foo7, say, then use dd(1)
to zero the first 512 bytes:  dd if=/dev/zero of=/dev/foo7 bs=512 count=1
(See fdisk(8).)
[/PHP]

---

### Post by caljohnsmith on 2008-12-23
Great, it looks like it finally worked, so the spaces after the file system ID seem to have been the problem. How about doing the Grub commands now and see if that works:
```
sudo grub
grub> root (hd1,2)
grub> setup (hd1)
grub> quit
```
If for some reason they don't work, please reboot your Live CD and try again. Also please post the output.

---

### Post by greenman1313 on 2008-12-23
The results (not 100% effective - I will reboot and try it again):
[PHP]ubuntu@ubuntu:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> root (hd1,2)
root (hd1,2)
grub> setup (hd1)
setup (hd1)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd1)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd1) (hd1)1+16 p (hd1,2)/boot/grub/stage2 /boot/grub/menu.lst"... failed

Error 22: No such partition
grub> quit
quit
ubuntu@ubuntu:~$ 
[/PHP]

---

### Post by caljohnsmith on 2008-12-23
After rebooting, please also post:
```
sudo sfdisk -d
sudo sfdisk -luS
sudo sfdisk -sV
```

---

### Post by greenman1313 on 2008-12-23
Here are the results of everything:
[PHP]To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> root (hd1,2)
root (hd1,2)
grub> setup (hd1)
setup (hd1)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd1)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd1) (hd1)1+16 p (hd1,2)/boot/grub/stage2 /boot/grub/menu.lst"... succeeded
Done.
grub> quit
quit
ubuntu@ubuntu:~$ sudo sfdisk -d
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       29, size=625137253, Id= 7, bootable
/dev/sda2 : start=        0, size=        0, Id= 0
/dev/sda3 : start=        0, size=        0, Id= 0
/dev/sda4 : start=        0, size=        0, Id= 0
# partition table of /dev/sdb
unit: sectors

/dev/sdb1 : start=       63, size=502257280, Id= 7, bootable
/dev/sdb2 : start=502272225, size=  2714985, Id= 5
/dev/sdb3 : start=505180053, size=119957292, Id=83
/dev/sdb4 : start=        0, size=        0, Id= 0
/dev/sdb5 : start=502272288, size=  2714922, Id=82
ubuntu@ubuntu:~$ sudo sfdisk -luS

Disk /dev/sda: 38913 cylinders, 255 heads, 63 sectors/track
Warning: The partition table looks like it was made
  for C/H/S=*/154/29 (instead of 38913/255/63).
For this listing I'll assume that geometry.
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1   *        29 625137281  625137253   7  HPFS/NTFS
/dev/sda2             0         -          0   0  Empty
/dev/sda3             0         -          0   0  Empty
/dev/sda4             0         -          0   0  Empty

Disk /dev/sdb: 38913 cylinders, 255 heads, 63 sectors/track
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sdb1   *        63 502257342  502257280   7  HPFS/NTFS
/dev/sdb2     502272225 504987209    2714985   5  Extended
/dev/sdb3     505180053 625137344  119957292  83  Linux
/dev/sdb4             0         -          0   0  Empty
/dev/sdb5     502272288 504987209    2714922  82  Linux swap / Solaris
ubuntu@ubuntu:~$ sudo sfdisk -sV
/dev/sda: 312571224
Warning: partition 1 does not end at a cylinder boundary
/dev/sdb: 312571224
Warning: partition 1 does not end at a cylinder boundary
total: 625142448 blocks
ubuntu@ubuntu:~$ 
[/PHP]

---

### Post by caljohnsmith on 2008-12-23
That's great news, it looks so far like our effort to convert your logical Ubuntu partition to a primary partition worked OK. How about rebooting, boot the sdb drive, and let me know exactly what happens.

---

### Post by greenman1313 on 2008-12-23
Okay, I booted into the sdb drive, and got the Grub screen. It had options for ubuntu, XP, and Vista. First, I tried to boot Vista; error 29 (happened repeatedly no matter how many times I tried to boot into Vista). Next, I tried to boot into XP, and kept getting error 29, no matter how many times I tried. Finally, I tried to boot into Ubuntu, and it worked!

I'm typing from the Ubuntu that was loaded onto my hard drive right now.

:)

---

### Post by caljohnsmith on 2008-12-23
Well I've certainly learned something new then, because I didn't think it would make any difference whether Ubuntu was on a logical or primary partition as far as causing a Grub error 18; but that seems to be true in your case. Next we'll need to repair your Vista and XP boot sectors, or more specifically, we're going to swap them since your XP partition has a Vista boot sector and your Vista partition has an XP boot sector. How about doing the following:
```
cd ~/Desktop
sudo dd if=/dev/sda1 of=sda1.bin count=9
sudo dd if=/dev/sdb1 of=sdb1.bin count=9
sudo dd if=sdb1.bin of=/dev/sda1 bs=1 skip=80 seek=80 
sudo dd if=sda1.bin of=/dev/sdb1 bs=1 skip=80 seek=80

```
Please post the output of all the above commands, and by the way, we both have meierfra to thank for figuring out which parts of the Vista/XP boot sectors need to be swapped in order to (hopefully) make it work. :) Next open your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And then swap the "title" lines of your XP/Vista entries, and also remove the "makeactive" and "savedefault" lines:
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Vista
root        (hd0,0)
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Windows XP
root        (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1

```
Next reboot and let me know what happens when you boot Vista/XP :)

---

### Post by meierfra. on 2008-12-23
> I tried to boot into Ubuntu, and it worked!

That's pretty amazing. This might be the first case where a grub error 18 was cured by turning a logical into primary partition. I got the idea from Hermanzone:


> I have also read of three separate instances where users claimed that installing Linux '/' (root) on a logical partition instead of a primary partition cleared this problem up for them. (..."Go figure?"..!)

But all those cases did the opposite: install Linux to a logical rather than a primary partition.

---

### Post by greenman1313 on 2008-12-23
:):)

Holy smokes... IT ALL WORKS!!!

:):)



I can't believe it - I appreciate your help so much Caljohnsmith and Meierfra. You guys took my problem child computer and whipped it into shape. Kudos to you! :)


Here are the results you asked for:
[PHP]justin@justin-desktop:~$ cd ~/Desktop
justin@justin-desktop:~/Desktop$ sudo dd if=/dev/sda1 of=sda1.bin count=9
[sudo] password for justin: 
9+0 records in
9+0 records out
4608 bytes (4.6 kB) copied, 0.0134399 s, 343 kB/s
justin@justin-desktop:~/Desktop$ sudo dd if=/dev/sdb1 of=sdb1.bin count=9
9+0 records in
9+0 records out
4608 bytes (4.6 kB) copied, 0.0219192 s, 210 kB/s
justin@justin-desktop:~/Desktop$ sudo dd if=sdb1.bin of=/dev/sda1 bs=1 skip=80 seek=80
4528+0 records in
4528+0 records out
4528 bytes (4.5 kB) copied, 0.0268442 s, 169 kB/s
justin@justin-desktop:~/Desktop$ sudo dd if=sda1.bin of=/dev/sdb1 bs=1 skip=80 seek=80
4528+0 records in
4528+0 records out
4528 bytes (4.5 kB) copied, 0.0196728 s, 230 kB/s
justin@justin-desktop:~/Desktop$ 
[/PHP]


** There are also two files on my desktop; one is named "sda1.bin" and the other is "sdb1.bin". they have a little orange lock in the upper right hand corner, and I can't open them up - it says "Could not display... There is no application installed for this file type". What should I do with those?



Man, this is great. You resurrected my computer from the depths of triple boot limbo. you guys should write a 'How To' triple boot. When I looked online, I saw everyone gushing about one writeup in particular, but the link would lead someplace where I could never find the writeup (some Russian blog?).

Thanks again! :)

---

### Post by caljohnsmith on 2008-12-23
That's great to hear that Ubuntu, XP, and Vista are all booting OK now. I'm still amazed that converting your Ubuntu partition from a logical to a primary partition actually made a difference. And thank you for being willing to experiment with your setup, because I think we all learned a lot in the process, or at least I did. Cheers, have fun with Vista, XP, and Ubuntu, and have a very Merry Christmas. :)

P.S. You can delete the sda1.bin and sdb1.bin files, those were only temporary files needed to swap your XP and Vista boot sectors.

---

### Post by greenman1313 on 2008-12-23
Merry Christmas to you - I hope Santa is kind to you this year. :)

---

