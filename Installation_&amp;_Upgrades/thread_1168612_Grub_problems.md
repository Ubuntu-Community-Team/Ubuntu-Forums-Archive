---
title: "Grub problems"
date: 2009-05-24
forum: Installation &amp; Upgrades
---

### Post by retired_dictator on 2009-05-24
I am dual-booting ubuntu Jaunty and Win XP and It worked fine until I tried removing grub and installing gfxGrub, it didn't work well so I removed gfxgGrub and I reinstalled grub again, guess what? the OS list is gone and It shows a mini-Bash like thing:

    ```
   [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> 

```
erm...help? =P
(I am using the Intrepid Live CD now)

---

### Post by presence1960 on 2009-05-24
open a terminal and run ```
sudo fdisk -l
``` BTW that is a lowercase L. Post the output here.

also open a terminal and run ```
gksu gedit /boot/grub/menu.lst
``` That is a lowercase L in .lst. Post that output also.

P.S. that text you posted in code tags is the exact text that comes up when you try to restore GRUB after the command sudo grub. That will not list your OS(s)

---

### Post by retired_dictator on 2009-05-24
sudo fdisk -l
```
Disk /dev/sda: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x33d133d0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sda2            3825        7476    29334690    f  W95 Ext'd (LBA)
/dev/sda5            3825        7383    28587636   83  Linux
/dev/sda6            7384        7476      746991   82  Linux swap / Solaris

```

menu.lst
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
# kopt=root=UUID=14685363-382b-4d51-a2fd-aa6c5c3bf0d8 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=14685363-382b-4d51-a2fd-aa6c5c3bf0d8

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
uuid		14685363-382b-4d51-a2fd-aa6c5c3bf0d8
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=14685363-382b-4d51-a2fd-aa6c5c3bf0d8 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		14685363-382b-4d51-a2fd-aa6c5c3bf0d8
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=14685363-382b-4d51-a2fd-aa6c5c3bf0d8 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		14685363-382b-4d51-a2fd-aa6c5c3bf0d8
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professionnel
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

---

### Post by presence1960 on 2009-05-24
your menu.lst looks ok. How did you try restoring GRUB? Try this : 

```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or 
   whatever your hard disk + partition # is, to install GRUB to a 
   partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.

```

At # 5 use root (hd0,4)
At # 6 I would restore GRUB to MBR by using ```
setup (hd0)
```

---

### Post by retired_dictator on 2009-05-24
```
grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  15 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+15 p (hd0,4)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

```

After all It shows an error when I roboot (error 2)
> # 2 : "Selected disk doesn't exist"

This error is returned if the device part of a device- or full filename refers to a disk or BIOS device that is not present or not recognized by the BIOS in the system.

**Quoted from: [http://www.uruk.org/orig-grub/errors.html](http://www.uruk.org/orig-grub/errors.html)**


---

### Post by presence1960 on 2009-05-24
I am running Jaunty and I just restored GRUB to compare your output to mine. The only differences that I can see is I have 17 sectors embedded where you have 15. The procedure I posted should have restored GRUB unless you removed more than just the other GRUB package when you uninstalled it. I would say hang tight for now and maybe someone else will come along that can see something I can't see. In the worst case scenario you can reinstall Ubuntu.

---

### Post by retired_dictator on 2009-05-24
I don't want to lose my files.
bah, I'll just wait then.. :(

---

### Post by ocean223 on 2009-05-24
Go here: [http://users.bigpond.net.au/hermanzone/p15.htm#First_method:_direct_kernel_boot.]("http://users.bigpond.net.au/hermanzone/p15.htm#First_method:_direct_kernel_boot.")

The second method worked for me, but I still need a solution to repair GRUB. :)

---

### Post by retired_dictator on 2009-05-24
I tried fixing Grub with the Super Grub Disk and it won't work, but I can boot to Jaunty now.
thanks for the link, ocean

[COLOR="Red"]EDIT:[/COLOR]**I just realized this, when I typed "root (hd0,4)" It doesn't show the filesystem In that partition **

---

### Post by ocean223 on 2009-05-24
Glad it worked for you. Now if I could only fix it so that I don,t have to boot it manually............;)

---

### Post by rettsin on 2009-05-25
presence1960,
I was having a grub error 21 problem until I read your answer to "Re: grub problems". I just wanted to say a hearty thank you! I have been working on error 21 for 2 days, every waking moment outside of work and finally I can rest a little. I think you're great.

rettsin

---

### Post by presence1960 on 2009-05-25
Glad you got it working. Enjoy Ubuntu & the rest of the holiday.

---

### Post by the_legendary_saiyajin on 2009-05-27
Im having trouble with getting grub to install, whenever it gets to grub with jaunty it has a fatal error and ubiquity closes. it looks like evertyhing is there for the jaunty when i boot into a live cd but i dont know if everything grub needs is there. any advice on a solution to this would be useful as i dont know how to install grub again

---

