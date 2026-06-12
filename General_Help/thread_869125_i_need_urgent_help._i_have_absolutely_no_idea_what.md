---
title: "i need urgent help. i have absolutely no idea what to do now"
date: 2008-07-24
forum: General Help
---

### Post by entrancetolight on 2008-07-24
Hi everyone. I'm new to Ubuntu and am already having problems
i installed ubuntu 8.04 and now can't seem to boot into vista.
my menu.lst. file is blank when open it.
if i use terminal and the command "sudo fdisk -l"
it shows 

  Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6        1311    10485760    7  HPFS/NTFS
/dev/sda3            1311       24108   183116800    7  HPFS/NTFS
/dev/sda4           24108       30394    50495261+   f  W95 Ext'd (LBA)
/dev/sda5           24108       30133    48397312   83  Linux
/dev/sda6           30134       30394     2096451   82  Linux swap / Solaris


this means my vista partition is still there untouched right?
however i tried to manually repair the vista bootloader by entering the commands found on this site 
[http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD)


i used the command prompt from a windows recovery disk 
which displayed something like:

x:source/
i completed all the commands except x:\boot\bootsect.exe /nt60 all/force
but after rebooting i received a message saying that "boot mgr is missing
press ctrl+alt+del to continue"
i'm currently stuck with ubuntu and face the grub screen everytime i boot the pc

my drives were originally C:OS (the drive with Vista installed) approx.183 GB and a D:Recovery approx. 10GB
dev/sda5 and 6 are the Ubuntu Linux partitions i created in vista and a free space swap file
dev/sda1 appears to be a dell utility partition
but now, when i insert the windows recovery cd it shows that disk C is labeled Recovery

PLEASE CAN ANYONE HELP ME?

---

### Post by Potatoj316 on 2008-07-24
It looks like you still have all your vista stuff.  Are you sure your menu.lst file is nonexistant?  I dont think you can use grub if you dont have one.  try 
```
gedit /boot/grub/menu.lst
```
you might need a sudo infront of that

---

### Post by entrancetolight on 2008-07-24
okay i see now.
it works but you don't need the sudo-fix in front
is it possible now to boot back into vista?
in the computer menu; it does not display the hard drive where vista is installed.
also the disk where vista was originally installed is now C:Recovery instead of C:OS
and the OS seems to be on Local Disk D.
i would like to boot into vista to wipe out the ubuntu partition and restore it back to the preinstall of Ubuntu
advice anyone?

---

### Post by Potatoj316 on 2008-07-24
post this command```
fdisk -l
```also post your menu.lst (actually just the bottom part is ok where it starts listing the grub boot menu options)

---

### Post by tamoneya on 2008-07-24
> **Potatoj316 said:**
> post this command```
fdisk -l
```also post your menu.lst (actually just the bottom part is ok where it starts listing the grub boot menu options)

fdisk -l requires sudo.  Also he already posted in his first post.  It would be nice though if we could take a look at menu.lst now that you have found it.  Note that while you dont need sudo to read menu.lst you will need to use sudo (gksudo would be better since gedit is graphical) in order to write to menu.lst when we make some edits.

---

### Post by 47_MasoN_47 on 2008-07-24
My desktop was setup with 2 hard drives (1 WinXP and 1 WinVista).  I formatted the XP drive and installed Ubuntu.  It didn't detect the Vista hard drive automatically.  I had to manually add ```
title = Windows Vista x64
root hd(1,0)
makeactive
chainloader +1
```
to menu.lst in order for Vista to boot.

I had to add it above the section where the Ubuntu ones are.  I believe it's called the automatically detected section or something to that effect.  It wouldn't boot Vista if I added the entry there, but if I put it above that it worked fine.

---

### Post by entrancetolight on 2008-07-24
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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

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
# kopt=root=UUID=347d865e-2ae7-4459-8d69-95f95efc9828 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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

title        Ubuntu 8.04.1, kernel 2.6.24-19-generic
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=347d865e-2ae7-4459-8d69-95f95efc9828 ro quiet splash
initrd        /boot/initrd.img-2.6.24-19-generic
quiet

title        Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=347d865e-2ae7-4459-8d69-95f95efc9828 ro single
initrd        /boot/initrd.img-2.6.24-19-generic

title        Ubuntu 8.04.1, memtest86+
root        (hd0,4)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Dell Utility Partition
root        (hd0,0)
savedefault
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title        Windows Vista/Longhorn (loader)
root        (hd0,2)
savedefault
chainloader    +1
```

---

### Post by entrancetolight on 2008-07-24
i only have one hard drive that was orginally partitioned as 
C: OS (the one with windows vista installed) approx 183 GB
D: Recovery (a Dell partition backup, i think that came with the orginal PC) 10 GB

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6        1311    10485760    7  HPFS/NTFS
/dev/sda3            1311       24108   183116800    7  HPFS/NTFS
/dev/sda4           24108       30394    50495261+   f  W95 Ext'd (LBA)
/dev/sda5           24108       30133    48397312   83  Linux
/dev/sda6           30134       30394     2096451   82  Linux swap / Solaris
```

but now Drive C appears to be labeled the Recovery disk, where Vista is in and D, is the Local Disk.This might have been the result of attempting to fix the Vista boot loader.
Can anyone make any sense of this, and try to help me return to the original configuration? Thanks

---

### Post by bodhi.zazen on 2008-07-24
> **entrancetolight said:**
> PLEASE CAN ANYONE HELP ME?

Your /boot/grub/menu.lst looks fine, what happens when you boot Vista ?

We may need to change to 

root (hd0,1)

---

### Post by entrancetolight on 2008-07-24
how do you change to root (hdO,1)
i am totally new to ubuntu and would like to have step by step instructions if thats possible.

my original configuration of my drives are listed in my previous postings.
i am unable to boot Vista even though the Windows Vista/Longhorn loader is listed
if i select the Vista loader, a small loading screen with the message "grub loading up to stage 2" appears briefly then it returns to the Grub menu.
if i select the "other operating systems" option; i get an error message. the error message says "error 11 unrecognized device string"

---

### Post by bodhi.zazen on 2008-07-24
Boot Ubuntu

Open a terminal

```
gksu gedit /boot/grub/menu.lst
```

Edit your window enteries. You should delete all but one, make it look like this :

> # This entry is for Vista
# on /dev/sda2
title        Windows Vista/Longhorn (loader)
root        (hd0,1)
savedefault
chainloader    +1

Reboot, should work.

---

### Post by entrancetolight on 2008-07-25
actually i reinstalled Ubuntu Linux this time choosing the default bootloader and the bootloader works now..but Windows won't boot. I used a Windows Recovery CD to try and see if it could repair it but it doesn't. I get a Windows Boot Manager error when i try to boot Vista. It says the the hal.dll is missing. I think this was the result of an attempt to manually fix the Vista bootloader using "Step Four" on this website
[http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD)

Unfortunately i think i forgot to enter the command 
"x:\boot\bootsect.exe /nt 60 all /force"  and as result Vista (C:) seems to be in the (D:) Recovery partition of my drive rather than the OS.I suspect that more than one driver is missing. Can anyone give me advice on how to access my Windows partitions or at least recover data from them? I get a message that says 
"System policy prevents from mounting internal media" when i try to open the Recovery partition. However, the important Windows files are now in "Local Disk D"
and that drive is not visible in the Places>Computer but i believe still exists because of "sudo fdisk -l"

```
Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6        1311    10485760    7  HPFS/NTFS
/dev/sda3            1311       24108   183116800    7  HPFS/NTFS
/dev/sda4           24108       30394    50495261+   f  W95 Ext'd (LBA)
/dev/sda5           24108       30133    48397312   83  Linux
/dev/sda6           30134       30394     2096451   82  Linux swap / Solaris
normanquitelikeyou@ARMIN:~$
```

dev/sda1=Dell Diagnostics Utility
dev/sda2=originally D:Recovery, but now Local Disk D
dev/sda3=originally C:OS, but now C:Recovery
dev/sda4-6=Ubuntu partition
i think that dev/sda2 is the that's being booted, is there a way to change that back to dev/sda3?

---

### Post by tamoneya on 2008-07-25
you shouldnt be booting /dev/sda3.  The boot partition for windows is /dev/sda2 as shown by the boot flag (the "*").  hal.dll is a windows issue now.  Previously there were some problems with grub (hd0,2) instead of (hd0,1). Now however windows is being told to boot correctly but is failing.  Try the windows CD again now that you have grub sorted out.

---

### Post by Ender305 on 2008-07-25
try manually mounting the vista partition, I think its something along the lines of
```

sudo mkdir /media/vista_hdd
sudo mount /dev/sda3 /media/vista_hdd

```

---

### Post by entrancetolight on 2008-07-25
```
normanquitelikeyou@ARMIN:~$ sudo mkdir /media/vista_hdd
[sudo] password for normanquitelikeyou: 
normanquitelikeyou@ARMIN:~$ sudo mkdir /media/vista_hdd
mkdir: cannot create directory `/media/vista_hdd': File exists
normanquitelikeyou@ARMIN:~$ sudo mount /dev/sda3 /media/vista_hdd
mount: you must specify the filesystem type
normanquitelikeyou@ARMIN:~$
```

those are the responses i got when entering the specified code from one of the postings. what filesystem type do i specify? 

and to a response; the asterik does show which partition boots; however 
originally it is dev/sda3 that has vista , approx 180GB and that's the one that's supposed to boot.Now, probably due to a mistake i made in trying to manually restore the Vista bootloader (using the instructions at this website, 

[http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD)

,i think i might have changed the partition that boots Vista to dev/sda2 which is supposed to be a recovery disk that is 10 GB. Is there any way to undo this?

---

