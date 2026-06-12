---
title: "Trouble re-installing Windows"
date: 2009-06-13
forum: Installation &amp; Upgrades
---

### Post by okayneil on 2009-06-13
Hey guys, 

sadly I need to re-install windows xp, so I want to do a dual boot. I followed the instructions[ given here]("http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm") to the T but cant seem to get windows to install. 

Currently I have ubuntu 9.04 only installed. 

I created a 20GB primary partition and formatted it to NTFS but when I run the windows CD its telling me that no hard drives were recognized so it cancels the setup. 

Any ideas?

Cheers :)

---

### Post by b.a.w on 2009-06-13
Did you format it to NTFS from ubuntu? Windows might not like that and decides not to recognize it. What happens if you run the cd with the drive unformatted? Does it recognize it then?

---

### Post by okayneil on 2009-06-13
> **b.a.w said:**
> Did you format it to NTFS from ubuntu? Windows might not like that and decides not to recognize it. What happens if you run the cd with the drive unformatted? Does it recognize it then?

First tried it with an unformatted drive, then formatted it to NTFS and gave it a go, both dont work :(

I even used gparted live cd to do the formatting.

---

### Post by AllenGG on 2009-06-13
Having gone this route in the past I'm surprised that "Windows" did not attempt to reformat your hard drive. Usually Windows treats a Linux installation as "foreign matter"
From personal experience you will have to:
1. reformat the drive, or
2. create a "virtual machine", VMWare should be in your "Synaptic"

---

### Post by okayneil on 2009-06-13
I figured out the problem, SATA support. Just disabled it in setup. 

Got a fresh problem though, having install windows xp, its not showing up in grub after I re-installed grub. Now I cant boot into windows, obviously I have to edit the grub menu, but dont know what to put in, any ideas?

yo

---

### Post by okayneil on 2009-06-13
```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0008d9b3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       11384    91441948+  83  Linux
/dev/sda2   *       11385       13995    20972857+   7  HPFS/NTFS
/dev/sda3           13996       14593     4803435    5  Extended
/dev/sda5           13996       14593     4803403+  82  Linux swap / Solaris
```

Thats my system/ drive config and here is grub: 

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
# kopt=root=UUID=eaeb177d-ad56-47e4-b35c-f1f8a5665f77 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=eaeb177d-ad56-47e4-b35c-f1f8a5665f77

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
uuid        eaeb177d-ad56-47e4-b35c-f1f8a5665f77
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=eaeb177d-ad56-47e4-b35c-f1f8a5665f77 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        eaeb177d-ad56-47e4-b35c-f1f8a5665f77
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=eaeb177d-ad56-47e4-b35c-f1f8a5665f77 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        eaeb177d-ad56-47e4-b35c-f1f8a5665f77
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by merlinus on 2009-06-13
You might try adding this to the very end of menu.lst:

title        Windows XP
root        (hd0,1)
makeactive
chainloader    +1

---

### Post by okayneil on 2009-06-13
> **merlinus said:**
> You might try adding this to the very end of menu.lst:

title        Windows XP
root        (hd0,1)
makeactive
chainloader    +1

Thanks mate, worked a treat ;)

---

### Post by merlinus on 2009-06-13
Glad to hear it!  Happy ubuntuing...

---

