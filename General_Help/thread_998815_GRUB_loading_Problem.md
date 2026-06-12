---
title: "GRUB loading Problem"
date: 2008-12-01
forum: General Help
---

### Post by sundarrajan on 2008-12-01
I have my system installed with both Windows XP as well as Ubuntu 8.04 installed...When i switch on my system Grub loads it produces a list about which either Ubuntu or Windows XP u want to boot...
I got a serious problem in Windows XP hence i reinstalled it..
i have not made any changes to the Space allocated to Ubuntu during Windows Install.. but my Ubuntu is not loading now .. i cannot able to see the list of OS nowadays   Give me a solution i Need Ubuntu in my system ......
Help.......:(:(:(

---

### Post by __Ryan__ on 2008-12-01
Windows overwrote GRUB in your MBR.  You need to reinstall it.

Take a look at this walkthrough. Your going to have to use an Ubuntu LiveCD.


[http://www.wiredrevolution.com/system-administration/install-the-grub-boot-loader-to-the-mbr]("http://www.wiredrevolution.com/system-administration/install-the-grub-boot-loader-to-the-mbr")

---

### Post by taurus on 2008-12-01
> **__Ryan__ said:**
> Windows overwrote GRUB in your MBR.  You need to reinstall it.

Take a look at this walkthrough. Your going to have to use an Ubuntu LiveCD.


[http://www.wiredrevolution.com/system-administration/install-the-grub-boot-loader-to-the-mbr]("http://http://www.wiredrevolution.com/system-administration/install-the-grub-boot-loader-to-the-mbr")

The link has an extra http:// at the beginning.  Here is another tutorial on how to recover GRUB.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by ajgreeny on 2008-12-01
And here is a note I produced a while ago with a bit more background to what is going on, still very simple to follow, however.

Boot into the ubuntu live CD
open a terminal and run :
    ```
sudo grub
```
This gets you to a simple grub command line.
Then:
   ```
 find /boot/grub/stage1
```
This will tell you where your /boot/grub/stage1 is which is needed to boot ubuntu. Replace the question marks in the following command with the output of the this last command :
   ```
 root (hd?,?)
```
[like : root (hd0,1) ,probably]
then:
    ```
setup (hd0)
```
This, (hd0),  is where your windows partition and MBR normally is, but if you want grub on another disk, use hd1, etc as appropriate. It's much easier to use the windows MBR and then just change the default boot system later if others in the family demand windows boots by default.
Then:
    ```
quit
```
Finally reboot, and hopefully you will now have a working grub bootloader.

I hope that helps and does not confuse you even more than you are at the moment.

---

### Post by sundarrajan on 2008-12-07
> **ajgreeny said:**
> And here is a note I produced a while ago with a bit more background to what is going on, still very simple to follow, however.

Boot into the ubuntu live CD
open a terminal and run :
    ```
sudo grub
```
This gets you to a simple grub command line.
Then:
   ```
 find /boot/grub/stage1
```
This will tell you where your /boot/grub/stage1 is which is needed to boot ubuntu. Replace the question marks in the following command with the output of the this last command :
   ```
 root (hd?,?)
```
[like : root (hd0,1) ,probably]
then:
    ```
setup (hd0)
```
This, (hd0),  is where your windows partition and MBR normally is, but if you want grub on another disk, use hd1, etc as appropriate. It's much easier to use the windows MBR and then just change the default boot system later if others in the family demand windows boots by default.
Then:
    ```
quit
```
Finally reboot, and hopefully you will now have a working grub bootloader.

I hope that helps and does not confuse you even more than you are at the moment.



Yes i Got the GRUB Loading and OS Menu in the System but when i select the Menu Ubuntu 8.04 but it produces the Error Message

" Cannot Able to mount the Selected Partition"

Why its not loading the Ubuntu OS in my system

I did whatever u have told right!!!

Menu showing Ubuntu is not loading the OS


Please help me to recover my Ubuntu Os :(

---

### Post by sundarrajan on 2008-12-07
Yes i Got the GRUB Loading and OS Menu in the System but when i select the Menu Ubuntu 8.04 but it produces the Error Message

" Cannot Able to mount the Selected Partition"

Why its not loading the Ubuntu OS in my system

I did whatever u have told right!!!

Menu showing Ubuntu is not loading the OS


Please help me to recover my Ubuntu Os

---

### Post by sundarrajan on 2008-12-10
Yes Success I got the Ubuntu Menu i have successfully got ubuntu in 

My System.


Thank u!!!

Using the above command by inserting Live Cd does not cleared the problem.

Instead placing the commands at the Ubuntu Menu of the System Start up or 
Boot is successfully opening the required GRUB with Ubuntu!!!



Use this its Working !!!!:lolflag::lolflag::lolflag:

---

### Post by sundarrajan on 2009-03-31
:(:(:(


I again got a problem in Ubuntu !!!

as i have both windows and ubuntu in my system, i m in a tie to meet the same problem again....


I have updated my system with two harddisks 160 GB + 250 GB 

Latestly my windows XP os corrupted and its not getting in . hence i installed the Windows Os once again. and using the live cd i tried the commands which used before once again 

```

sudo grub

find /boot/grub/stage1

root hd(1,6)

setup(hd1)



```

but the grub is not reloaded and ubuntu menu is not coming .....

Please help me to recover my ubuntu or else atleast give me an idea to recover the data that are in documents and desktop of my Ubuntu!!!

Windows is always making problem out of me !!!

:confused::confused::confused:

---

### Post by sundarrajan on 2009-03-31
I again got a problem in Ubuntu !!!

as i have both windows and ubuntu in my system, i m in a tie to meet the same problem again....


I have updated my system with two harddisks 160 GB + 250 GB 

Latestly my windows XP os corrupted and its not getting in . hence i installed the Windows Os once again. and using the live cd i tried the commands which used before once again 


Code:
sudo grub

find /boot/grub/stage1

root hd(1,6)

setup(hd1)but the grub is not reloaded and ubuntu menu is not coming .....

Please help me to recover my ubuntu or else atleast give me an idea to recover the data that are in documents and desktop of my Ubuntu!!!

Windows is always making problem out of me !!!


but its in my hd(0,6) partition when i installed Ubuntu at first !!!

I recently installed wine in my ubuntu 
Is this problem is due to the wine software that i have installed 


Try at a better level to atleast catch up my data !!!

Its better i can able to recover the files in my ubuntu and after recovering it i can just go on reinstallation of ubuntu !!!

Help me as i am a buddy in ubuntu !!!



Advance thanks to 1 and all who reply an apt solution for my problem !!!:KS:KS:KS

---

### Post by Elfy on 2009-03-31
> **sundarrajan said:**
> :(:(:(


I again got a problem in Ubuntu !!!

as i have both windows and ubuntu in my system, i m in a tie to meet the same problem again....


I have updated my system with two harddisks 160 GB + 250 GB 

Latestly my windows XP os corrupted and its not getting in . hence i installed the Windows Os once again. and using the live cd i tried the commands which used before once again 

```

sudo grub

find /boot/grub/stage1

root hd(1,6)

setup(hd1)



```

but the grub is not reloaded and ubuntu menu is not coming .....

Please help me to recover my ubuntu or else atleast give me an idea to recover the data that are in documents and desktop of my Ubuntu!!!

Windows is always making problem out of me !!!

:confused::confused::confused:

Run the commands from the live cd and when you get errors paste them into a new post please.

Also run these and paste the results.

```
sudo fdisk -l
ls -l /dev/disk/by-uuid
```

---

### Post by sundarrajan on 2009-03-31
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5b72c83b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2       10200    81923467+   f  W95 Ext'd (LBA)
/dev/sda2   *       10201       20399    81923467+   7  HPFS/NTFS
/dev/sda3           20400       30401    80341065    7  HPFS/NTFS
/dev/sda5               2       10200    81923436    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcbb2cbb2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3917    31463271    7  HPFS/NTFS
/dev/sdb2            3918       19456   124817017+   f  W95 Ext'd (LBA)
/dev/sdb5            3918        7834    31463271    7  HPFS/NTFS
/dev/sdb6            7835        8488     5253223+   7  HPFS/NTFS
/dev/sdb7            8489       11610    25077433+  83  Linux
/dev/sdb8           11611       11751     1132551   82  Linux swap / Solaris
/dev/sdb9           11752       15668    31463271    7  HPFS/NTFS
/dev/sdb10          15669       19456    30427078+   7  HPFS/NTFS
ubuntu@ubuntu:~$ ls -l /dev/disk/by-uuid
total 0
lrwxrwxrwx 1 root root 10 2009-03-31 19:32 3254FB3754FAFD03 -> ../../sdb1
lrwxrwxrwx 1 root root 10 2009-03-31 19:32 3a867158-3dc2-468a-b958-0cc828a3a90c -> ../../sdb8
lrwxrwxrwx 1 root root 11 2009-03-31 19:32 4C00FF5200FF420E -> ../../sdb10
lrwxrwxrwx 1 root root 10 2009-03-31 19:32 7E8CF1D58CF187C3 -> ../../sdb5
lrwxrwxrwx 1 root root 10 2009-03-31 19:32 9668F0B168F090EB -> ../../sda5
lrwxrwxrwx 1 root root 10 2009-03-31 19:32 9A1005BB10059F7F -> ../../sda2
lrwxrwxrwx 1 root root 10 2009-03-31 19:32 abd15458-6774-4289-b537-94a1f67ed969 -> ../../sdb7
lrwxrwxrwx 1 root root 10 2009-03-31 19:32 B280FAFD80FAC73F -> ../../sdb9
lrwxrwxrwx 1 root root 10 2009-03-31 19:32 EC3879C138798AFA -> ../../sdb6
lrwxrwxrwx 1 root root 10 2009-03-31 19:32 F68C17948C174F0D -> ../../sda3
ubuntu@ubuntu:~$ 


```

:pthank u for u r reply i get these when i type the commands as you specifed and i think that u can get a idea with this about my system.


As i am new to ubuntu i cannot able to understand completely about this harddisk specification 

Guide me what i have to do further !!!:):)

---

### Post by sundarrajan on 2009-03-31
hi i have installed ubuntu in my system and later when i tried to install windows along with ubuntu the menu appearing for ubuntu failed.

i know some of the commands to use in order to recover the menu from the thread  

Please refer this [http://ubuntuforums.org/showthread.php?t=998815]("http://ubuntuforums.org/showthread.php?t=998815")


When i used those i got the following results

I need an expert in ubuntu to understand whats actually going on in my system. please help to recover my ubuntu that i have it before 


The result i obtained in my system for the given commands is 

```
grub> find /boot/grub/stage1
 (hd1,6)

grub> root (hd1,6)

grub> setup (hd1)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd1)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd1) (hd1)1+16 p (hd1,6)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

grub> 
```


Even though it seems success the menu that i needed for ubuntu startup is not available when i switch on my system.


Further the additional commands that represent my system harddisk are 


```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5b72c83b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2       10200    81923467+   f  W95 Ext'd (LBA)
/dev/sda2   *       10201       20399    81923467+   7  HPFS/NTFS
/dev/sda3           20400       30401    80341065    7  HPFS/NTFS
/dev/sda5               2       10200    81923436    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcbb2cbb2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3917    31463271    7  HPFS/NTFS
/dev/sdb2            3918       19456   124817017+   f  W95 Ext'd (LBA)
/dev/sdb5            3918        7834    31463271    7  HPFS/NTFS
/dev/sdb6            7835        8488     5253223+   7  HPFS/NTFS
/dev/sdb7            8489       11610    25077433+  83  Linux
/dev/sdb8           11611       11751     1132551   82  Linux swap / Solaris
/dev/sdb9           11752       15668    31463271    7  HPFS/NTFS
/dev/sdb10          15669       19456    30427078+   7  HPFS/NTFS
ubuntu@ubuntu:~$ ls -l /dev/disk/by-uuid
total 0
lrwxrwxrwx 1 root root 10 2009-03-31 19:32 3254FB3754FAFD03 -> ../../sdb1
lrwxrwxrwx 1 root root 10 2009-03-31 19:32 3a867158-3dc2-468a-b958-0cc828a3a90c -> ../../sdb8
lrwxrwxrwx 1 root root 11 2009-03-31 19:32 4C00FF5200FF420E -> ../../sdb10
lrwxrwxrwx 1 root root 10 2009-03-31 19:32 7E8CF1D58CF187C3 -> ../../sdb5
lrwxrwxrwx 1 root root 10 2009-03-31 19:32 9668F0B168F090EB -> ../../sda5
lrwxrwxrwx 1 root root 10 2009-03-31 19:32 9A1005BB10059F7F -> ../../sda2
lrwxrwxrwx 1 root root 10 2009-03-31 19:32 abd15458-6774-4289-b537-94a1f67ed969 -> ../../sdb7
lrwxrwxrwx 1 root root 10 2009-03-31 19:32 B280FAFD80FAC73F -> ../../sdb9
lrwxrwxrwx 1 root root 10 2009-03-31 19:32 EC3879C138798AFA -> ../../sdb6
lrwxrwxrwx 1 root root 10 2009-03-31 19:32 F68C17948C174F0D -> ../../sda3
ubuntu@ubuntu:~$
```


Please read it completely and give me an idea how to handle this problem and to recover my ubuntu !!!;););)

---

### Post by Sam Lars on 2009-03-31
It sounds like you're doing the instructions from [here ]("http://ubuntuforums.org/showthread.php?t=224351")right...
Could you use the LiveCD to copy your important data somewhere else and then reinstall?

---

### Post by Elfy on 2009-03-31
> Run the commands from the live cd and when you get errors paste them into a new post please.Please read the whole of a post when replying :)

If the grub reinstalls fails - what errrors do you get?

Also please make the terminal wider and run ls -l /dev/disk/by-uuid again please - I want the whole output, not a truncated one ;)

---

### Post by plucky on 2009-03-31
> grub> setup (hd1)

You have setup to boot GRUB from the MBR for your second hard drive.
When you boot,enter the BIOS (Delete or F8 or whatever the startup screen says) and select the second hard drive as the boot device and see if you then get the Grub menu.

I am assuming that you when you startup,it automatically boots Windows from your first hard drive with no Grub menu.


Good Luck

---

### Post by sundarrajan on 2009-03-31
how to use live cd to copy the existing data explain me please !!):P

---

### Post by meierfra. on 2009-03-31
> sudo grub

find /boot/grub/stage1

root hd(1,6)

setup(hd1)

You installed grub to the MBR of the ubuntu drive. What happens when you set you bios to boot from the Ubuntu drive?


You might also try:
```

sudo grub
root (hd1,6)
setup (hd0)
quit

```

> try at a better level to atleast catch up my data !!!

Its better i can able to recover the files in my ubuntu and after recovering it i can just go on reinstallation of ubuntu !!!

Currently I don't see any reason why you should have to reinstall Ubuntu.

---

### Post by Panarchy on 2009-04-01
Or you could use the LiveCD with the commands that autopopulate the GRUB menu.

However, if the MBR somehow got corrupted, then fix it with fdisk /mbr or by using the Windows bootdisc.

Also, if the MBR is fully corrupted, and you can't get anything from it, give TestDisk a go.

Worked for me on multiple occasions.

Panarchy

---

### Post by SubNetMask on 2009-04-01
> **sundarrajan said:**
> 

Try at a better level to atleast catch up my data !!!



If you just want to get your data back, Get hiren's boot CD, and make a partition, then delete the windows folder and the MBR, then re-install windows/linux.

---

### Post by anitha-h on 2009-04-01
If ubuntu partition is not seen in grub after installing windows, Put a live Ubuntu CD and open a terminal then try these commands

#sudo grub
grub> find /boot/grub/stage1
grub > root (hd0,0)
grub>setup grub

ok
grub>quit
then boot again now you see ubuntu in the grub menu

---

### Post by sundarrajan on 2009-04-01
I have tried it also but no use !!!


You are partly right about my system that is now windows alone is loading in and if i change the harddisk priroity for bootup process system doesnt find any os!!


So i am sure that both windows and ubuntu are on the same hard drive ! the second harddrive contains only data !!!


So please help me to clear the problem !!1

---

### Post by meierfra. on 2009-04-01
Please don't start multiple  threads on the same subject.

Some bios refuse to load a hard drive without a boot flag.
Try this:


Open a terminal in the Live CD and type

```
sudo sfdisk -A1 /dev/sdb
```
( the 1 after -A is the number one not the lower case letter L)

Reboot and make sure that the bios are set to boot from the Ubuntu drive (not the storage drive)

---

### Post by bwallum on 2009-04-01
I have just had a similar problem. 

The first point is to make sure that the hard drive booted by the bios is the hard drive with GRUB in the master boot record.

Using the live CD you can see the hard drives with the command```
sudo lshw -class disk
``` This will give you the manufacturers name and serial number of the disk and also the logical name which will be something like /dev/sda. 

You have more than one disk so make sure that grub is installed on the disk that the bios uses as the boot drive.

You may still get a blank screen even if you align the disks as above and if you do you need to edit the /boot/grub/menu.lst file which should look something like this:> # menu.lst - See: grub(8), info grub, update-grub(8)
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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
#password topsecret

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
# kopt=root=UUID=57087ac6-33b7-4eb5-ad7b-0cb7c7f8e921 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,0)

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
# defoptions=quiet splash vga=795

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

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

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

title		Ubuntu jaunty (development branch), kernel 2.6.28-11-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=57087ac6-33b7-4eb5-ad7b-0cb7c7f8e921 ro quiet splash vga=795 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu jaunty (development branch), kernel 2.6.28-11-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=57087ac6-33b7-4eb5-ad7b-0cb7c7f8e921 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu jaunty (development branch), memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
title		Ubuntu 7.10, kernel 2.6.22-14-generic (on /dev/sdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=f4adee08-311b-4cc5-99d3-a6b00e4624a6 ro quiet splash 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode) (on /dev/sdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=f4adee08-311b-4cc5-99d3-a6b00e4624a6 ro single 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
title		Ubuntu 7.10, memtest86+ (on /dev/sdc1)
root		(hd2,0)
kernel		/boot/memtest86+.bin  
savedefault
bootIn the above I have two versions of Ubuntu running on seperate hard drives and the master boot record is on hd(0,0). (I have three hard drives in total on the system but hd(1,0) is not shown above because there is no linux kernel on that drive.)

Look for the entry that relates to the boot harddrive and make sure that it really does point to the booted hard drive. The convention for naming the disks in grub starts at 0 so hd(0,0) relates to sda normally. You can check to see if you have altered this mapping by looking at /boot/grub/device.map```
gksu gedit /boot/grub/device.map
```

I hope that helps and wish you luck.

Bob

---

### Post by sundarrajan on 2009-04-04
thank u for step please read this !!!

sorry for the late reply please pay some attention and help me to recover!

```
ubuntu@ubuntu:~$ ls -l /dev/disk/by-uuid
total 0
lrwxrwxrwx 1 root root 10 2009-04-04 12:01 3a867158-3dc2-468a-b958-0cc828a3a90c -> ../../sdb8
lrwxrwxrwx 1 root root 10 2009-04-04 12:01 3C0C0B410C0AF5A4 -> ../../sdb1
lrwxrwxrwx 1 root root 11 2009-04-04 12:01 4C00FF5200FF420E -> ../../sdb10
lrwxrwxrwx 1 root root 10 2009-04-04 12:01 7E8CF1D58CF187C3 -> ../../sdb5
lrwxrwxrwx 1 root root 10 2009-04-04 12:01 9668F0B168F090EB -> ../../sda5
lrwxrwxrwx 1 root root 10 2009-04-04 12:01 9A1005BB10059F7F -> ../../sda2
lrwxrwxrwx 1 root root 10 2009-04-04 12:01 abd15458-6774-4289-b537-94a1f67ed969 -> ../../sdb7
lrwxrwxrwx 1 root root 10 2009-04-04 12:01 B280FAFD80FAC73F -> ../../sdb9
lrwxrwxrwx 1 root root 10 2009-04-04 12:01 EC3879C138798AFA -> ../../sdb6
lrwxrwxrwx 1 root root 10 2009-04-04 12:01 F68C17948C174F0D -> ../../sda3
ubuntu@ubuntu:~$ 
```

---

### Post by sundarrajan on 2009-04-04
i tried this but no change in the boot menu

```
ubuntu@ubuntu:~$ sudo sfdisk -A1 /dev/sdb
Done

ubuntu@ubuntu:~$
```

THANKS FOR U R REPLY

---

### Post by meierfra. on 2009-04-04
> i tried this but no change in the boot menu

Did you set your bios to boot from the Ubuntu drive, after you set the boot flag?


Did you ever try

sudo grub
root (hd1,6)
setup (hd0)
quit

and then boot from the 250GB drive?


**If none of this helps:**

In order to get a clearer picture of your setup, I suggest to boot from the Ubuntu LiveCD and  download the Boot Info Script to  your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, (use the code tags)

---

### Post by Elfy on 2009-04-04
Do this please - boot the livecd and open a terminal, then run these commands

```
sudo mkdir /mnt/tmp
sudo mount -t ext3 /dev/sdb7 /mnt/tmp
```

Now run the grub reinstall operation as you did before, if it gives an error, we need to know what it is.

Now run this and paste it's result and the answer to the above here 

```
cat /mnt/tmp/boot/grub/menu.lst
```

---

### Post by meierfra. on 2009-04-04
**forestpixie** The OP is running another threads on the same subject 

[http://ubuntuforums.org/showthread.php?t=1111887](http://ubuntuforums.org/showthread.php?t=1111887)

---

### Post by Elfy on 2009-04-04
> **meierfra. said:**
> **forestpixie** The OP is running another threads on the same subject 

[http://ubuntuforums.org/showthread.php?t=1111887](http://ubuntuforums.org/showthread.php?t=1111887)

Aah - I hate that :(

Thanks for letting me know, I shall report this and get it locked or merged.


@sundarrajan - don't post duplicate threads - it's a waste of volunteer's time and also - information gets disjointed and no-one knows what is going on elsewhere. Next time just start a new thread instead of tagging on the end of a SOLVED one.

---

### Post by Elfy on 2009-04-04
sundarrajan - the tag system is there for people to search by - it is for everyone, I would guess that very few people will search for 'sundarrajan needs help'

Please change them so they reflect the nature of the thread

---

### Post by bapoumba on 2009-04-04
Threads merged.

---

