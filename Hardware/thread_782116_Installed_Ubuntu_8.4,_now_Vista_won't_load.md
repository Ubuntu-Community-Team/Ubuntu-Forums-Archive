---
title: "Installed Ubuntu 8.4, now Vista won't load"
date: 2008-05-04
forum: Hardware
---

### Post by mxpxmx3x on 2008-05-04
Not that the lack of Vista is a huge issue or anything, but I need to load Vista to run some of my other programs that don't work with Wine.

Anyways, I installed Ubuntu 8.4 the other day on my Dell Inspiron E1505 Notebook which had Vista pre-installed on it. I wanted to go with the multi-os, but it looks like the Vista boot is missing. I have already tried using the Super Grub disk, but that actually made matters worse. I have also used the Vista CD, but that didn't help at all. I have also edited my menu.lst file to include my Vista boot info, but that didn't work either.

I can still access all of my files in the /media/disk/ directory, so my files are all still there.

I know there are solutions for this issue, and I have searched many forums for a solution, but nothing has worked.

Partition info:
```

Disk /dev/sda: 78.5 GB, 78518522880 bytes
255 heads, 63 sectors/track, 9546 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1           6       48163+   6  FAT16
/dev/sda2               7        9112    73143945    f  W95 Ext'd (LBA)
/dev/sda4            9113        9545     3478072+  db  CP/M / CTOS / ...
/dev/sda5               7        6888    55279633+   7  HPFS/NTFS
/dev/sda6            7168        9112    15623181   83  Linux
/dev/sda7            6889        7167     2241036   82  Linux swap / Solaris

```

---

### Post by mxpxmx3x on 2008-05-04
Bump...

---

### Post by jimv on 2008-05-04
Can you post the contents of boot.ini from windows and menu.list from ubuntu?

---

### Post by mxpxmx3x on 2008-05-04
> **jimv said:**
> Can you post the contents of boot.ini from windows and menu.list from ubuntu?
Well, I actually didn't find boot.ini anywhere on my system.

Here is my menu.lst file

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
# kopt=root=UUID=c401a3af-6713-4929-b690-a175f2231d92 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=c401a3af-6713-4929-b690-a175f2231d92 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=c401a3af-6713-4929-b690-a175f2231d92 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Dell Utility Partition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda4
title		Windows NT/2000/XP
root		(hd0,3)
savedefault
makeactive
chainloader	+1

```

---

### Post by mxpxmx3x on 2008-05-04
FYI - Whenever I select "Windows NT/2000/XP" from the main menu, it loads the Symantec Recovery Tool.

The problem I had with the super grub disk, was it made it boot directly into the Symantec Recovery Tool instead of Vista. Then I was screwed because I couldn't even boot Linux.

---

### Post by jimv on 2008-05-04
OK, I just had to read up on Vista's boot loader.  Apparently it doesn't use boot.ini anymore.  I think the problem is with Vista's loader, not grub.  There an app called Windows Vista Boot Pro that will allow you to verify/edit Vista's boot info, but it's for XP.

I think it will run under Wine, but you need to use WineTricks to install .Net Framework 2.0 first.

The page I saw about the Windows Vista Boot Pro tool is here:
[http://www.ghacks.net/2006/12/15/how-to-repair-the-vista-bootloader/](http://www.ghacks.net/2006/12/15/how-to-repair-the-vista-bootloader/)

You can get WineTricks here:
[http://www.kegel.com/wine/winetricks](http://www.kegel.com/wine/winetricks)

- Copy the text on that page into a text file and call it "winetricks"
- To run wintricks, open a terminal, go to wherever you saved the file, and type 'sh winetricks' 
- A little dialog pops up and you can check .Net Framwork 2.0 and click Install

Once you have that done, trying using the Windows Vista Boot Pro tool and follow that guy's instructions.

---

### Post by mxpxmx3x on 2008-05-04
> **jimv said:**
> OK, I just had to read up on Vista's boot loader.  Apparently it doesn't use boot.ini anymore.  I think the problem is with Vista's loader, not grub.  There an app called Windows Vista Boot Pro that will allow you to verify/edit Vista's boot info, but it's for XP.

I think it will run under Wine, but you need to use WineTricks to install .Net Framework 2.0 first.

The page I saw about the Windows Vista Boot Pro tool is here:
[http://www.ghacks.net/2006/12/15/how-to-repair-the-vista-bootloader/](http://www.ghacks.net/2006/12/15/how-to-repair-the-vista-bootloader/)

You can get WineTricks here:
[http://www.kegel.com/wine/winetricks](http://www.kegel.com/wine/winetricks)

- Copy the text on that page into a text file and call it "winetricks"
- To run wintricks, open a terminal, go to wherever you saved the file, and type 'sh winetricks' 
- A little dialog pops up and you can check .Net Framwork 2.0 and click Install

Once you have that done, trying using the Windows Vista Boot Pro tool and follow that guy's instructions.
I did this, but I got this error message:

```


100%[====================================>] 5,746,895    390.34K/s    ETA 00:00

18:11:24 (366.79 KB/s) - `wine_gecko-0.1.0.cab' saved [5746895/5746895]

Executing cabextract /home/greg/.winetrickscache/wine_gecko-0.1.0.cab
winetricks: 1209: cabextract: not found
Note: command 'cabextract /home/greg/.winetrickscache/wine_gecko-0.1.0.cab' returned status 127.  Aborting.


```

---

### Post by fmartinez on 2008-05-04
> **mxpxmx3x said:**
> 

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Dell Utility Partition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda4
title		Windows NT/2000/XP
root		(hd0,3)
savedefault
makeactive
chainloader	+1
[/code]


On this part in your menu.lst page: try changing 
root             (hd0,3)  =>  root       (hd0,"the drive your Windows partition is on")

So basically your telling Grub that the boot partition for Windows in on hd0 (hard disk 0) partition 3. 

This should let you boot into the Windows partition of your hard disk. 

REMEMBER TO BACK UP YOUR "MENU.LST" FILE, AND YOU CAN ALWAYS BOOT INTO A LIVE CD TO RE-EDIT THIS FILE IF YOU RUN INTO PROBLEMS.
GOOD LUCK.

---

### Post by mxpxmx3x on 2008-05-04
> **fmartinez said:**
> On this part in your menu.lst page: try changing 
root             (hd0,3)  =>  root       (hd0,"the drive your Windows partition is on")

So basically your telling Grub that the boot partition for Windows in on hd0 (hard disk 0) partition 3. 

This should let you boot into the Windows partition of your hard disk. 

REMEMBER TO BACK UP YOUR "MENU.LST" FILE, AND YOU CAN ALWAYS BOOT INTO A LIVE CD TO RE-EDIT THIS FILE IF YOU RUN INTO PROBLEMS.
GOOD LUCK.
It says I don't have permission to save/backup menu.lst

---

### Post by jrbush82 on 2008-05-04
You'll need to edit the file with escalated privileges.  For example:

In the shell, type: "sudo vi menu.lst"

This will load the vi editor with the file menu.lst and also with escalated privileges.  If you don't like to use vi, you might try pico.

---

### Post by jimv on 2008-05-04
YOu need to install cabextract.  Type this in a terminal

sudo apt-get install cabextract

---

### Post by mxpxmx3x on 2008-05-05
> **jimv said:**
> YOu need to install cabextract.  Type this in a terminal

sudo apt-get install cabextract
What do I need that for?

---

### Post by frodon on 2008-05-05
mxpxmx3x, your partition number for vista might be wrong in your menu.lst, What is the the partition number of your vista partition sda5 ?

---

### Post by jimv on 2008-05-05
Because when you tried to run WIne, it said you needed cabextract to extract the file.

---

### Post by mxpxmx3x on 2008-05-05
> **frodon said:**
> mxpxmx3x, your partition number for vista might be wrong in your menu.lst, What is the the partition number of your vista partition sda5 ?
I don't know, how do I find that information?

---

### Post by frodon on 2008-05-05
You don't know the size and type of your windows partition ?

From what i see from your fdisk -l command i would say the NTFS partition (sda5) is your windows partition so in this case your windows part in your menu.lst file should look like that :
```
title Windows NT/2000/XP
root (hd0,[COLOR="Red"]**4**[/COLOR])
savedefault
makeactive
chainloader +1
```Even if you are not sure you can try it, it won't break anything.

---

### Post by mxpxmx3x on 2008-05-05
> **frodon said:**
> You don't know the size and type of your windows partition ?

From what i see from your fdisk -l command i would say the NTFS partition (sda5) is your windows partition so in this case your windows part in your menu.lst file should look like that :
```
title Windows NT/2000/XP
root (hd0,[COLOR="Red"]**4**[/COLOR])
savedefault
makeactive
chainloader +1
```Even if you are not sure you can try it, it won't break anything.
Okay, cool. I will give that a try.

My Vista partition is the one with ~56GB of space.

---

### Post by mxpxmx3x on 2008-05-05
I still can't edit my menu.lst file. I tried switching to the root user, but I don't remember setting a password for it.

---

### Post by mxpxmx3x on 2008-05-05
> **frodon said:**
> You don't know the size and type of your windows partition ?

From what i see from your fdisk -l command i would say the NTFS partition (sda5) is your windows partition so in this case your windows part in your menu.lst file should look like that :
```
title Windows NT/2000/XP
root (hd0,[COLOR="Red"]**4**[/COLOR])
savedefault
makeactive
chainloader +1
```Even if you are not sure you can try it, it won't break anything.
I changed my root password, and edited my menu.lst file, but it didn't work.

I keep getting this message:
```

Error 12: Invalid Device Requested
Press any key

```

---

### Post by frodon on 2008-05-06
Then first thing to try is to reinstall GRUB from live CD to exclude any GRUB install issue :
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoverGrub#head-7e18706bb1b3e5c3e4d3d8699471ec0e7b4023c4](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoverGrub#head-7e18706bb1b3e5c3e4d3d8699471ec0e7b4023c4)

---

### Post by silver on 2008-05-06
Just curious but did you install Vista or was it the original Dell installation ? The reason I ask is they use a variant of Ghost on their systems which they refer to as PC Restore. Even if you deleted the partition, the bootloader would still have references for it.

---

### Post by mxpxmx3x on 2008-05-06
> **silver said:**
> Just curious but did you install Vista or was it the original Dell installation ? The reason I ask is they use a variant of Ghost on their systems which they refer to as PC Restore. Even if you deleted the partition, the bootloader would still have references for it.

It came with Vista already on it, but I already had to re-install Vista since I bought the computer.

---

