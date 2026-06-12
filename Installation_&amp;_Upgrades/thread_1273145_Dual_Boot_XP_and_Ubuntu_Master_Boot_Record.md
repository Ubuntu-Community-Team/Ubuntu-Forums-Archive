---
title: "Dual Boot XP and Ubuntu Master Boot Record"
date: 2009-09-23
forum: Installation &amp; Upgrades
---

### Post by mecv on 2009-09-23
Hi,
I have recently installed ubuntu for the first time, in my laptop which has been running with XP for Dual Booting, so I made a few mistakes, and so I've decided to reinstall ubuntu. But when I did and everything is now working, I realized that at the start of booting (time when you are asked to choose which OS to run), there are two entries of Ubuntu. I assumed that one for each installation.

It seems as if everything is working properly but it just feels a bit awkward that there are redundant entries of Ubuntu.

So Does anyone know how to fix this. It has something to do with the master boot record.

Thanks all.

---

### Post by jammen33 on 2009-09-23
When Ubuntu installs it creates two entries the regular and a recovery. If that is the two entries then all is fine, if not then you can edit the boot list if it really bothers you by running this command:

sudo gedit /boot/grub/menu.lst

but be careful, removing the wrong entry can mess up your computer

---

### Post by tommcd on 2009-09-23
When you reinstalled Ubuntu did you install it on the same partition as the previous install? In other words, did you reformat the partition that Ubuntu was previously installed on and install Ubuntu on the same partition? Or did you reinstall Ubuntu to a new partition, in which case the old install of Ubuntu would remain?

Can you post the output of:
```
sudo fdisk -l
```
This will list your partitions. And also post everything after the line:
## End Default Options ##
in the /boot/grub/menu.lst file.

---

### Post by mecv on 2009-09-23
I deleted the old partition, but created a new one at the same logiccal drive. 

Thanks for the info.

---

### Post by mecv on 2009-09-23
here's what it says...
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4864    39070048+   7  HPFS/NTFS
/dev/sda2            4865        9729    39078112+   5  Extended
/dev/sda5            4865        5113     2000061   82  Linux swap / Solaris
/dev/sda6            5114        9729    37077988+  83  Linux

---

### Post by mecv on 2009-09-23
> **jammen33 said:**
> When Ubuntu installs it creates two entries the regular and a recovery. If that is the two entries then all is fine, if not then you can edit the boot list if it really bothers you by running this command:

sudo gedit /boot/grub/menu.lst

but be careful, removing the wrong entry can mess up your computer


It creates two sets of "Ubuntu general" and "Ubuntu recovery"

---

### Post by jammen33 on 2009-09-23
as tommcd said> **tommcd said:**
> And also post everything after the line:
## End Default Options ##
in the /boot/grub/menu.lst file.

---

### Post by mecv on 2009-09-23
The command sudo fdisk -l
shows :
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x13631362

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4864    39070048+   7  HPFS/NTFS
/dev/sda2            4865        9729    39078112+   5  Extended
/dev/sda5            4865        5113     2000061   82  Linux swap / Solaris
/dev/sda6            5114        9729    37077988+  83  Linux

at the console.
how do i access /boot/... file again?

---

### Post by mecv on 2009-09-23
Sorry, I found it.... here goes...

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
# kopt=root=UUID=3790c3df-f878-42b8-a7a2-8be475881a70 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=3790c3df-f878-42b8-a7a2-8be475881a70

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

title        Ubuntu 9.04, kernel 2.6.28-15-generic
uuid        3790c3df-f878-42b8-a7a2-8be475881a70
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=3790c3df-f878-42b8-a7a2-8be475881a70 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid        3790c3df-f878-42b8-a7a2-8be475881a70
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=3790c3df-f878-42b8-a7a2-8be475881a70 ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        3790c3df-f878-42b8-a7a2-8be475881a70
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=3790c3df-f878-42b8-a7a2-8be475881a70 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        3790c3df-f878-42b8-a7a2-8be475881a70
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=3790c3df-f878-42b8-a7a2-8be475881a70 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        3790c3df-f878-42b8-a7a2-8be475881a70
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


thats it

---

### Post by jammen33 on 2009-09-23
```
sudo gedit /boot/grub/menu.lst
```

---

### Post by jammen33 on 2009-09-23
When Ubuntu updates the kernel it leaves the old version so if the new version breaks something you can go back to the old version.

The top option is the newest version
"Ubuntu 9.04, kernel 2.6.28-15-generic"

and further down is older versions
"Ubuntu 9.04, kernel 2.6.28-11-generic"

if you want you can delete the older version or you can just ignore it.


title Ubuntu 9.04, kernel 2.6.28-11-generic
uuid 3790c3df-f878-42b8-a7a2-8be475881a70
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=3790c3df-f878-42b8-a7a2-8be475881a70 ro quiet splash
initrd /boot/initrd.img-2.6.28-11-generic
quiet

title Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid 3790c3df-f878-42b8-a7a2-8be475881a70
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=3790c3df-f878-42b8-a7a2-8be475881a70 ro single
initrd /boot/initrd.img-2.6.28-11-generic

---

### Post by mecv on 2009-09-23
Ah... I see... How do you know which one is the older one? They look the same to me...

---

### Post by mecv on 2009-09-23
I get it **15** and **11**... okay thanks you very much...

---

### Post by jammen33 on 2009-09-23
The name says the kernel version "Ubuntu 9.04, **kernel 2.6.28-15-generic**"
The higher number is the newer version

---

### Post by tommcd on 2009-09-23
It is always good to leave one backup kernel in place in the grub menu. That way if your current kernel gets corrupted, or a newer kernel won't boot for what ever reason, then you can still boot the old one and then troubleshoot the problem with the new kernel.

---

### Post by presence1960 on 2009-09-23
```
## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		00c044ae-b749-4eb1-bedf-90ad5c6c054c
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=00c044ae-b749-4eb1-bedf-90ad5c6c054c ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		00c044ae-b749-4eb1-bedf-90ad5c6c054c
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=00c044ae-b749-4eb1-bedf-90ad5c6c054c ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		00c044ae-b749-4eb1-bedf-90ad5c6c054c
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=00c044ae-b749-4eb1-bedf-90ad5c6c054c ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		00c044ae-b749-4eb1-bedf-90ad5c6c054c
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=00c044ae-b749-4eb1-bedf-90ad5c6c054c ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

#title		Ubuntu 9.04, kernel 2.6.28-11-generic
#uuid		00c044ae-b749-4eb1-bedf-90ad5c6c054c
#kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=00c044ae-b749-4eb1-bedf-90ad5c6c054c ro quiet splash 
#initrd		/boot/initrd.img-2.6.28-11-generic
#quiet

#title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
#uuid		00c044ae-b749-4eb1-bedf-90ad5c6c054c
#kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=00c044ae-b749-4eb1-bedf-90ad5c6c054c ro  single
#initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		00c044ae-b749-4eb1-bedf-90ad5c6c054c
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

or you can comment out (#) the kernels you don't want to see on the GRUB menu. They will still be installed and all you need to do is uncomment them if you need to use them. If your machine won't boot you can uncomment them from the Live Cd, then reboot & choose that kernel.

I always leave the 2 most recent visible in the GRUB menu and comment out the others. I don't uninstall them since space is not an issue for me.

---

### Post by raymondh on 2009-09-23
After practicing your editing skills (and learning),  you may also want to check out startupmanager (found in synaptic).  It is GUI-based and in there, you can set defaults, time, etc.  SUM also writes to the menu.lst.

It is always good to learn the manual editing first.  That way, you can repair anytime using the liveCD.   Am just showing what I call the "lazy" way ;)

Happy Ubuntu-ing.

[Reference materials to learn more about GRUB]("http://members.iinet.net.au/~herman546/p15.html")

---

