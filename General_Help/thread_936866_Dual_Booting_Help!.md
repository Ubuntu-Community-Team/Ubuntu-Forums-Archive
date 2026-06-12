---
title: "Dual Booting Help!"
date: 2008-10-03
forum: General Help
---

### Post by brookswm on 2008-10-03
Alright, I'm nearly at my ropes end with trying to get Ubuntu to be my default hard drive on start up.  I've tried many things, downloading 'start up manager' and editing my menu.lst.  No matter what I do my computer starts back up in Windows XP.  My computer has 2 hard drives, it came with WinXP preloaded and just recently I decided to try out Ubuntu and so I installed it on the second hard drive.  I'm starting to think that I'm going to have do something in Windows to get Ubuntu to be my primary OS.

Here is my menu.lst file for good measure, no matter how I change it, it always reverts back to this:

> 
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
**default		0 (Set to 0, which is Ubuntu)**

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=DAD82ABED82A9931 loop=/ubuntu/disks/root.disk ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=()/ubuntu/disks

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
# defoptions=quiet splash vga=771

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=DAD82ABED82A9931 loop=/ubuntu/disks/root.disk ro quiet splash vga=771
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=DAD82ABED82A9931 loop=/ubuntu/disks/root.disk ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		()/ubuntu/disks
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Home Edition
root		(hd0,1)
**savedefault  (I have deleted this)**
chainloader	+1


---

### Post by caljohnsmith on 2008-10-03
It looks like you did a Wubi install to install Ubuntu inside Windows? So when you start up, you don't get a Windows boot menu that allows you to choose between Windows or Ubuntu? Also, how did you access the menu.lst you posted? Which partition is it on? 

Please post the following:
```
sudo fdisk -l
```
And we can go from there.

---

### Post by brookswm on 2008-10-03
I do get the choice of booting into WinXP or Ubuntu, but I like to start my computer, get a drink, use the toilet, do a jig, compose a novelette and then come back once it has started up.  I accessed the menu.lst by using the terminal, following instructions I found in a different thread about the same subject.  I believe that it is located on the 2nd hard drive on the Ubuntu partition... does that make sense? 
And the results are in:

> 
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6        9725    78075900    7  HPFS/NTFS

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000081

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4862    39053983+   7  HPFS/NTFS


---

### Post by Shazaam on 2008-10-03
According to fdisk Ubuntu isn't there (has no partition). Are you sure you didn't do a WUBI (done while running Windows) install? Or did you set your pc up so it boots from cd and then install Ubuntu using the livecd?

---

### Post by ster1988 on 2008-10-03
I just installed last night with vista, and basically what did when i was installing, was i installed grub on the main partition of ubuntu and then when i restarted it loaded vista. Then all i did was download a program called Easy bcd and added the partition to the boot list and everything works great. i dont know if this is what you are looking to do or not if you have any questions let me know.

---

### Post by brookswm on 2008-10-03
> **Shazaam said:**
> According to fdisk Ubuntu isn't there (has no partition). Are you sure you didn't do a WUBI (done while running Windows) install? Or did you set your pc up so it boots from cd and then install Ubuntu using the livecd?

I downloaded Ubuntu from the site and installed it while running windows, so I guess I did do a WUBI install.

---

### Post by Shazaam on 2008-10-04
> **brookswm said:**
> I downloaded Ubuntu from the site and installed it while running windows, so I guess I did do a WUBI install.

Thats fine. You can make a WUBI install into a regular hard drive install so you don't loose all of your goodies later. There is a WUBI subforum here; you might poke around there if you need more help.

---

### Post by brookswm on 2008-10-04
I followed the instructions in the Wubi form and my last query changed to this:

> 
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   83  Linux
/dev/sda2   *           6        9725    78075900    7  HPFS/NTFS

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000081

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4862    39053983+   7  HPFS/NTFS


If I am reading it correctly, it now has the Linux partition.  I have re-edited menu.lst and tried to use the startupmanager program... WinXP is still the first STD on my list of boot devices.

I'll add this for good measure:

> 
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=DAD82ABED82A9931 loop=/ubuntu/disks/root.disk ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=()/ubuntu/disks

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
# defoptions=quiet splash vga=775

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
# updatedefaultentry=true

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=DAD82ABED82A9931 loop=/ubuntu/disks/root.disk ro quiet splash vga=775
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=DAD82ABED82A9931 loop=/ubuntu/disks/root.disk ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		()/ubuntu/disks
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Home Edition
root		(hd0,1)
chainloader	+1



title Ubuntu-on-/dev/sda1
root (hd0,0)
configfile /boot/grub/menu.lst


---

### Post by caljohnsmith on 2008-10-04
If you want to make Ubuntu be the default OS to boot on start up, the problem is that you have a Wubi install; with a Wubi install, Ubuntu is added to the Windows XP boot loader, so you are not booting into Grub directly on start up. That is why using Startup Manager and programs like that won't help you. I'm sure you could modify your Windows boot.ini file (the Windows boot menu file) so that you could make Ubuntu boot by default and not Windows. But if you can, I would personally recommend you just repartition either your sda or sdb drive so that you can install Ubuntu to its own partition as a dual-boot. I've had too many problems with Wubi to recommend using it, so I try to encourage others to do the traditional "give Ubuntu its own partition" method. 

If you really don't want to give Ubuntu its own partition, I'm sure we can modify your boot.ini file to boot Ubuntu first. Let me know what you want to do and we can work from there.

---

### Post by brookswm on 2008-10-04
I guess I will wait until the CD that I requested comes.  I dont mind reinstalling because it'll reinforce how to do things in Ubuntu.  I hope it arrives soon.

---

### Post by Nero60 on 2008-10-14
Can you please tell me how to make Ubuntu first using the Windows Boot.  I would really appreciate it since I can't seem to utilize Ubuntu in a seperate partition.  Seems not to work with ATI Graphics Card.  It starts to load and then the screen goes black and nothing happens.  However, when I boot under Windows, it works fine.  Thanks in advance!

---

### Post by caljohnsmith on 2008-10-14
Nero60, you'll need to modify your Wndows boot.ini file to make Ubuntu the default OS to boot, if that is what you are asking for. Your boot.ini should look similar to:
```
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn
C:\wubildr.mbr="Ubuntu"
```
You'll need to change the "default" line to:
```
[boot loader]
timeout=[COLOR="Blue"]30[/COLOR]
[COLOR="Blue"]default=C:\wubildr.mbr[/COLOR]
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn
C:\wubildr.mbr="Ubuntu"
```
Note you can also change the "timeout" line above to however many seconds you want the boot loader to wait before it boots the default OS, which will be Ubuntu. If you don't know how to modify your boot.ini file, you can follow [Herman's guide]("http://users.bigpond.net.au/hermanzone/p9.html") to do it within Windows.

---

### Post by Nero60 on 2008-10-15
I followed your suggestion and went to Herman's guide.  I followed the instructions and received an error msg. indicating that boot.ini did not exist.  I listed what was on the C: drive and found no Boot reference.

---

### Post by caljohnsmith on 2008-10-15
Well you could modify your boot.ini from your Live CD. From your Live CD, open a terminal (applications > accessories > terminal), and do:
```
sudo fdisk -lu

```
Find which is your Windows partition by noticing it should be either NTFS or FAT32 file system, and it will probably be partition sda1. Next mount it, print the root directory and the contents of boot.ini:
```
mount /dev/sda1 /mnt
ls -l /mnt
cat /mnt/boot.ini
```
Note the "-l" is a lowercase L, not a one, and change the "sda1" above if your Windows is on a different partition. Please post the output of all the above commands. :)

---

### Post by Nero60 on 2008-10-15
This is the output from sudo fdisk -lu

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xea4fea4f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1           16065    81915434    40949685    f  W95 Ext'd (LBA)
/dev/sda2   *    81915435   488392064   203238315    7  HPFS/NTFS
/dev/sda5           16128    81915434    40949653+   7  HPFS/NTFS

Being really new at this, I am not sure how to mount NTFS file system?

---

### Post by caljohnsmith on 2008-10-15
OK, from the Live CD, post the output of:
```
sudo mount /dev/sda2 /mnt
ls -l /mnt
cat /mnt/boot.ini
```
Also, do you have internet access from your Live CD?

---

### Post by TeXtonyx on 2008-10-15
What program did you use to edit boot.ini? Once upon a time I used Notepad to
edit boot.ini and I made a small correction and saved it. Well, I hadn't changed the
Notepad default configuration. It is set to save as .txt so it appends a .txt extension
to the file automatically. One has to change Notepad to "all files" in order to save
boot.ini as boot.ini or else it will save it as boot.ini.txt

So of course my Windows machine wouldn't boot because it couldn't find boot.ini.
Such a small thing wasn't that easy to fix because Windows went into that mode
where it shows a bunch of options which include last good configuration and start
Windows normally. On my system this locked out mounting Windows from Linux.

Eventually, I had to use UBCD cd which let me enter the Windows C:\ partition.
From the Dos prompt I typed: C:\copy boot.ini.txt boot.ini <enter>
When I rebooted it worked. If you have a backup of boot.ini , boot.ini.bak 
then C:\copy boot.ini.bak boot.ini restores the original boot.ini before it was edited.
You might have to rename, C:\ren boot.ini boot.ini.Edited first before this will work 
though if you get an error message at the step of  C:\copy boot.ini.bak boot.ini 

Just thought I would mention this just in case you used Notepad to edit boot.ini
I saw a copy of your boot.ini so I'm looking for what could have changed it so 
that the OS can't find it anymore. Changing the .ext will do that, boot.ini.txt

---

### Post by Nero60 on 2008-10-17
The Following is the result of ls -l /mnt after mounting sda2:  

total 2161
drwxrwxrwx 1 root root       0 2008-09-16 13:57 0e467daecda755357b4f6ab94285d7
drwxrwxrwx 1 root root       0 2006-11-20 08:46 7eb4bb1f7f567ee7e9d3f63c72a763
drwxrwxrwx 1 root root       0 2008-09-16 13:41 ad781518d2145304e635161e6e09
-rwxrwxrwx 1 root root     236 2008-09-26 16:28 boot.ini
-rwxrwxrwx 1 root root 1700352 2001-09-05 21:00 gdiplus.dll
-rwxrwxrwx 1 root root   47564 2007-10-08 14:11 NTDETECT.COM
-rwxrwxrwx 1 root root  250032 2007-10-08 14:11 ntldr
drwxrwxrwx 1 root root       0 2007-10-08 13:07 RECYCLER
drwxrwxrwx 1 root root    4096 2004-12-21 13:11 System Volume Information
-rwxrwxrwx 1 root root  188547 2008-06-30 11:30 wubildr
-rwxrwxrwx 1 root root    8192 2008-06-30 11:30 wubildr.mbr

This is the output of cat /mnt/boot.ini


[boot loader]
timeout=15
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn
c:\wubildr.mbr="Ubuntu"

I do have internet access from Ubuntu.

Thanks again for your help!

---

### Post by caljohnsmith on 2008-10-17
Great, so first make sure you can download and install the package "tofrodos" as that will help ensure the following directions work:
```
sudo apt-get install tofrodos
```
So only proceed if the above command successfully installs that package. Next, mount sda2 again (in case you are still not running the same session), make a backup of boot.ini, and edit it with:
```
sudo mount /dev/sda2 /mnt
sudo cp /mnt/boot.ini /mnt/boot.ini.backup
gksudo gedit /mnt/boot.ini
```
Then change the default line in your boot.ini as follows:
```
[boot loader]
timeout=15
default=[COLOR="Blue"]C:\wubildr.mbr[/COLOR]
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Micro soft Windows XP Home Edition" /fastdetect /NoExecute=OptIn
c:\wubildr.mbr="Ubuntu"
```
That will make Ubuntu the default entry to boot after the 15 second delay that is set on the "timeout" line (you can change that if you wish). Save, quit gedit, and do the following to ensure that the boot.ini file has NTFS style line endings for all lines:
```
unix2dos /mnt/boot.ini
```
To explain a little, Unix/Linux uses only a line feed at end of lines, whereas Windows (NTFS/DOS) uses a carriage return + line feed; so if you look at a text file in Windows that was created with gedit, it will appear as one long line (no end of lines). Therefore "unix2dos" makes sure all the end of lines in your boot.ini are NTFS style and not Linux style. 

Let me know how it goes, or if you run into problems. :)

---

### Post by Nero60 on 2008-10-18
You are great!!  It is working just fine now and I really appreciate your help.  Learning alot about the OS.

One last question.  I don't know if you can answer but I have Ubuntu on my laptop and have been using it almost exclusively for a year.  Since I recently installed Ubuntu on my desktop I noticed that the laptop desktop configuration has 4 optional screens to utilize.  The configuration on the desktop only has 2.  Is this a function of operating the desktop under windows?  The laptop has Ubuntu on a seperate partition.

Again, thanks for all your help.

---

### Post by caljohnsmith on 2008-10-18
> **Nero60 said:**
> You are great!!  It is working just fine now and I really appreciate your help.  Learning alot about the OS.

One last question.  I don't know if you can answer but I have Ubuntu on my laptop and have been using it almost exclusively for a year.  Since I recently installed Ubuntu on my desktop I noticed that the laptop desktop configuration has 4 optional screens to utilize.  The configuration on the desktop only has 2.  Is this a function of operating the desktop under windows?  The laptop has Ubuntu on a seperate partition.

Again, thanks for all your help.
That's great that it defaults to Ubuntu now. :) When you say four optional screens to use, do you mean by clicking the little buttons on the bottom of the screen on the panel to switch between desktops? If so, I know you can change how many desktop spaces there are, but I can't remember at the moment how to do it in Gnome as I've been using KDE 3.5 for a while instead of Gnome; sorry I can't help on that, you'll have to ask someone else. :)

---

