---
title: "Neogrub issues"
date: 2009-10-27
forum: Installation &amp; Upgrades
---

### Post by Deliverance XXV on 2009-10-27
Hi :D Newb to Ubuntu here. Apologies in this is in the wrong forum.

Okay basically, I had installed Vista as normal and decided I wanted to try Ubuntu. So I installed Ubuntu as a dual boot option. All was fine. Then I wanted Vista to boot first. 

So I changed the MBR with Easy BCD using this [guide]("http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=1"). Now the problem is Vista works perfectly whilst the Ubuntu booting options wont boot. The error is error 17 : A file is missing...

So I googled for solutions and upgrading to EasyBCD2 was recommended. I tried this to no avail. So, any help is greatly appreciated. 

Future Ubuntu lover, James.

Here is the config file.

[html]
# NeoSmart NeoGrub Bootloader Configuration File
#
# This is the NeoGrub configuration file, and should be located at C:\NST\menu.lst
# Please see the EasyBCD Documentation for information on how to create/modify entries:
# http://neosmart.net/wiki/display/EBCD

default 4        #Pick the task to be run if the user doesn't pick one within the time limit.
timeout 10        #Give the user 10 seconds to choose a task.

## ## End Default Options ##

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        6dd819ec-f0c5-4c84-bf3b-c17c95964b6e
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=6dd819ec-f0c5-4c84-bf3b-c17c95964b6e ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        6dd819ec-f0c5-4c84-bf3b-c17c95964b6e
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=6dd819ec-f0c5-4c84-bf3b-c17c95964b6e ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        6dd819ec-f0c5-4c84-bf3b-c17c95964b6e
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdd1
title        Windows Vista (loader)
rootnoverify    (hd3,0)
savedefault
makeactive
map        (hd0) (hd3)
map        (hd3) (hd0)
chainloader    +1

[/html]

---

### Post by ajgreeny on 2009-10-27
I would restore grub as it was after installing ubuntu and simply set grub to boot windows first, rather than messing about with anything else, though I admit I know absolutely nothing about EasyBCD

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
This will tell you where your /boot/grub/stage1 is which is needed to boot ubuntu. If you have more than one linux install you may get more than one answer here.  Use the one from which you want to use grub.  Replace the question marks in the following command with the output of the this last command :
    ```
root (hd?,?)
```
[like : root (hd0,1) ,probably]
then:
    ```
setup (hd0)
```
This is where your windows partition and MBR normally is, but if you want grub on another disk, use hd1, etc as appropriate. It's much easier to use the windows MBR and then just change the default boot system later if others in the family demand windows boots by default.
Then:
    ```
quit
```
Finally reboot, and hopefully you will now have a working grub bootloader.

Now after checking that it works for both OSs boot to ubuntu and use ```
gksud gedit /boot/grub/menu.lst
```which will open that file and allow you to edit and save the changes as root.

Look for:-
```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0
```
and change the 0 to "saved".  If your menu list looks like mine, the windows entry will have the line savedefault in it like this:-
> title        Microsoft Windows XP (or vista)
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1Now windows will boot instead of ubuntu as default, and it will not matter if new kernels are installed as the number of windows is not important, just the "saved" notation in grub.

I hope that makes sense.  It's not really as difficult as it may sound, and should work fine.

---

### Post by Deliverance XXV on 2009-10-28
Cheers for the fast reply :p I'm just finished work now and I'm off to college so wont be able to check it until tomorrow. Will keep you update. Cheers m8

---

### Post by presence1960 on 2009-10-28
> **ajgreeny said:**
> I would restore grub as it was after installing ubuntu and simply set grub to boot windows first, rather than messing about with anything else, though I admit I know absolutely nothing about EasyBCD

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
This will tell you where your /boot/grub/stage1 is which is needed to boot ubuntu. If you have more than one linux install you may get more than one answer here.  Use the one from which you want to use grub.  Replace the question marks in the following command with the output of the this last command :
    ```
root (hd?,?)
```
[like : root (hd0,1) ,probably]
then:
    ```
setup (hd0)
```
This is where your windows partition and MBR normally is, but if you want grub on another disk, use hd1, etc as appropriate. It's much easier to use the windows MBR and then just change the default boot system later if others in the family demand windows boots by default.
Then:
    ```
quit
```
Finally reboot, and hopefully you will now have a working grub bootloader.

Now after checking that it works for both OSs boot to ubuntu and use ```
gksud gedit /boot/grub/menu.lst
```which will open that file and allow you to edit and save the changes as root.

Look for:-
```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0
```
and change the 0 to "saved".  If your menu list looks like mine, the windows entry will have the line savedefault in it like this:-
Now windows will boot instead of ubuntu as default, and it will not matter if new kernels are installed as the number of windows is not important, just the "saved" notation in grub.

I hope that makes sense.  It's not really as difficult as it may sound, and should work fine.

+1

Be glad you know nothing of EasyBCD. In my opinion it is garbage. GRUB is way more customizable and easier to use.

---

### Post by Deliverance XXV on 2009-10-29
Cheers for the replies guys.

Okay I followed all your steps and they went through flawlessly until I got to the point where I was checking both OS's. Vista boot was fine but I'm still getting the error with Ubuntu?? Any ideas?

Thanks for the patience folks!

---

### Post by presence1960 on 2009-10-29
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by Deliverance XXV on 2009-10-29
Here you go, cheers m8.

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #4 in 
    partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
 => Windows is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdc2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /NST/menu.lst /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe

sdd2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdd5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdd6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcb16cc8a

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   625,139,711   625,137,664   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
16 heads, 63 sectors/track, 969021 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3325c588

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   821,121,023   821,118,976   7 HPFS/NTFS
/dev/sdb2         821,121,024   972,673,023   151,552,000   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
256 heads, 63 sectors/track, 60563 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *              1 4,294,967,295 4,294,967,295  ee GPT

/dev/sdc1 ends after the last sector of /dev/sdc

GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sdc1              34       262,177       262,144 Microsoft Windows
/dev/sdc2         264,192   976,773,119   976,508,928 Linux (usually)

Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7e95a801

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *          2,048 1,827,821,567 1,827,819,520   7 HPFS/NTFS
/dev/sdd2       1,827,827,505 1,953,520,064   125,692,560   5 Extended
/dev/sdd5       1,827,827,568 1,948,298,939   120,471,372  83 Linux
/dev/sdd6       1,948,299,003 1,953,520,064     5,221,062  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="8A1834731834607D" LABEL="Hard Disc 3" TYPE="ntfs" 
/dev/sdb1: UUID="C252DB5252DB49B5" LABEL="Back Up (400GB)" TYPE="ntfs" 
/dev/sdb2: UUID="BEA6C6BCA6C67485" LABEL="Other (74GB)" TYPE="ntfs" 
/dev/sdc2: UUID="1EB84F05B84EDB43" LABEL="Hard Disc 2 (500GB)" TYPE="ntfs" 
/dev/sdd1: UUID="864AA6804AA66C9D" TYPE="ntfs" 
/dev/sdd5: UUID="6dd819ec-f0c5-4c84-bf3b-c17c95964b6e" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdd6: UUID="a4d7be86-c7db-4004-ad83-98c61069b9b4" TYPE="swap" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sr1 on /media/FRINGE_SEASON_1_DISC_2 type udf (ro,nosuid,nodev,uhelper=hal,uid=999)


============================== sdd1/NST/menu.lst: ==============================

# NeoSmart NeoGrub Bootloader Configuration File 
# 
# This is the NeoGrub configuration file, and should be located at C:\NST\menu.lst 
# Please see the EasyBCD Documentation for information on how to create/modify entries: 
# http://neosmart.net/wiki/display/EBCD 
 
default 4        #Pick the task to be run if the user doesn't pick one within the time limit. 
timeout 10        #Give the user 10 seconds to choose a task. 
 
## ## End Default Options ## 
 
title        Ubuntu 9.04, kernel 2.6.28-11-generic 
uuid        6dd819ec-f0c5-4c84-bf3b-c17c95964b6e 
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=6dd819ec-f0c5-4c84-bf3b-c17c95964b6e ro quiet splash  
initrd        /boot/initrd.img-2.6.28-11-generic 
quiet 
 
title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) 
uuid        6dd819ec-f0c5-4c84-bf3b-c17c95964b6e 
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=6dd819ec-f0c5-4c84-bf3b-c17c95964b6e ro  single 
initrd        /boot/initrd.img-2.6.28-11-generic 
 
title        Ubuntu 9.04, memtest86+ 
uuid        6dd819ec-f0c5-4c84-bf3b-c17c95964b6e 
kernel        /boot/memtest86+.bin 
quiet 
 
### END DEBIAN AUTOMAGIC KERNELS LIST 
 
# This is a divider, added to separate the menu items below from the Debian 
# ones. 
title        Other operating systems: 
root 
 
 
# This entry automatically added by the Debian installer for a non-linux OS 
# on /dev/sdd1 
title        Windows Vista (loader) 
rootnoverify    (hd3,0) 
savedefault 
makeactive 
map        (hd0) (hd3) 
map        (hd3) (hd0) 
chainloader    +1 
 

=========================== sdd5/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=6dd819ec-f0c5-4c84-bf3b-c17c95964b6e ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=6dd819ec-f0c5-4c84-bf3b-c17c95964b6e

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

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        6dd819ec-f0c5-4c84-bf3b-c17c95964b6e
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=6dd819ec-f0c5-4c84-bf3b-c17c95964b6e ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        6dd819ec-f0c5-4c84-bf3b-c17c95964b6e
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=6dd819ec-f0c5-4c84-bf3b-c17c95964b6e ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        6dd819ec-f0c5-4c84-bf3b-c17c95964b6e
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdd1
title        Windows Vista (loader)
rootnoverify    (hd3,0)
savedefault
makeactive
map        (hd0) (hd3)
map        (hd3) (hd0)
chainloader    +1


=============================== sdd5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdd5 during installation
UUID=6dd819ec-f0c5-4c84-bf3b-c17c95964b6e /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdd6 during installation
UUID=a4d7be86-c7db-4004-ad83-98c61069b9b4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdd5: Location of files loaded by Grub: ===================


 974.5GB: boot/grub/menu.lst
 974.5GB: boot/grub/stage2
 974.5GB: boot/initrd.img-2.6.28-11-generic
 974.5GB: boot/vmlinuz-2.6.28-11-generic
 974.5GB: initrd.img
 974.5GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sde sdf sdg sdh 
```

---

### Post by presence1960 on 2009-10-29
This is what I would do: put GRUB on MBR of sdd (1000 GB) and then set sdd as first in the hard disk boot order in BIOS.

```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd3,4)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd3,4)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd3)", to install GRUB to MBR
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.
```

when rebooting go into BIOS and set sdd (1000 GB) as first disk to boot in hard disk boot order. Save changes to CMOS and exit BIOS. 

Boot into Ubuntu. When the desktop Loads open a terminal and run this command ```
gksu gedit /boot/grub/menu.lst
``` That is a lowercase L in .lst

scroll down to the bottom and change this:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdd1
title        Windows Vista (loader)
rootnoverify    (hd3,0)
savedefault
makeactive
map        (hd0) (hd3)
map        (hd3) (hd0)
chainloader    +1
```

TO:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdd1
title           Windows Vista (loader)
rootnoverify    (hd0,0)
chainloader     +1

```

Your (hdx,y) numbers will change because your hard disk boot order has changed. In (hdx,y) x = device and y = partition.Numbering starts at 0 for both designations. But the x designation is determined by the boot order of the disks in BIOS as that is the order in which your machine boots regardless of what fdisk or ubuntu report. Since sdd now boots first instead of fourth it changes from (hd3) to (hd0).

You will no longer need the map lines because windows is installed to the first disk that boots.

---

### Post by Deliverance XXV on 2009-10-29
Excellent stuff, cheers m8! 
Okay, Ubuntu is working perfectly as is Vista but ubuntu is still the default boot option :)

---

### Post by presence1960 on 2009-10-29
> **Deliverance XXV said:**
> Excellent stuff, cheers m8! 
Okay, Ubuntu is working perfectly as is Vista but ubuntu is still the default boot option :)

Glad you got it working. You can install startupmanager to control the default OS as well as other options. You can use Synaptic to install it or open a terminal and run ```
sudo apt-get install startupmanager
```

---

### Post by Deliverance XXV on 2009-11-01
Hey cheers again :-) 

I tried the above and used StartUp Manager and there was an option for Vista for first boot but when I tried that and it came to boot the memtest was the first selected?

Here is the structure of the boot up list:

Ubuntu #1
Ubuntu #2
Ubuntu #3

Vista

Then I would select Vista and then I would get another menu, of which Vista is is an option. Is there supposed to be a sub-menu? Was this the remnants of a NeoGrub attempt?

Cheers folks.

---

