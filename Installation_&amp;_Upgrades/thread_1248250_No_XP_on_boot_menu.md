---
title: "No XP on boot menu"
date: 2009-08-23
forum: Installation &amp; Upgrades
---

### Post by NickArcifa on 2009-08-23
hey all,
can you please help me!

I have an old 800mhz computer which has XP installed on it on a 40gb HDD, and it had a second HDD which was 7gb, i installed Xubuntu on the 7gb hdd. Intallation was good with no hitches but now when i load up i get a message press esc in 3 seconds to go to menu. when i press this it shows up Xubuntu, Xubuntu Recovery, and Xubuntu memtest but no xp!. if i dont press esc it automatically boots into xubuntu. Is their anyway to not press escape to get to list, but automatically get the bootlist. how can i add xp to the boot list. also in xubuntu my xp hdd wont show up and Xubuntu wont remeber the resolution i specified, 1024x768, i have 1152x864 but this causes the desktop to be skewed so i run it on the lower res.
Cheers Nick Arcifa

---

### Post by NickArcifa on 2009-08-23
i did a little research,

i opened a terminal and wrote sudo fdisk -l and it came up with this:  

Disk /dev/sda: 5121MB, 5121446400 bytes
255 heads, 63 sectors/track, 622 cylinders
Units = cylinders of 16065 * 512 = 82252800 bytes
Disk identifiers 0xcccdcccd

Device   boot       Start        End    Blocks      Id    System
/dev/sda1 *          1           622    4996183+     83    Linux


Disk /dev/sdb: 40.9GB, 40982151168 bytes
255 heads, 63 sectors/track, 4982 cylinders
Units = cylinders of 16065 * 512 = 82252800 bytes
Disk identifiers 0x75fd75fd

Device   boot       Start        End    Blocks      Id    System
/dev/sdb1 *          1           4891    4009851    83    Linux

I don't understand why the second has Linux, it may be possibly from a failed WUBI install before, because when i used to boot xp it had a Grub like menu that had Xubuntu and XP as an option, but Xubuntu would not work..

Hope this helps and you guys can help me fix my system....
If not my mother will possibley throttle me for stuffing up our old computer even know no one barely uses it....
Thanks, Nick Arcifa

---

### Post by NickArcifa on 2009-08-24
oops the Device Boot lines kinda failed a bit no spaces lol
under device their is the hdd eg. /dev/sd(a or b), under boot their is a * for both HDDs.
Both have 1 under start, end for the first hdd is 622 and for the next hdd it is 4981. blocks in the first is 4996183+ and for the second it is 40009851 both id's are 83 and both show up as Linux System

---

### Post by NickArcifa on 2009-08-24
Would it be better to somehow delete xubuntu and go back to xp, get a program to fix my MBR to get rid of xubuntu option when it comes up for the Xubuntu and XP (wubi) boot screen. and then reinstall Xubuntu? would this fix my problem if it would could you please tell me how to do it...

i hope its not to confusing

---

### Post by NickArcifa on 2009-08-24
To clear this up a little, when XP was my only operating system i tried a wubi install of xubuntu. For some reason the system would not install properly so i got into xp and uninstalled the wubi Xubuntu..

The second time i booted of a live CD of xubuntu and installed it off the xubuntu desktop icon :)

please help!

Even thought my XP hardrive shows up as linux when i ran fdisk -l, how come it doesn't show up in Xubuntu thunar browser, it only has the filesystem

---

### Post by presence1960 on 2009-08-25
Nick to get rid of the wubi entry in windows see my post #3 [here]("http://ubuntuforums.org/showthread.php?t=1234516&highlight=wubi+boot.ini")

Then do this:

Let's get a better look at your setup. Boot into Ubuntu. Come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

To not have to press Esc boot into Ubuntu and edit your menu.lst file to look like this (I only pasted the relevant section here):
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
timeout		[COLOR="Blue"]4[/COLOR]

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
[COLOR="Red"]#[/COLOR]hiddenmenu

# Pretty colours
#color cyan/blue white/blue
```

See the red # sign. You need to add that to your menu.lst
See the blue 4. change that value to set the number of seconds before Grub will boot whatever is highlighted without you hitting enter. This is the delay setting.

---

### Post by NickArcifa on 2009-08-25
The thing is that i can't get into XP at all as it doesn't have an option on the boot menu for grub!

im confuddled! 

i asked a friend and he suggested to me to use the XP disc to restore the MBR to xp, then jsut simply reinstall my windows

---

### Post by NickArcifa on 2009-08-25
```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => Syslinux is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /ntldr

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 5121 MB, 5121446400 bytes
255 heads, 63 sectors/track, 622 cylinders, total 10002825 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcccdcccd

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63     9,992,429     9,992,367  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 40.9 GB, 40982151168 bytes
255 heads, 63 sectors/track, 4982 cylinders, total 80043264 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x75fd75fd

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    80,019,764    80,019,702  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 8019 MB, 8019509248 bytes
20 heads, 16 sectors/track, 48947 cylinders, total 15663104 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc3072e18

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             80    15,663,103    15,663,024   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="6eae820c-4b7e-4685-b14c-8cf9803d68c7" TYPE="ext3" 
/dev/sdb1: UUID="DE58055458052CB9" TYPE="ntfs" 
/dev/sdc1: LABEL="NICK ARCIFA" UUID="2EF1-33B1" TYPE="vfat" 

=============================== "mount" output: ===============================

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
/dev/sdc1 on /media/NICK ARCIFA type vfat (rw,nosuid,nodev,uhelper=hal,utf8,shortname=winnt,uid=1000)


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
timeout		5

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
# kopt=root=UUID=6eae820c-4b7e-4685-b14c-8cf9803d68c7 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=6eae820c-4b7e-4685-b14c-8cf9803d68c7

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

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		6eae820c-4b7e-4685-b14c-8cf9803d68c7
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=6eae820c-4b7e-4685-b14c-8cf9803d68c7 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		6eae820c-4b7e-4685-b14c-8cf9803d68c7
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=6eae820c-4b7e-4685-b14c-8cf9803d68c7 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		6eae820c-4b7e-4685-b14c-8cf9803d68c7
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=6eae820c-4b7e-4685-b14c-8cf9803d68c7 /               ext3    relatime,errors=remount-ro 0       1
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


   4.8GB: boot/grub/menu.lst
   4.9GB: boot/grub/stage2
   4.9GB: boot/initrd.img-2.6.28-11-generic
   4.9GB: boot/vmlinuz-2.6.28-11-generic
   4.9GB: initrd.img
   4.9GB: vmlinuz

```

here is the info from the results file sdc1 is just a usb plugged into the system after boot, which is bootable which i use on random slow computers for booting puppylinux or DSL

---

### Post by presence1960 on 2009-08-25
Nick,

You do want to restore XPs bootloader as it is missing boot.ini. First though you must switch the disk with XP on it to first boot in the BIOS hard disk boot order. The reason for this is windows will try to write the bootloader to which ever disk is the one that boots first. [Here]("http://ubuntuforums.org/showthread.php?t=1014708") is a how to in case you are not familiar with how to restore bootloader. After that is complete reboot and make sure you boot straight into windows.

Next reboot one more time & go into BIOS and put your sda (Ubuntu) disk back to first boot so GRUB will come up when you boot. Then boot into Ubuntu. Open a terminal and run ```
gksu gedit /boot/grub/menu.lst
```
and add this after the Ubuntu kernels list:

```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows XP
rootnoverify	(hd1,0)
chainloader	+1
```

This will work as long as your windows files are intact. If they are not you will not be able to boot into windows. At that point you will have to reinstall windows. if you have to do that just make sure you put the sdb disk as first boot in BIOS hard disk order before installing Windows  or the windows bootloader will be written to the wrong disk (sda) When complete boot again and go into BIOS and put sda back to first boot. Then follow the instructions above for adding the windows entry to menu.lst. let us know how you make out!

---

### Post by NickArcifa on 2009-08-26
Ok so what exactley am i going to have to do. change the boot order to boot off the xp hardrive first in BIOS then do what once im in windows?

reboot then change the hardrive to xubuntu hardrive first? then do what im slightley confused?

---

### Post by NickArcifa on 2009-08-26
Oh noes, i don't have an xp disc at home, is there anything that i can use to fix the xp thingy. i heard of a program called ERD commander but i don't know if it will work.

---

### Post by NickArcifa on 2009-08-26
I do have a Vista Ultimate Upgrade disc thought, will that help?

---

### Post by NickArcifa on 2009-08-26
Ok i managed to change the boot order to the XP hardrive first :() but it just doesn't want to boot xp, just comes up with a hung screen after these lines 

```
Verifying DMI Pool Data..........
Boot from ATAPI CD-ROM : Bootable CD does not exist...
Boot from ATAPI CD-ROM : Bootable CD does not exist...
```

as i have 2 CD drives on the old computer. After this there is just a continuous white underscore repeditavley flashing.

This tells me that the XP "boot.ini" is either 1. missing or 2. corrupted.

If i could see the other big HDD (sdb or hd1) with XP on it in xubuntu could i get say a boot.ini file from somebody else using XP home and just paste it in the same directory?

The only problem with this idea (if it was possible, is that i cant see sdb in xubuntu) im confuddled 

Is it possible that some how i screwed up and overwrit the XP hardrive or something or did xubuntu just not work?

---

### Post by NickArcifa on 2009-08-26
I booted off a xubuntu live CD and could not see either HDD,
booted off a ubuntu live CD and could see and mount both? wtf? lol confuddled! both versions were 9.04

maybe i should just reformat both the HDD's and install XP on the big one then put Xubuntu on the small HDD. we don't use it a lot just for surfing web really

---

### Post by presence1960 on 2009-08-26
> **NickArcifa said:**
> Ok so what exactley am i going to have to do. change the boot order to boot off the xp hardrive first in BIOS then do what once im in windows?

reboot then change the hardrive to xubuntu hardrive first? then do what im slightley confused?

You really need your XP install disk!

Change the boot order so the disk with XP boots first. Then boot off the XP CD. You will then do this:

For this you will need your Windows XP installation CD. Boot into it now.

You will get to a part where it asks if you want to repair or recover. To do so, press "r".

If prompted, enter your Windows XP administrator password. This will leave you at at a command line, so type in the following two commands:

```
fixboot
```
```
fixmbr
```

then type```
 exit
```

reboot and see if XP boots. if it does reboot again and put the disk with Ubuntu back to first in the BIOS boot order so GRUB comes up when you boot.

Boot into Ubuntu and run this command from terminal ```
gksu gedit /boot/grub/menu.lst
``` 
Scroll down to bottom and add the windows entry like this:
```

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows XP
rootnoverify	(hd1,0)
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader	+1
```

---

### Post by NickArcifa on 2009-08-27
Ok got a XP home  disk will tell you what happens :) and by the way xubuntu is mousepad hehe :) but i installed gedit, prefer the interface :)

Could you explain exactley what the map commands mean and what they do? or is it to complicated :)

---

### Post by NickArcifa on 2009-08-27
god damn it it wont boot! grr followed the instructions, typed fixboot, then fixmbr, then quit XP will not boot god damn it!!! and now my xubuntu wont boot either! grr! im so confuddled! does this mean that i am going to have to reinstall XP? during the fix boot it came up with this 

I made sure that the XP hdd was first boot, then the xubuntu. and in recover console i picked 1 as this was the only option for Windows install

```
The Target Partiton is C:.
are you sure you want to  write a new boot sector to the partiton C:? (i hit y)
the file system on the startup partition is unknown
FIXBOOT is attempting to detect the file system type.

The Boot sector is corrupt.
Fixboot is checking the filesystem type..... 
the partition is using the NTFS file system.

FIXBOOT is writing a new boot sector.

The new boot sector was successfully written.
```

When i typed fixmbr i got 
```
** CAUTION **
this computer appears to have a non-standard or invalid master boot record
FIXMBR may damage you partiton tables if you proceed.

This coild cause all the partitons on the current harddisk to become inaccessible

If you are having problems accessing your drive, do not continue.

Are you sure u want to write a new MBR? (i hit y again)

Writing new master boot record on physical drive
\Device\Harddisk0\Partition0.

The New master boot record has been successfully written
```

I then typed exit and rebooted but windows would not boot, nor would xubuntu.

it just hung after the Boot from CD rom bit with an underscore (_) continually blinking!

---

