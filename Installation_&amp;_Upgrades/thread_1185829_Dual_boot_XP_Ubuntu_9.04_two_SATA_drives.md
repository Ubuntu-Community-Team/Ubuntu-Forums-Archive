---
title: "Dual boot XP Ubuntu 9.04 two SATA drives"
date: 2009-06-12
forum: Installation &amp; Upgrades
---

### Post by android73 on 2009-06-12
Hi everyone, I have posted this question to the lengthy previous thread regarding this topic([http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)), but thought I would address it here as well in the hopes of getting some advice!

I too am new to Ubuntu and Linux in general, and am in the process of installing a dual boot system with my existing Windows XP. I have installed Ubuntu on a separate internal SATA drive, after unplugging my other Windows drive which is also a SATA. I have done all the updates and am ready to modify the grub menu and re-plug in my Windows drive, but am still unsure after reading all these posts what lines to add to it based on my setup. I am not sure what the difference is between inserting this:

title              Windows XP
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1

...and inserting this is:

title Windows NT/2000/XP (loader)
map (hd0,0) (hd1,0)
map (hd1,0) (hd0,0)
rootnoverify (hd1,0)
makeactive
chainloader +1

I have found both of these in different threads as solutions. But have no idea if this applies to my setup. Does the "hd" designation apply to an IDE type drive? Does this need to be changed to "sd" designation for SATA drives? Im confused. Below is my fdisk list. Also, when you add these lines, are spaces required above and below that section? Thank you in advance for any assistance you guys could provide. These are really helpful forums! :p


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0004d8e5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1245    10000431   83  Linux
/dev/sda2            1246       60303   474383385   83  Linux
/dev/sda3           60304       60801     4000185   82  Linux swap / Solaris
andrew@andrew-desktop:~$

---

### Post by labinnsw on 2009-06-12
First of all I would not have unplugged the windows drive for installation of Ubuntu. That way the menu list would be created automatically and only need minor editing if at all.

That said, either option looks good. I am using only one hard drive so in my case, I have commented out the map lines. If you have a problem you can try that like:


> title Windows XP
root (hd1,0)
savedefault
makeactive
[B]#map (hd0) (hd1)
#map (hd1) (hd0)[/B]
chainloader +1

or

title Windows NT/2000/XP (loader)
[B]#map (hd0,0) (hd1,0)
#map (hd1,0) (hd0,0)[/B]
rootnoverify (hd1,0)
makeactive
chainloader +1

---

### Post by android73 on 2009-06-12
Hi labinnsw,

Thanks for the tip! I had unplugged windows drive per the other threads I had read so that there was no possibility of me screwing up the windows mbr(seriously I am new to this!). I will give these a shot. I'm stumbling along trying to figure this all out! Thanks again.

---

### Post by presence1960 on 2009-06-12
plug in all your drives. Boot Ubuntu and run in terminal : ```
sudo fdisk -l
``` Post the output back here.

Also run in terminal ```
gksu gedit /boot/grub/menu.lst
``` post that output also. BTW those are lowercase L in those commands.

---

### Post by android73 on 2009-06-13
Ok, thanks will post those soon! Again I appreciate all the help here!

---

### Post by android73 on 2009-06-13
Ok, here is the info. Thanks again!!! Also, when I first booted into Ubuntu I got three error messages, not sure what they mean:

Error: The panel ecountered a problem while loading "OAFIID:GNOME_MixerApplet". Do you want to delete the applet from your config?
Error: The panel ecountered a problem while loading "FastUserSwitchApplet". Do you want to delete the applet from your config?
Error: The panel ecountered a problem while loading "IndicatorApplet". Do you want to delete the applet from your config?


andrew@andrew-desktop:~$ sudo fdisk -l
[sudo] password for andrew: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0004d8e5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1245    10000431   83  Linux
/dev/sda2            1246       60303   474383385   83  Linux
/dev/sda3           60304       60801     4000185   82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x66e7999a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30401   244196001    7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001    7  HPFS/NTFS
andrew@andrew-desktop:~$ 


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
timeout        3

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
# kopt=root=UUID=f54083ad-d142-4448-b5ef-22073bdcd61c ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=f54083ad-d142-4448-b5ef-22073bdcd61c

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
uuid        f54083ad-d142-4448-b5ef-22073bdcd61c
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=f54083ad-d142-4448-b5ef-22073bdcd61c ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        f54083ad-d142-4448-b5ef-22073bdcd61c
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=f54083ad-d142-4448-b5ef-22073bdcd61c ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        f54083ad-d142-4448-b5ef-22073bdcd61c
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by presence1960 on 2009-06-13
those errors on boot seem to indicate you either reinstalled or did a clean install of Ubuntu and used your config files from the old /home BUT did not install those apps to the new installation panels. That's why you are getting those errors, the config files are in your /home directory but the apps are not installed.

your windows entry at the end of menu.lst should be:

```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP 
rootnoverify	(hd1,0)
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader	+1
```

if that does not work check in BIOS to see the boot order of your disks. If windows is on sdb1 then that disk should be second boot in the order. You can change it in BIOS.

---

### Post by android73 on 2009-06-13
Thanks for the reply! That did work, however I still get the 3 seconds to hit esc to go into the grub menu itself before it boots into Ubuntu. If I ever want to get the grub menu to load first and prompt you to choose operating systems, how would I go about doing that? Also, I tried installing the fs-driver in windows so I could read the ext3 partition in Ubuntu, does this only work for ext2? If that's the case, how can I get access from Windows. Thanks so much for your help, it's great to be up an running!

aap

---

### Post by presence1960 on 2009-06-13
```
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		4

## hiddenmenu
 Hides the menu by default (press ESC to see the menu)
hiddenmenu

```

 change the above in menu.lst - comment out the "hidden menu" lines like this

```
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		4

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

```

to change the time to boot default entry change the numeric value in the timeout line.

---

