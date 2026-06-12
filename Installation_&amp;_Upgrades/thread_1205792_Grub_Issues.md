---
title: "Grub Issues"
date: 2009-07-06
forum: Installation &amp; Upgrades
---

### Post by Alpaca on 2009-07-06
Hey guys,

I've done a few Ubuntu installs before, but this one tottally went over my head.

So heres the situation.

I'm running a thinkpad t61, with the recovery partition still there (The last few times I've dual booted on this laptop, I didn't have the recovery partition.) The reveovery partition is a stripped down version of Vista, and shows up as such in Ubuntu's installer.

What I intended to do, was dual boot Windows 7, and Ubuntu. I had Windows 7 installed first, along with the hidden Vista recovery partition, so all in all, it's a tri-boot.

Heres what I did, I used Windows 7 disk management to shrink it's partition by 20 gigs, I then installed ubuntu to the free 20 gigs of space. Ubuntu runs perfectly fine.

So the partitions are: the recovery partition is (0,0), a small, 100 meg extra patition that I believe belongs to Windows 7 is (0,1), Windows 7 itself is (0,3) and Ubuntu is (0,4).

Now, I couldn't boot into Windows 7, which I expected. So I added the appropriate entry to Menu.lst:

[quote="Menu.lst"]
title        Windows 7
rootnoverify    (hd0,3)
savedefault
makeactive
chainloader    +1
[/quote]

However, I get an error "Invalid boot device" or something along that lines.

So, for S&G's, I added:

[quote="menu.lst"]
title        Potential Windows 7
rootnoverify    (hd0,2)
savedefault
makeactive
chainloader    +1
[/quote]

Which magically worked, however it also gives me the "Boot Manager is Missing CTRL-ALT-DEL to reset"

Which means I gotta run FixMbr in windows, however, I've misplaced my Windows 7 disk, so I'm downloading another ISO.

However, out of curiosity, could this be result of how I set up menu.lst? I've included my Menu.lst file and the results of a fdisk -l:

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
# kopt=root=UUID=7c511d34-16f2-4e86-99b2-c7c05e12e854 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=7c511d34-16f2-4e86-99b2-c7c05e12e854

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

title        Ubuntu 9.04
uuid        7c511d34-16f2-4e86-99b2-c7c05e12e854
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=7c511d34-16f2-4e86-99b2-c7c05e12e854 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04 (recovery mode)
uuid        7c511d34-16f2-4e86-99b2-c7c05e12e854
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=7c511d34-16f2-4e86-99b2-c7c05e12e854 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        7c511d34-16f2-4e86-99b2-c7c05e12e854
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista (Recovery)
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows 7
rootnoverify    (hd0,3)
savedefault
makeactive
chainloader    +1

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Potential Windows 7
rootnoverify    (hd0,2)
savedefault
makeactive
chainloader    +1

``````

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf3d23cb0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1305    10477568   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2            1305        1318      102400    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3   *        1318       27791   212644864    7  HPFS/NTFS
Partition 3 does not end on cylinder boundary.
/dev/sda4           27792       30401    20964825    5  Extended
/dev/sda5           27792       30287    20049088+  83  Linux
/dev/sda6           30288       30401      915673+  82  Linux swap / Solaris
Note: sector size is 4096 (not 512)

Disk /dev/sdb: 79.8 GB, 79824777216 bytes
26 heads, 50 sectors/track, 14991 cylinders
Units = cylinders of 1300 * 4096 = 5324800 bytes
Disk identifier: 0x20202020

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14992    77953628    b  W95 FAT32

```Thanks for any help!

---

### Post by frenkel on 2009-07-06
Grub numbers the devices from 0 upwards. The linux kernel numbers from 1 upwards. This means your sda3 device is (hd0,2), so that is where your Windows 7 is located. I don't know about the "Boot Manager is Missing CTRL-ALT-DEL to reset", but it's not a Grub problem.

---

### Post by ronparent on 2009-07-06
I am frankly totaly confused by what I currently see with my own win 7 install. In a prior install of win 7 on another drive the root I needed to reference in grub to boot it was a special small (100Mb Reserved) partition created by win 7 on install. In my current installation a simular 100 Mb partitions was created by my current win 7 install, but, to boot it I have to refer to my sda1 - (hd0,0) -as the root to boot win 7? I haven't yet taken the time to investigate, but, in my case, the win 7 root is the same partition as my win xp?? 

So, before you fixmbr you might want to edit the grub menu on boot to see if you can locate the proper win 7 root to boot it from. In any event running fixmrb now may well muck up your grub install. Probably your best bet is to see if a temporary edit of the grub will find a fix.

---

