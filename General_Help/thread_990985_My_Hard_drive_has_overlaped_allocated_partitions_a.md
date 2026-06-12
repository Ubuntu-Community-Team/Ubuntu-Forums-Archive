---
title: "My Hard drive has overlaped allocated partitions and wont boot XP"
date: 2008-11-23
forum: General Help
---

### Post by togden on 2008-11-23
I wanted to add XP to my Grub loader but when i looked at the drive partitions it said this
    
Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1824    14651248+  83  Linux
/dev/sda2            1825        3648    14651280    f  W95 Ext'd (LBA)
/dev/sda3            3649        6017    19028992+  82  Linux swap / Solaris
/dev/sda4   *        6018        9040    24280064    7  HPFS/NTFS
/dev/sda5            1825        3648    14651248+   7  HPFS/NTFS

XP is on /dev/sda5
I'm guessing this is why it wont load XP, but it might not be because of this

See blow for additional related info

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
# kopt=root=UUID=b6fd3816-5c72-450c-aeec-29c20c21fec7 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=b6fd3816-5c72-450c-aeec-29c20c21fec7 ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=b6fd3816-5c72-450c-aeec-29c20c21fec7 ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda4
title		Windows Vista/Longhorn (loader)
root		(hd0,3)
savedefault
makeactive
chainloader	+1

# this entry added by James for WinXP partition
# on /dev/sda2
title Microsoft Windows XP Professional
root (hd0,1)
makeactive
map (hd0,0) (hd0,1)
map (hd0,1) (hd0,0)
rootnoverify (hd0,1)
chainloader +1
savedefault

Disk /dev/sda: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7c787c78

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1824    14651248+  83  Linux
/dev/sda2            1825        3648    14651280    f  W95 Ext'd (LBA)
/dev/sda3            3649        6017    19028992+  82  Linux swap / Solaris
/dev/sda4   *        6018        9040    24280064    7  HPFS/NTFS
/dev/sda5            1825        3648    14651248+   7  HPFS/NTFS

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf4dff4df

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30514   245103673+   7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x969b09a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001    7  HPFS/NTFS

---

### Post by caljohnsmith on 2008-11-23
Are you sure XP is on sda5? If that's true, then XP's boot files are most likely in your sda4 Vista partition. It is possible to boot XP solely from a logical partition if you move XP's boot files into the XP partition, but you also have to modify the boot.ini file and do some other fixes. A simpler solution for you might be to use [EasyBCD]("http://neosmart.net/dl.php?id=1") to add XP to Vista boot loader menu, if it isn't there all ready. That way you would boot Vista from Grub, and then boot XP from Vista's boot menu. Or if you really want to boot XP from Grub, you'll have to do as I mentioned and move the boot files and do some modifications. If you want more details of how to do that, let me know.

---

### Post by togden on 2008-12-05
Yeah, id like to add XP to my grub loader, If its ok, could you please give me more details on how i would do that, thanks

---

### Post by caljohnsmith on 2008-12-05
OK, how about posting:
```
sudo mkdir /mnt/sda4 /mnt/sda5
sudo mount /dev/sda4 /mnt/sda4
sudo mount /dev/sda5 /mnt/sda5
ls -l /mnt/sda4 /mnt/sda5
cat /mnt/sda4/boot.ini /mnt/sda5/boot.ini
```
Note "-l" is a lowercase L, not a one. Also, do you have a Vista Install CD? There's a chance you will need it to do a few minor repairs in order to get everything working OK.

---

### Post by togden on 2008-12-09
/mnt/sda4:
total 3764810
-rwxrwxrwx 1 root root         24 2006-09-18 22:43 autoexec.bat
-rwxrwxrwx 1 root root        960 2008-12-08 23:13 bar.emf
drwxrwxrwx 1 root root       4096 2008-09-10 07:16 Boot
-rwxrwxrwx 1 root root     438840 2006-11-02 09:53 bootmgr
-rwxrwxrwx 1 root root       8192 2008-09-10 07:16 BOOTSECT.BAK
-rwxrwxrwx 2 root root         10 2006-09-18 22:43 config.sys
drwxrwxrwx 1 root root          0 2006-11-02 13:02 Documents and Settings
-rwxrwxrwx 1 root root   51568640 2008-10-22 00:58 dump_dvd.vob
-rwxrwxrwx 1 root root          0 2008-10-24 14:18 IO.SYS
-rwxrwxrwx 1 root root          0 2008-10-24 14:18 MSDOS.SYS
drwxrwxrwx 1 root root          0 2008-10-18 15:16 MSOCache
-rwxrwxrwx 1 root root 3802923008 2008-12-08 17:50 pagefile.sys
drwxrwxrwx 1 root root          0 2008-12-07 11:17 photos
drwxrwxrwx 1 root root       4096 2008-12-06 19:56 ProgramData
drwxrwxrwx 1 root root      12288 2008-11-14 10:26 Program Files
drwxrwxrwx 1 root root     167936 2008-12-08 23:05 QUARANTINE
drwxrwxrwx 1 root root          0 2008-09-09 22:26 $Recycle.Bin
-rwxrwxrwx 2 root root        268 2008-10-14 17:04 sqmdata00.sqm
-rwxrwxrwx 2 root root        244 2008-10-14 17:04 sqmnoopt00.sqm
drwxrwxrwx 1 root root          0 2008-09-09 22:17 System Volume Information
drwxrwxrwx 1 root root          0 2008-12-06 19:56 temp
drwxrwxrwx 1 root root       4096 2008-09-09 22:25 Users
drwxrwxrwx 1 root root          0 2008-12-07 11:17 videos
drwxrwxrwx 1 root root      24576 2008-12-08 19:56 Windows

/mnt/sda5:
total 2095144
drwxrwxrwx 1 root root       4096 2008-09-09 21:20 Documents and Settings
-rwxrwxrwx 1 root root 2145386496 2008-09-09 21:57 pagefile.sys
drwxrwxrwx 1 root root       4096 2008-09-09 21:26 Program Files
drwxrwxrwx 1 root root          0 2008-09-09 22:26 $RECYCLE.BIN
drwxrwxrwx 1 root root       4096 2008-09-09 21:18 System Volume Information
drwxrwxrwx 1 root root      28672 2008-09-09 21:46 WINDOWS

---

### Post by togden on 2008-12-09
When i entered the final command cat /mnt/sda4/boot.ini /mnt/sda5/boot.ini
It returned the error, no such file or directory for both partitons, and i was unable to get anything else when i tried to redirect it to where i think my boot.ini is on the vista drive, and i sort of have a vista CD, i have vista lite 32bit which is whats installed, which is a hacked copy but i do have a 64bit DVD.

---

### Post by meson2439 on 2008-12-09
DISCLAIMER: Follow the advice below at your own cost. I'm not responsible for what happens to your VISTA. My advice works upon the assumption that VISTA will not fuss about it.

From what I see, both your disk don't have boot.ini either because you delete them or they just dissapear because of VISTA. My suggestion is to write one up.
```
gedit /mnt/sda5/boot.ini
```
and afterwards insert this into the boot.ini
```

[boot loader]
timeout=15
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS /noexecute=optin /fastdetect

```
 If it still doesn't work
You can change 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

to either ones that work below
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS /noexecute=optin /fastdetect
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS /noexecute=optin /fastdetect
multi(0)disk(0)rdisk(0)partition(4)\WINDOWS /noexecute=optin /fastdetect
multi(0)disk(0)rdisk(0)partition(5)\WINDOWS /noexecute=optin /fastdetect

also make sure the default is similar. You can add vista on that list because I do not know how. For heaven's sake I hope it is as simple as changing partition(x). If that still doesn't work, try modifying in Grub by replacing
```
title Microsoft Windows XP Professional
root (hd0,1)
makeactive
map (hd0,0) (hd0,1)
map (hd0,1) (hd0,0)
rootnoverify (hd0,1)
chainloader +1
savedefault
```

with

```
title Windows 
root (hd0,1)
makeactive
chainloader +1
savedefault
```

and try playing with root (hd0,1) by changing it to either
root (hd0,2)
root (hd0,3)
root (hd0,4)
root (hd0,5)

AGAIN DISCLAIMER:I'm not responsible to what happens to your computer so backup everything first. Send all data to different computer or backup device.

---

### Post by togden on 2008-12-11
thanks, ive created the boot.ini in sda5 but altering the grub like that will prevent it from working, because xp has to be mapped into partition 0, or so i am told

---

### Post by caljohnsmith on 2008-12-11
OK, how about downloading the attached "WinXP_boot_files.zip" file to your desktop, and then do:
```
sudo mount /dev/sda5 /mnt
cd ~/Desktop
unzip WinXP_boot_files.zip
sudo mv boot.ini ntldr NTDETECT.COM /mnt
```
Then open your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And change your Windows XP entry at the end to:
```
title Windows XP
rootnoverify (hd0,4)
chainloader +1
```
Then reboot, select XP from the Grub menu, and let me know exactly what happens. We can work from there.

---

### Post by togden on 2008-12-11
ok that made some progress, it actually began to boot , it said starting up in white dos writing in the top left and then did nothing more

---

### Post by caljohnsmith on 2008-12-11
So just to check, you're sure your Windows XP entry does not have any "map" lines or anything in addition to what is in my previous post? The next step would be to check the XP partition boot sector with "testdisk", so first make sure the Ubuntu Universe repository is enabled in System > Admin > Software Sources, and then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk, choose "no log", choose the correct HDD and "proceed", choose "intel", choose "advanced", select the Windows XP partition (sda5), choose "boot", then choose "Rebuild BS"; if testdisk gives you a warning that the "sectors are not identical", then choose "write". After you are done doing the "rebuild BS" in testdisk, reboot and let me know exactly what happens when you boot XP from Grub. If it displays any errors or text, please let me know what it says.

---

### Post by meson2439 on 2008-12-12
Can I ask which is the OS first installed, Vista, XP or Ubuntu?? If Vista is the first and XP is the second then you use

root hd(0,1)

under XP. If XP is installed after Ubuntu, then

root hd(0,4)

under XP. 

I also assure you that using partition(1) or partition(4) in XP is quite safe.

---

### Post by togden on 2008-12-22
Yeh after selecting windows XP from the grub boot menu, it says starting up in white text at the top left of the screen, after a few minutes it still says starting up and gets no further.

---

