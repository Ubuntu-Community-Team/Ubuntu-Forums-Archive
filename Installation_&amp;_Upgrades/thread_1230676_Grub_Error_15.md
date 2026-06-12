---
title: "Grub Error 15"
date: 2009-08-03
forum: Installation &amp; Upgrades
---

### Post by gmclella on 2009-08-03
Ok, so I've googled this problem and it seems to be common.   My issue is that I'm not familiar with LINUX and am having a hard time deciphering some of the info I've come across.   I'm hoping someone can walk me through this.

I'm dual booting XP and Ubuntu and when I try to launch Ubuntu through Grub I get the Error 15: File not found message.    From my digging it seems that the menu.lst file is not in the root and is at /media/disk-1/boot/grub.  I'm thinking this is why it's not found.

1 hard drive, first partition is XP, second is swap, third is /, and fourth was /home.

Anyways, the hard data: 
menu.lst

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
# kopt=root=UUID=b0ce8276-1c50-472e-a41e-44c4406bb924 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=b0ce8276-1c50-472e-a41e-44c4406bb924

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
root (hd0,2)
uuid        b0ce8276-1c50-472e-a41e-44c4406bb924
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=b0ce8276-1c50-472e-a41e-44c4406bb924 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet


title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
root (hd0,2)
uuid        b0ce8276-1c50-472e-a41e-44c4406bb924
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=b0ce8276-1c50-472e-a41e-44c4406bb924 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
root (hd0,2)
uuid        b0ce8276-1c50-472e-a41e-44c4406bb924
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Windows NT/2000/XP (loader)
rootnoverify    (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1

===========================

device.map

(hd0)    /dev/sda
(hd1)    /dev/sdb

===========================
fdisk -l

Disk /dev/sdb: 31 MB, 31129600 bytes
255 heads, 63 sectors/track, 3 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0027bda5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1           4       30368+   e  W95 FAT16 (LBA)
Partition 1 has different physical/logical endings:
     phys=(2, 254, 63) logical=(3, 200, 5)



I've tried find /boot/grub/stage1 but I get file not found.

Any help is appreciated.

---

### Post by merlinus on 2009-08-03
Since you are running from the live cd, ubuntu is mounted at /media/disk-1, and so that's where you are finding menu.lst

Try this again and post results:

```
sudo fdisk -l
```

---

### Post by gmclella on 2009-08-03
Thanks Merlinus.   I knew it didn't look right.

sudo fdisk -l

Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x113c113b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3187    25599546    7  HPFS/NTFS
/dev/sda2            3188        3454     2144677+  82  Linux swap / Solaris
/dev/sda3            3455        7831    35158252+  83  Linux
/dev/sda4            7832       11721    31246425   83  Linux

Disk /dev/sdb: 31 MB, 31129600 bytes
255 heads, 63 sectors/track, 3 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0027bda5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1           4       30368+   e  W95 FAT16 (LBA)
Partition 1 has different physical/logical endings:
     phys=(2, 254, 63) logical=(3, 200, 5)

---

### Post by merlinus on 2009-08-03
Which hdd is booting first in bios?  Also run

```
blkid
```

and check the UUID for / with what is in menu.lst.

---

### Post by gmclella on 2009-08-03
blkid
/dev/sdb1: SEC_TYPE="msdos" UUID="9A64-A27C" TYPE="vfat" 

It looks like the UUID is different from the menu.lst.   The menu.lst has the following:
## ## End Default Options ##

title        Ubuntu 9.04, kernel 2.6.28-11-generic
root (hd0,2)
uuid        b0ce8276-1c50-472e-a41e-44c4406bb924
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=**b0ce8276-1c50-472e-a41e-44c4406bb924** ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet


title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
root (hd0,2)
uuid        b0ce8276-1c50-472e-a41e-44c4406bb924
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=**b0ce8276-1c50-472e-a41e-44c4406bb924** ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
root (hd0,2)
uuid**        b0ce8276-1c50-472e-a41e-44c4406bb924**
kernel        /boot/memtest86+.bin
quiet

Should I edit the menu.lst to match the UUID above from blkid?


There's only 1 physical HDD so I don't think it's a BIOS setting.   I believe it's HDD-0 though.  I'll confirm that though.

---

### Post by merlinus on 2009-08-03
You are wanting the UUID for sda3, which is the linux root partition, from what you wrote.

Try 

```
sudo blkid
```to see if you can get it that way.

Another option is to use supergrub to boot linux and reinstall grub.

[http://supergrubdisk.org](http://supergrubdisk.org)

---

### Post by gmclella on 2009-08-03
My bad again.   I keep forgetting sudo!

sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="26A8C5C4A8C5932B" TYPE="ntfs" 
/dev/sda2: UUID="561d889f-6749-4e66-8b75-2c00303c4b8c" TYPE="swap" 
/dev/sda3: UUID="b0ce8276-1c50-472e-a41e-44c4406bb924" TYPE="ext3" 
/dev/sda4: UUID="b09cbe1f-3270-4eb5-9494-a380850215d3" TYPE="ext3" 
/dev/sdb1: SEC_TYPE="msdos" UUID="9A64-A27C" TYPE="vfat" 

The UUID seems to be correct.  I'll take a look at Supergrub.

---

### Post by merlinus on 2009-08-03
You might also try this:

```
sudo grub
root (hd0,2)
setup (hd0)
quit
```

and restart.

---

### Post by gmclella on 2009-08-03
I believe I tried this but might have forgotten the sudo again.   I'll give it a shot.   Looks good so far:
grub> root (hd0,2)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,2)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.


I'll try a restart and cross my fingers.

---

### Post by gmclella on 2009-08-03
No dice.  I'm still getting the Error 15: File not found.

Any other suggestions.   I'll take a look at supergrub now too to see if that will do the trick.

---

### Post by merlinus on 2009-08-03
Did you check hdd boot order?

---

### Post by gmclella on 2009-08-03
There seems to be some progress though, as now when I do 
sudo grub
grub> find /boot/grub/stage1
 (hd0,2)

It seems to be able to find stage 1 now.   This is new.    It still can't seem to find it from the boot loader though.

---

### Post by merlinus on 2009-08-03
When grub appears, press e, and arrow down or over to the boot line.  Make sure it says root (hd0,2).  If not, press e to edit, change root to (hd0,2), and press b to boot.

If this works, then menu.lst will have to be edited to make the change permanent.

---

### Post by gmclella on 2009-08-03
I'll check this on the next reboot.   I'm pretty sure it says root (hd0,2) on the first line.   I manually added this to the menu.lst file already as there wasn't a root entry in the file to begin with.   


I checked the boot order and it was CD-ROM and then HDD-0.

---

### Post by gmclella on 2009-08-03
It says root (hd0,2) after pressing e in the boot menu.   Interestingly enough, when I type 
grub> find /boot/grub/stage1 from the command line in the boot menu it still says Error 15: File not found.   

For whatever reason it can find the file when I do the same thing after booting from LiveCD

---

### Post by presence1960 on 2009-08-03
If that does not work, boot from the Live Cd and when the desktop loads download [BootInfo Script 0.32]("http://sourceforge.net/projects/bootinfoscript/") to the desktop.

Open a termainal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh

```
This will create a RESULTS.txt file on the desktop. paste the entire contents of that file back here. Be sure to highlight all text pasted here and click the # sign on the toolbar at the top. This will place code tags around the text and prevent the text from taking up so much space on the forum.

This script will show us all the commands you ran plus a lot more about your partitions set up and boot process. Let's see exactly what you got there on that rig.

---

### Post by gmclella on 2009-08-03
I'm working on it.   I'm now having issues even booting off the Live CD.

---

### Post by gmclella on 2009-08-06
I think I'm suffering from lack of sleep because it seems every time I touch my computer I make it worse.   I can't seem to boot off the Live CD anymore (keep getting I/O errors) or it asks me for a username and password.   So, I decided to delete my additional partitions making the mistake of not reformatting them first.  So of course now I run into errors on my primary disk while trying to create the new partition.  Argh...
 
Of course my system is too old to boot from USB so that's out, so I'll have to try the alternate ISO or reburn at lower speeds.   Once I get a working disc I plan to just re-format the entire drive - nuke XP and start fresh with Ubuntu.
 
Easier said than done at this point

---

### Post by gmclella on 2009-08-06
Making my first post from Ubuntu!   After formatting the drive and starting fresh it worked without a hitch.  From what I`ve read I decided to go with 8.04 to have a more stable experience.   

I plan on installing XP on a separate partition later - is there anything I should know about it before I start?

---

### Post by merlinus on 2009-08-06
xp needs to be in a primary partition, and preferably the first one on your hdd.  You can use gparted to shrink the linux partition to make a new one, and format it as ntfs so the xp installer will see it.

But make sure you install xp into that partition, and not let it use the entire hdd.

Congratulations, and welcome to the family!

---

