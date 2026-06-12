---
title: "can't load windows XP"
date: 2009-06-21
forum: Installation &amp; Upgrades
---

### Post by LeoKhk on 2009-06-21
Hi,
I'm a bit new to Linux as a whole. Recently, i got onboard the new Ubuntu-wagon and installed Ubuntu 9.04 on my computer as an additional OS next to Windows XP SP2. Then, i came across this Linux-based application called Wine but realized that i had very little space to install windows applications on Ubuntu. So, I formatted my Linux partition to redistribute memory to the root, home and swap partition. I didn't touch any of the windows partition. 
 
Now, after reinstalling Ubuntu, I can't load Windows Xp anymore. When i choose windows xp on the Grub loader, it just gets back to the same OS list. Only Ubuntu loads properly.
 
Plz help!!!!! Coz i want my migration from windows to Linux to take some time.
:(

---

### Post by merlinus on 2009-06-21
Open a terminal, and post results of these two commands:

```

sudo fdisk -l
cat /boot/grub/menu.lst

```

---

### Post by LeoKhk on 2009-06-21
**Result for sudo fdisk -l** 
 
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe947e947
Device Boot Start End Blocks Id System
/dev/sda1 * 1 3079 24732036 c W95 FAT32 (LBA)
/dev/sda2 3080 9729 53416125 f W95 Ext'd (LBA)
/dev/sda5 3080 4619 12370018+ b W95 FAT32
/dev/sda6 4620 6149 12289693+ b W95 FAT32
/dev/sda7 6150 8581 19535008+ b W95 FAT32
/dev/sda8 8582 9019 3518203+ 83 Linux
/dev/sda9 9020 9461 3550333+ 83 Linux
/dev/sda10 9462 9729 2152678+ 82 Linux swap / Solaris
 
 
 
**Result for cat /boot/grub/menu.lst**
 
# menu.lst - See: grub(8 ), info grub, update-grub(8 )
# grub-install(8 ), grub-floppy(8 ),
# grub-md5-crypt, /usr/share/doc/grub
# and /usr/share/doc/grub-doc/.
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default 0
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 10
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu
# Pretty colours
#color cyan/blue white/blue
## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line) and entries protected by the
# command 'lock'
# e.g. password topsecret
# password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret
#
# examples
#
# title Windows 95/98/NT/2000
# root (hd0,0)
# makeactive
# chainloader +1
#
# title Linux
# root (hd0,1)
# kernel /vmlinuz root=/dev/hda2 ro
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
## kopt_2_6_8=root=/dev/hdc1 ro
## kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=6ba224a1-e1a1-4021-a98f-2bedf2d16ed7 ro
## default grub root device
## e.g. groot=(hd0,0)
# groot=6ba224a1-e1a1-4021-a98f-2bedf2d16ed7
## should update-grub create alternative automagic boot options
## e.g. alternative=true
## alternative=false
# alternative=true
## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
## lockalternative=false
# lockalternative=false
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash
## should update-grub lock old automagic boot options
## e.g. lockold=false
## lockold=true
# lockold=false
## Xen hypervisor options to use with the default Xen boot option
# xenhopt=
## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0
## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
## altoptions=(recovery) single
# altoptions=(recovery mode) single
## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
## howmany=7
# howmany=all
## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
## indomU=true
## indomU=false
# indomU=detect
## should update-grub create memtest86 boot option
## e.g. memtest86=true
## memtest86=false
# memtest86=true
## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false
## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false
## ## End Default Options ##
title Ubuntu 9.04, kernel 2.6.28-11-generic
uuid 6ba224a1-e1a1-4021-a98f-2bedf2d16ed7
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=6ba224a1-e1a1-4021-a98f-2bedf2d16ed7 ro quiet splash 
initrd /boot/initrd.img-2.6.28-11-generic
quiet
title Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid 6ba224a1-e1a1-4021-a98f-2bedf2d16ed7
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=6ba224a1-e1a1-4021-a98f-2bedf2d16ed7 ro single
initrd /boot/initrd.img-2.6.28-11-generic
title Ubuntu 9.04, memtest86+
uuid 6ba224a1-e1a1-4021-a98f-2bedf2d16ed7
kernel /boot/memtest86+.bin
quiet
### END DEBIAN AUTOMAGIC KERNELS LIST
# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root
 
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Microsoft Windows XP Professional
rootnoverify (hd0,0)
savedefault
chainloader +1
 
 
**P.S: I heavily depend on AutoCAD 2009 for my work and unfortunately it does not work well when installed on Linux using Wine. Also QCAD in Linux is no substitute for AutoCAD. So plz, I need XP to work on my computer for the moment.**

---

### Post by merlinus on 2009-06-21
The xp entry in menu.lst is correct.  It may be that things changed, however, when you resized partitions.  Which one is / on, sda8 or sda9?

If you do not remember, 

```

df -h

```will tell you.

Also, run this command to make sure that the uuid did not change:

```

sudo blkid

```Then we can try reinstalling grub.

If that does not work, then you may have to use supergrub or your xp disk to fixmbr, and then reinstall grub.

---

### Post by swerdna on 2009-06-21
That look correct except perhaps take out the line "savedefault" to make it like this:
> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Microsoft Windows XP Professional
rootnoverify (hd0,0)
chainloader +1
If that doesn't work, check in the partition sda1 (by mounting it) that it contains these two files ntldr and boot.ini

---

### Post by merlinus on 2009-06-21
Good point!  You also might change it to:

title Window XP
root (hd0,0)
makeactive
chainloader +1

---

### Post by swerdna on 2009-06-21
> **merlinus said:**
> Good point!  You also might change it to:

title Window XP
root (hd0,0)
makeactive
chainloader +1

That's not necessary because the asterisk beside sda1 in the return received from "fdisk -l" shows that sda1 is already active.

---

### Post by LeoKhk on 2009-06-22
**Here's the output for:  df -h**
 
[FONT=Times New Roman][SIZE=3]/dev/loop0: TYPE="squashfs" [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]/dev/sda1: LABEL="WINXP" UUID="94C2-AC80" TYPE="vfat" [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]/dev/sda5: UUID="B48A-B31F" TYPE="vfat" [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]/dev/sda6: LABEL="BISHWA CHAU" UUID="AC9C-24AB" TYPE="vfat" [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]/dev/sda7: LABEL="BACKUP" UUID="84A5-DD95" TYPE="vfat" [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]/dev/sda8: UUID="e7185a1c-d4b4-4df3-a19f-e23e903214fa" TYPE="ext3" [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]/dev/sda9: UUID="f9a93594-a3b8-4646-9f7c-c199af38e577" TYPE="ext3" [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman]/dev/sda10: UUID="93c6e66b-20dc-4d1b-90ae-f0f77cc967bb" TYPE="swap" [/FONT]
[FONT=Times New Roman][/FONT] 
[FONT=Times New Roman][/FONT] 
[FONT=Times New Roman]**And here's the output for:    sudo blkid**[/FONT]
[FONT=Times New Roman][/FONT] 
[FONT=Times New Roman]/dev/loop0: TYPE="squashfs" 

/dev/sda1: LABEL="WINXP" UUID="94C2-AC80" TYPE="vfat" 

/dev/sda5: UUID="B48A-B31F" TYPE="vfat" 

/dev/sda6: LABEL="BISHWA CHAU" UUID="AC9C-24AB" TYPE="vfat" 

/dev/sda7: LABEL="BACKUP" UUID="84A5-DD95" TYPE="vfat" 

/dev/sda8: UUID="e7185a1c-d4b4-4df3-a19f-e23e903214fa" TYPE="ext3" 

/dev/sda9: UUID="f9a93594-a3b8-4646-9f7c-c199af38e577" TYPE="ext3" 

[FONT=Times New Roman]/dev/sda10: UUID="93c6e66b-20dc-4d1b-90ae-f0f77cc967bb" TYPE="swap" [/FONT]
[FONT=Times New Roman][/FONT] 
[FONT=Times New Roman][/FONT] 
[FONT=Times New Roman]**PS: I hope you guys understand my case. The GRUB loader loads normally when PC is started. But when i select XP, it gets back to the same OS menu. Only Ubuntu loads normally.**[/FONT]
[FONT=Times New Roman][/FONT] 
[FONT=Times New Roman]**PS: PS: **[/FONT][FONT=Times New Roman]**I really appreciate all the help i'm getting. Thank you very much! :D**[/FONT][/FONT]

---

