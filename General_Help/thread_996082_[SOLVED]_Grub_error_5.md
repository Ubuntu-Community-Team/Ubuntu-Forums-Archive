---
title: "[SOLVED] Grub error 5"
date: 2008-11-28
forum: General Help
---

### Post by jcsaintpo on 2008-11-28
my pc is dual-boot ubuntu 8.04  windows-xp

I get the mentioning
"grub error 5" everytime i want to start up windows xp!
No problem to start up Ubuntu!

How can I get Xp to start up again?

Kind greets
JC

---

### Post by psusi on 2008-11-28
Post the output of:

sudo fdisk -l
sudo cat /boot/grub/menu.lst

---

### Post by jcsaintpo on 2008-11-28
> **psusi said:**
> Post the output of:

sudo fdisk -l  

Schijf /dev/sda: 250.0 GB, 250059350016 bytes
255 koppen, 63 sectoren/spoor, 30401 cilinders
Eenheid = cilinders van 16065 * 512 = 8225280 bytes
Schijf-ID: 0x44684467

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sda1   *           1        5447    43752996    7  HPFS/NTFS
/dev/sda2            5448       30401   200443005    f  W95 Uitgeb. (LBA)
/dev/sda5            5448        6467     8193118+   7  HPFS/NTFS
/dev/sda6            6468       15391    71681998+   7  HPFS/NTFS
/dev/sda7           15392       16666    10241406    7  HPFS/NTFS
/dev/sda8           16667       17304     5124703+   7  HPFS/NTFS
/dev/sda9           17305       17942     5124703+   7  HPFS/NTFS
/dev/sda10          17943       18580     5124703+   7  HPFS/NTFS
/dev/sda11          18581       26448    63199678+   7  HPFS/NTFS
/dev/sda12          28489       30401    15366141    b  W95 FAT32
/dev/sda13          26449       28397    15655311   83  Linux
/dev/sda14          28398       28488      730926   82  Linux wisselgeheugen

Partitietabel-items liggen niet in schijfvolgorde.


> **psusi said:**
>  sudo cat /boot/grub/menu.lst

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
# kopt=root=UUID=eb2055e1-3c1e-467d-a8d5-631aa3fb1984 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,12)

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

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic
root		(hd0,12)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=eb2055e1-3c1e-467d-a8d5-631aa3fb1984 ro quiet splash
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode)
root		(hd0,12)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=eb2055e1-3c1e-467d-a8d5-631aa3fb1984 ro single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd0,12)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=eb2055e1-3c1e-467d-a8d5-631aa3fb1984 ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,12)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=eb2055e1-3c1e-467d-a8d5-631aa3fb1984 ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,12)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=eb2055e1-3c1e-467d-a8d5-631aa3fb1984 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,12)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=eb2055e1-3c1e-467d-a8d5-631aa3fb1984 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,12)
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

---

### Post by caljohnsmith on 2008-11-28
From the Grub manual:
> **Error 5**: Partition table invalid or corrupt
This error is returned if the sanity checks on the integrity of the partition table fail. This is a bad sign.
So I think it would be a good idea to check the integrity of your HDD's partition table. How about first making sure the Ubuntu Universe repository is enabled in System > Admin > Software Sources, and then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk with the above command, choose "no log", select HDD and "proceed", "Intel", "Analyze", and see what it shows for your HDD and what errors it might give. Please post the output of that screen. Then do "quick search", Y/N depending on if you have any Vista partitions, hit enter to continue, and select "Deeper Search" so it does a deeper search, which could take a while. Post the output of the screen that has the deep search results, and we can work from there if you want. :)

---

### Post by jcsaintpo on 2008-11-28
> **caljohnsmith said:**
> From the Grub manual:

So I think it would be a good idea to check the integrity of your HDD's partition table. How about first making sure the Ubuntu Universe repository is enabled in System > Admin > Software Sources, and then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk with the above command, choose "no log", select HDD and "proceed", "Intel", "Analyze", and see what it shows for your HDD and what errors it might give. Please post the output of that screen. Then do "quick search", Y/N depending on if you have any Vista partitions, hit enter to continue, and select "Deeper Search" so it does a deeper search, which could take a while. Post the output of the screen that has the deep search results, and we can work from there if you want. :)

TestDisk 6.8, Data Recovery Utility, August 2007
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 250 GB / 232 GiB - CHS 30401 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 * HPFS - NTFS              0   1  1  5446 254 63   87505992 [Windows]
 2 E extended LBA          5447   0  1 30400 254 63  400886010
 5 L HPFS - NTFS           5447   1  1  6466 254 63   16386237 [BACKUP]
   X extended              6467   0  1 15390 254 63  143364060
 6 L HPFS - NTFS           6467   1  1 15390 254 63  143363997 [PROGRAMMAS]
   X extended             15391   0  1 16665 254 63   20482875
 7 L HPFS - NTFS          15391   1  1 16665 254 63   20482812 [GEGEVENS]
   X extended             16666   0  1 17303 254 63   10249470
 8 L HPFS - NTFS          16666   1  1 17303 254 63   10249407 [MAIL]
   X extended             17304   0  1 17941 254 63   10249470
 9 L HPFS - NTFS          17304   1  1 17941 254 63   10249407 [INTERNET]
   X extended             17942   0  1 18579 254 63   10249470
10 L HPFS - NTFS          17942   1  1 18579 254 63   10249407 [WEBSITE]
    Next
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted



TestDisk 6.8, Data Recovery Utility, August 2007
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 250 GB / 232 GiB - CHS 30401 255 63
     Partition               Start        End    Size in sectors
D HPFS - NTFS              0   1  1  5446 254 63   87505992 [Windows]
D HPFS - NTFS              0   1  8  5446 254 63   87505985
L HPFS - NTFS           5447   1  1  6466 254 63   16386237 [BACKUP]
L HPFS - NTFS           6467   1  1 15390 254 63  143363997 [PROGRAMMAS]
L HPFS - NTFS          15391   1  1 16665 254 63   20482812 [GEGEVENS]
L HPFS - NTFS          16666   1  1 17303 254 63   10249407 [MAIL]
L HPFS - NTFS          17304   1  1 17941 254 63   10249407 [INTERNET]
L HPFS - NTFS          17942   1  1 18579 254 63   10249407 [WEBSITE]
D HPFS - NTFS          18580   1  1 26447 254 63  126399357 [FILMS]
D HPFS - NTFS          18580   1  1 28487 254 63  159171957 [FILMS]
D HPFS - NTFS          18580   1 13 26447 254 63  126399345
D Linux                26448   1  1 28396 254 63   31310622
D Linux Swap           28397   1  1 28487 254 63    1461852
Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,



TestDisk 6.8, Data Recovery Utility, August 2007
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 250 GB / 232 GiB - CHS 30401 255 63

     Partition                  Start        End    Size in sectors

 1 E extended LBA          5447   0  1 30400 254 63  400886010
 5 L HPFS - NTFS           5447   1  1  6466 254 63   16386237 [BACKUP]
 6 L HPFS - NTFS           6467   1  1 15390 254 63  143363997 [PROGRAMMAS]
 7 L HPFS - NTFS          15391   1  1 16665 254 63   20482812 [GEGEVENS]
 8 L HPFS - NTFS          16666   1  1 17303 254 63   10249407 [MAIL]
 9 L HPFS - NTFS          17304   1  1 17941 254 63   10249407 [INTERNET]
10 L HPFS - NTFS          17942   1  1 18579 254 63   10249407 [WEBSITE]
11 L FAT32 LBA            28488   1  1 30400 254 63   30732282 [RECOVER]

---

### Post by caljohnsmith on 2008-11-28
From what I can tell from the testdisk output compared to the fdisk output, it looks like your partition table is OK; you had so many partitions listed though that it scrolled off the screen in testdisk, so I couldn't see all of them in that first screen you posted. What led up to getting the Grub error 5? Were you able to boot XP from Grub just fine before? What might have changed on your computer around the time you started getting the Grub error? 

How about opening your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And change your Windows entry to:
```
title Windows XP
rootnoverify (hd0,0)
chainloader +1

```
Next, reinstall Grub:
```
sudo apt-get purge grub
sudo apt-get install grub
sudo grub-install --recheck /dev/sda
```
Reboot, and let me know if you get the same Grub error.

---

### Post by jcsaintpo on 2008-11-28
> **caljohnsmith said:**
> From what I can tell from the testdisk output compared to the fdisk output, it looks like your partition table is OK; you had so many partitions listed though that it scrolled off the screen in testdisk, so I couldn't see all of them in that first screen you posted. What led up to getting the Grub error 5? Were you able to boot XP from Grub just fine before? What might have changed on your computer around the time you started getting the Grub error? 

How about opening your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And change your Windows entry to:
```
title Windows XP
rootnoverify (hd0,0)
chainloader +1

```
Next, reinstall Grub:
```
sudo apt-get purge grub
sudo apt-get install grub
sudo grub-install --recheck /dev/sda
```
Reboot, and let me know if you get the same Grub error.

I was able to start “windows xp” just fine before!
I put always windows in sleeping mode!
This time it didn't wanted to wake up again!
Before it was never a problem!


I will try now changing what you mentioned

---

### Post by jcsaintpo on 2008-11-28
here menu.lst




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
# kopt=root=UUID=eb2055e1-3c1e-467d-a8d5-631aa3fb1984 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,12)

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

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic
root		(hd0,12)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=eb2055e1-3c1e-467d-a8d5-631aa3fb1984 ro quiet splash
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode)
root		(hd0,12)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=eb2055e1-3c1e-467d-a8d5-631aa3fb1984 ro single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd0,12)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=eb2055e1-3c1e-467d-a8d5-631aa3fb1984 ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,12)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=eb2055e1-3c1e-467d-a8d5-631aa3fb1984 ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,12)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=eb2055e1-3c1e-467d-a8d5-631aa3fb1984 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,12)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=eb2055e1-3c1e-467d-a8d5-631aa3fb1984 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,12)
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

---

### Post by jcsaintpo on 2008-11-28
I keep having the same problem!

Grub loading .........
Error 5

---

### Post by caljohnsmith on 2008-11-28
I forgot to ask you to post the output of the previous commands, so please post the output of:
```
sudo apt-get purge grub
sudo apt-get install grub
sudo grub-install --recheck /dev/sda
```
And also post the output of:
```
sudo mount /dev/sda1 /mnt
ls -l /mnt
cat /mnt/boot.ini
```
The above commands are mainly to check that your Windows partition is still mountable and readable. Unfortunately though, it sounds like you might have a Windows problem and not a Grub problem. Do you have a Windows Install CD? If so, boot that, go to the "recovery console", and do:
```
fixboot
chkdsk /r
```
And run the chkdsk command as many times as it takes until it reports no errors. If you don't have a Windows Install CD, you can download a Windows Repair CD from [here]("http://www.webtree.ca/windowsxp/tools/bootdiscs/xp_rec_con.zip").

---

### Post by jcsaintpo on 2008-11-29
> **caljohnsmith said:**
> I forgot to ask you to post the output of the previous commands, so please post the output of:
```
sudo apt-get purge grub
sudo apt-get install grub
sudo grub-install --recheck /dev/sda
```

Probing devices to guess BIOS drives. This may take a long time.
Searching for GRUB installation directory ... found: /boot/grub
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(fd0)	/dev/fd0
(hd0)	/dev/sda


> **caljohnsmith said:**
> 
And also post the output of:
```
sudo mount /dev/sda1 /mnt
ls -l /mnt
cat /mnt/boot.ini
```

 sudo mount /dev/sda1 /mnt
Windows is hibernated, refused to mount.
Failed to mount '/dev/sda1': Bewerking niet toegestaan
The NTFS partition is hibernated. Please resume and shutdown Windows
properly, or mount the volume read-only with the 'ro' mount option, or
mount the volume read-write with the 'remove_hiberfile' mount option.
For example type on the command line:

            mount -t ntfs-3g /dev/sda1 /mnt -o remove_hiberfile


 ls -l /mnt
totaal 0


cat /mnt/boot.ini
cat: /mnt/boot.ini: Bestand of map bestaat niet


> **caljohnsmith said:**
> 
The above commands are mainly to check that your Windows partition is still mountable and readable. Unfortunately though, it sounds like you might have a Windows problem and not a Grub problem. Do you have a Windows Install CD? If so, boot that, go to the "recovery console", and do:
```
fixboot
chkdsk /r
```
And run the chkdsk command as many times as it takes until it reports no errors. If you don't have a Windows Install CD, you can download a Windows Repair CD from [here]("http://www.webtree.ca/windowsxp/tools/bootdiscs/xp_rec_con.zip").

---

### Post by jcsaintpo on 2008-11-29
mount -t ntfs-3g /dev/sda1 /mnt -o remove_hiberfile
mount: alleen root kan dat doen

---

### Post by jcsaintpo on 2008-11-29
> **caljohnsmith said:**
> 
The above commands are mainly to check that your Windows partition is still mountable and readable. Unfortunately though, it sounds like you might have a Windows problem and not a Grub problem. Do you have a Windows Install CD? If so, boot that, go to the "recovery console", and do:
```
fixboot
chkdsk /r
```
And run the chkdsk command as many times as it takes until it reports no errors. If you don't have a Windows Install CD, you can download a Windows Repair CD from [here]("http://www.webtree.ca/windowsxp/tools/bootdiscs/xp_rec_con.zip").

I downloaded the program, wrote it on a cd via Ubuntu (lucky that I have dualboot) Then got into recovery console!
Followed your instructions, and now evrything works just fine again!!!!!!!!!!!!!!!
Windows booted again as usual!
Thank you very much for your help!  It was much appreciated!

Funny to know I got so much more help from ubuntu then I ever got from the other company!
You seem to know more about them, then they about you! :-))))))))))

---

### Post by caljohnsmith on 2008-11-29
That's great news, I'm really glad it worked and didn't take any more effort than simply running those commands from the Repair CD. Cheers and have fun with Windows and Ubuntu. :)

---

### Post by jcsaintpo on 2009-01-04
grrrrrrrrrrrrrrrrrrrrrrr it happened again!!!!!!!!!
now nothing helps! :-(
any other solutions?

---

### Post by caljohnsmith on 2009-01-04
So are you getting the Grub error 5 again when you try and boot Windows? How about opening a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup in order to get a better idea of which direction to take.

---

### Post by jcsaintpo on 2009-01-04
grrrrrrrrrrrrrrrrrrrrrrr it happened again!!!!!!!!!
now nothing helps! :-(
any other solutions?

(sorry had connectionproblems, therefore I unfortunately added 2 times same message)

---

### Post by jcsaintpo on 2009-01-04
> **caljohnsmith said:**
> So are you getting the Grub error 5 again when you try and boot Windows? How about opening a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup in order to get a better idea of which direction to take.

```
============================= Boot Info Summary: ==============================

 => Grub is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #13 for its boot files.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
Windows is hibernated, refused to mount.
Failed to mount '/dev/sda1': Bewerking niet toegestaan
The NTFS partition is hibernated. Please resume and shutdown Windows
properly, or mount the volume read-only with the 'ro' mount option, or
mount the volume read-write with the 'remove_hiberfile' mount option.
For example type on the command line:

            mount -t ntfs-3g /dev/sda1 sda1 -o remove_hiberfile


sda10: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda10 starts 
                       at sector 63, but according to the info from fdisk, 
                       sda10 starts at sector 288238293 .
    Mounting failed:
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda10': Bewerking wordt niet ondersteund
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda10 sda10 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda10 sda10 ntfs-3g force 0 0

sda11: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda11 starts 
                       at sector 63, but according to the info from fdisk, 
                       sda11 starts at sector 298487763 .
    Mounting failed:
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda11': Bewerking wordt niet ondersteund
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda11 sda11 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda11 sda11 ntfs-3g force 0 0

sda12: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Win_98
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda13: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  Ubuntu 8.04.1
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sda14: _________________________________________________________________________

    File system:       swap

sda2: _________________________________________________________________________

    File system:       Extended Partition

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63, but according to the info from fdisk, 
                       sda5 starts at sector 87506118 . The info in boot 
                       sector on the starting sector of the MFT is wrong. The 
                       info in the boot sector on the starting sector of the 
                       MFT Mirror is wrong.
    Mounting failed:
$LogFile indicates unclean shutdown (0, 1)
Failed to mount '/dev/sda5': Bewerking wordt niet ondersteund
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda5 sda5 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda5 sda5 ntfs-3g force 0 0

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63, but according to the info from fdisk, 
                       sda6 starts at sector 103892418 .
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63, but according to the info from fdisk, 
                       sda7 starts at sector 247256478 .
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda8 starts 
                       at sector 63, but according to the info from fdisk, 
                       sda8 starts at sector 267739353 .
    Mounting failed:
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda8': Bewerking wordt niet ondersteund
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda8 sda8 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda8 sda8 ntfs-3g force 0 0

sda9: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda9 starts 
                       at sector 63, but according to the info from fdisk, 
                       sda9 starts at sector 277988823 .
    Mounting failed:
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda9': Bewerking wordt niet ondersteund
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda9 sda9 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda9 sda9 ntfs-3g force 0 0

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Schijf /dev/sda: 250.0 GB, 250059350016 bytes
255 koppen, 63 sectoren/spoor, 30401 cilinders, totaal 488397168 sectoren
Eenheid = sectoren van 1 * 512 = 512 bytes
Schijf-ID: 0x44684467

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sda1   *          63    87506054    43752996    7  HPFS/NTFS
/dev/sda2        87506055   488392064   200443005    f  W95 Uitgeb. (LBA)
/dev/sda5        87506118   103892354     8193118+   7  HPFS/NTFS
/dev/sda6       103892418   247256414    71681998+   7  HPFS/NTFS
/dev/sda7       247256478   267739289    10241406    7  HPFS/NTFS
/dev/sda8       267739353   277988759     5124703+   7  HPFS/NTFS
/dev/sda9       277988823   288238229     5124703+   7  HPFS/NTFS
/dev/sda10      288238293   298487699     5124703+   7  HPFS/NTFS
/dev/sda11      298487763   424887119    63199678+   7  HPFS/NTFS
/dev/sda12      457659783   488392064    15366141    b  W95 FAT32
/dev/sda13      424887183   456197804    15655311   83  Linux
/dev/sda14      456197868   457659719      730926   82  Linux wisselgeheugen

Partitietabel-items liggen niet in schijfvolgorde.

sfdisk -V /dev/sda:

partitie 2: begin: (c,k,s) verwacht: (1023,254,63) gevonden: (1023,0,1)
partitie 5: begin: (c,k,s) verwacht: (1023,254,63) gevonden: (1023,1,1)
partitie 6: begin: (c,k,s) verwacht: (1023,254,63) gevonden: (1023,1,1)
partitie 7: begin: (c,k,s) verwacht: (1023,254,63) gevonden: (1023,1,1)
partitie 8: begin: (c,k,s) verwacht: (1023,254,63) gevonden: (1023,1,1)
partitie 9: begin: (c,k,s) verwacht: (1023,254,63) gevonden: (1023,1,1)
partitie 10: begin: (c,k,s) verwacht: (1023,254,63) gevonden: (1023,1,1)
partitie 11: begin: (c,k,s) verwacht: (1023,254,63) gevonden: (1023,1,1)
partitie 12: begin: (c,k,s) verwacht: (1023,254,63) gevonden: (1023,1,1)
/dev/sda: OK

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="C488292888291B06" LABEL="Windows" TYPE="ntfs" 
/dev/sda5: UUID="1120EA0FBA41E599" LABEL="BACKUP" TYPE="ntfs" 
/dev/sda6: UUID="968C80DE8C80B9EF" LABEL="PROGRAMMAS" TYPE="ntfs" 
/dev/sda7: UUID="FA1883451882FFBD" LABEL="GEGEVENS" TYPE="ntfs" 
/dev/sda8: UUID="580485E70485C888" LABEL="MAIL" TYPE="ntfs" 
/dev/sda9: UUID="2CB088BBB0888CD0" LABEL="INTERNET" TYPE="ntfs" 
/dev/sda10: UUID="A6888B85888B532B" LABEL="WEBSITE" TYPE="ntfs" 
/dev/sda11: UUID="CA7C8F487C8F2E6F" LABEL="FILMS" TYPE="ntfs" 
/dev/sda12: LABEL="RECOVER" UUID="846F-F78E" TYPE="vfat" 
/dev/sda13: UUID="eb2055e1-3c1e-467d-a8d5-631aa3fb1984" TYPE="ext3" 
/dev/sda14: TYPE="swap" UUID="5e94c590-e6be-4fe9-a911-67909df2e4dc" 

=============================== "mount" output: ===============================

/dev/sda13 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-22-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/chris/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=chris)

========================== sda13/boot/grub/menu.lst: ==========================

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
# kopt=root=UUID=eb2055e1-3c1e-467d-a8d5-631aa3fb1984 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,12)

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

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic
root		(hd0,12)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=eb2055e1-3c1e-467d-a8d5-631aa3fb1984 ro quiet splash
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode)
root		(hd0,12)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=eb2055e1-3c1e-467d-a8d5-631aa3fb1984 ro single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd0,12)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=eb2055e1-3c1e-467d-a8d5-631aa3fb1984 ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,12)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=eb2055e1-3c1e-467d-a8d5-631aa3fb1984 ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,12)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=eb2055e1-3c1e-467d-a8d5-631aa3fb1984 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,12)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=eb2055e1-3c1e-467d-a8d5-631aa3fb1984 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,12)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP
rootnoverify		(hd0,0)
chainloader	+1


=============================== sda13/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda13
UUID=eb2055e1-3c1e-467d-a8d5-631aa3fb1984 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda14
UUID=5e94c590-e6be-4fe9-a911-67909df2e4dc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

================================= sda13/boot: =================================

totaal 56020
drwxr-xr-x  3 root root    4096 2008-12-10 21:02 .
drwxr-xr-x 22 root root    4096 2008-11-28 15:59 ..
-rw-r--r--  1 root root  420224 2008-08-21 00:15 abi-2.6.24-19-generic
-rw-r--r--  1 root root  420395 2008-10-22 03:49 abi-2.6.24-21-generic
-rw-r--r--  1 root root  420395 2008-11-24 23:19 abi-2.6.24-22-generic
-rw-r--r--  1 root root   74164 2008-08-21 00:15 config-2.6.24-19-generic
-rw-r--r--  1 root root   74177 2008-10-22 03:49 config-2.6.24-21-generic
-rw-r--r--  1 root root   74177 2008-11-24 23:19 config-2.6.24-22-generic
drwxr-xr-x  2 root root    4096 2009-01-04 13:03 grub
-rw-r--r--  1 root root 7736303 2008-08-27 18:00 initrd.img-2.6.24-19-generic
-rw-r--r--  1 root root 7736831 2008-08-13 19:19 initrd.img-2.6.24-19-generic.bak
-rw-r--r--  1 root root 7737952 2008-11-08 10:29 initrd.img-2.6.24-21-generic
-rw-r--r--  1 root root 7737709 2008-11-03 17:22 initrd.img-2.6.24-21-generic.bak
-rw-r--r--  1 root root 7735870 2008-12-10 21:02 initrd.img-2.6.24-22-generic
-rw-r--r--  1 root root 7734203 2008-11-28 15:59 initrd.img-2.6.24-22-generic.bak
-rw-r--r--  1 root root  103204 2007-09-28 13:03 memtest86+.bin
-rw-r--r--  1 root root 1152364 2008-08-21 00:15 System.map-2.6.24-19-generic
-rw-r--r--  1 root root 1153201 2008-10-22 03:49 System.map-2.6.24-21-generic
-rw-r--r--  1 root root 1153201 2008-11-24 23:19 System.map-2.6.24-22-generic
-rw-r--r--  1 root root 1903096 2008-08-21 00:15 vmlinuz-2.6.24-19-generic
-rw-r--r--  1 root root 1905688 2008-10-22 03:49 vmlinuz-2.6.24-21-generic
-rw-r--r--  1 root root 1905656 2008-11-24 23:19 vmlinuz-2.6.24-22-generic

=============================== sda13/boot/grub: ===============================

totaal 212
drwxr-xr-x 2 root root   4096 2009-01-04 13:03 .
drwxr-xr-x 3 root root   4096 2008-12-10 21:02 ..
-rw-r--r-- 1 root root    197 2009-01-04 13:03 default
-rw-r--r-- 1 root root     30 2009-01-04 13:03 device.map
-rw-r--r-- 1 root root   8056 2009-01-04 13:03 e2fs_stage1_5
-rw-r--r-- 1 root root   7904 2009-01-04 13:03 fat_stage1_5
-rw-r--r-- 1 root root     18 2009-01-04 13:10 installed-version
-rw-r--r-- 1 root root   8608 2009-01-04 13:03 jfs_stage1_5
-rw-r--r-- 1 root root   5416 2008-11-28 21:59 menu.lst
-rw-r--r-- 1 root root   5454 2008-11-28 15:59 menu.lst~
-rw-r--r-- 1 root root   7324 2009-01-04 13:03 minix_stage1_5
-rw-r--r-- 1 root root   9632 2009-01-04 13:03 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2009-01-04 13:03 stage1
-rw-r--r-- 1 root root 108356 2009-01-04 13:10 stage2
-rw-r--r-- 1 root root   9276 2009-01-04 13:03 xfs_stage1_5

=========================== Unknown MBRs or Boot Sectors =======================

MFT Sector of /dev/sda5

00000000  46 49 4c 45 2a 00 03 00  00 00 00 00 00 00 00 00  |FILE*...........|
00000010  01 00 01 00 30 00 05 00  90 01 00 00 00 04 00 00  |....0...........|
00000020  00 00 00 00 00 00 00 00  04 00 5b 00 00 00 00 00  |..........[.....|
00000030  10 00 00 00 60 00 00 00  00 00 18 00 00 00 00 00  |....`...........|
00000040  48 00 00 00 18 00 00 00  35 de 22 25 34 2a c5 01  |H.......5."%4*..|
00000050  35 de 22 25 34 2a c5 01  35 de 22 25 34 2a c5 01  |5."%4*..5."%4*..|
00000060  35 de 22 25 34 2a c5 01  06 00 00 00 00 00 00 00  |5."%4*..........|
00000070  00 00 00 00 00 00 00 00  00 00 00 00 00 01 00 00  |................|
00000080  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000090  30 00 00 00 68 00 00 00  00 00 18 00 00 00 01 00  |0...h...........|
000000a0  4a 00 00 00 18 00 01 00  05 00 00 00 00 00 05 00  |J...............|
000000b0  35 de 22 25 34 2a c5 01  35 de 22 25 34 2a c5 01  |5."%4*..5."%4*..|
*
000000d0  00 00 57 00 00 00 00 00  00 00 57 00 00 00 00 00  |..W.......W.....|
000000e0  06 00 00 00 00 00 00 00  04 03 24 00 4d 00 46 00  |..........$.M.F.|
000000f0  54 00 00 00 00 00 00 00  80 00 00 00 48 00 00 00  |T...........H...|
00000100  01 00 40 00 00 00 02 00  00 00 00 00 00 00 00 00  |..@.............|
00000110  6f 05 00 00 00 00 00 00  40 00 00 00 00 00 00 00  |o.......@.......|
00000120  00 00 57 00 00 00 00 00  00 00 57 00 00 00 00 00  |..W.......W.....|
00000130  00 00 57 00 00 00 00 00  32 70 05 00 00 0c 00 00  |..W.....2p......|
00000140  b0 00 00 00 48 00 00 00  01 00 40 00 00 00 03 00  |....H.....@.....|
00000150  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000160  40 00 00 00 00 00 00 00  00 10 00 00 00 00 00 00  |@...............|
00000170  b8 02 00 00 00 00 00 00  b8 02 00 00 00 00 00 00  |................|
00000180  21 01 15 40 00 00 00 00  ff ff ff ff 00 00 00 00  |!..@............|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 5b 00  |..............[.|
00000200

=============================== StdErr Messages: ===============================

No errors were reported.
```

---

### Post by jcsaintpo on 2009-01-04
after reading output, should I do this?

```
  mount -t ntfs-3g /dev/sda1 sda1 -o remove_hiberfile

```

---

### Post by caljohnsmith on 2009-01-04
> **jcsaintpo said:**
> after reading output, should I do this?

```
  mount -t ntfs-3g /dev/sda1 sda1 -o remove_hiberfile

```
Yes, give that a try, and don't forget to put a "sudo" in front of it. Let me know if that successfully mounts your sda1 partition.

---

### Post by jcsaintpo on 2009-01-04
> **caljohnsmith said:**
> Yes, give that a try, and don't forget to put a "sudo" in front of it. Let me know if that successfully mounts your sda1 partition.

this was unfortunate responce

```
fuse: failed to access mountpoint sda1: Bestand of map bestaat niet

```

---

### Post by caljohnsmith on 2009-01-04
OK, I think I see the problem, how about instead doing:
```
sudo mount -t ntfs-3g /dev/sda1 /mnt -o remove_hiberfile && ls -l /mnt
```
And please post the output.

---

### Post by jcsaintpo on 2009-01-04
> **caljohnsmith said:**
> OK, I think I see the problem, how about instead doing:
```
sudo mount -t ntfs-3g /dev/sda1 /mnt -o remove_hiberfile && ls -l /mnt
```
And please post the output.

Can I kiss you? :-)))))))))))))))

---

