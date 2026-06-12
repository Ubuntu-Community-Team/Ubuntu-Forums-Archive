---
title: "Can't get GRUB 2 to boot Windows XP... any solutions? o.O"
date: 2009-10-14
forum: Installation &amp; Upgrades
---

### Post by hoppipolla on 2009-10-14
Yeah since updating to the Karmic Koala beta I just can't get Windows XP to boot... this wasn't a problem at first but I want to use it for something now and I can't get into it!

Here is my **menu.lst**:

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
default         4

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
# kopt=root=UUID=ffbcbfc7-e7fd-4fbb-aee5-76d25349dce8 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=ffbcbfc7-e7fd-4fbb-aee5-76d25349dce8

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
# howmany=3

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
# updatedefaultentry=true

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu karmic (development branch), kernel 2.6.31-13-generic
uuid		ffbcbfc7-e7fd-4fbb-aee5-76d25349dce8
kernel		/boot/vmlinuz-2.6.31-13-generic root=UUID=ffbcbfc7-e7fd-4fbb-aee5-76d25349dce8 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-13-generic
quiet

title		Ubuntu karmic (development branch), kernel 2.6.31-13-generic (recovery mode)
uuid		ffbcbfc7-e7fd-4fbb-aee5-76d25349dce8
kernel		/boot/vmlinuz-2.6.31-13-generic root=UUID=ffbcbfc7-e7fd-4fbb-aee5-76d25349dce8 ro  single
initrd		/boot/initrd.img-2.6.31-13-generic

title		Ubuntu karmic (development branch), kernel 2.6.31-12-generic
uuid		ffbcbfc7-e7fd-4fbb-aee5-76d25349dce8
kernel		/boot/vmlinuz-2.6.31-12-generic root=UUID=ffbcbfc7-e7fd-4fbb-aee5-76d25349dce8 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-12-generic
quiet

title		Ubuntu karmic (development branch), kernel 2.6.31-12-generic (recovery mode)
uuid		ffbcbfc7-e7fd-4fbb-aee5-76d25349dce8
kernel		/boot/vmlinuz-2.6.31-12-generic root=UUID=ffbcbfc7-e7fd-4fbb-aee5-76d25349dce8 ro  single
initrd		/boot/initrd.img-2.6.31-12-generic

title		Ubuntu karmic (development branch), kernel 2.6.31-11-generic
uuid		ffbcbfc7-e7fd-4fbb-aee5-76d25349dce8
kernel		/boot/vmlinuz-2.6.31-11-generic root=UUID=ffbcbfc7-e7fd-4fbb-aee5-76d25349dce8 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-11-generic
quiet

title		Ubuntu karmic (development branch), kernel 2.6.31-11-generic (recovery mode)
uuid		ffbcbfc7-e7fd-4fbb-aee5-76d25349dce8
kernel		/boot/vmlinuz-2.6.31-11-generic root=UUID=ffbcbfc7-e7fd-4fbb-aee5-76d25349dce8 ro  single
initrd		/boot/initrd.img-2.6.31-11-generic

title		Ubuntu karmic (development branch), memtest86+
uuid		ffbcbfc7-e7fd-4fbb-aee5-76d25349dce8
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1
```


Cheers guys, this has got me most confuzzled! :)


Hoppi!

---

### Post by tommcd on 2009-10-14
Grub2 no longer uses /boot/grub/menu.lst. Grub2 uses /boot/grub/grub.cfg, which you are not supposed to edit.
Anyway, it looks like you did not completely update to grub2, you may be chainloading grub2 from grub legacy. Follow this tutorial in the wiki about upgrading from grub legacy to grub2:
[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)
Here is another good tutorial on grub2:
[http://members.iinet.net/~herman546/p20.html](http://members.iinet.net/~herman546/p20.html)
I'm still trying to get up to speed with grub2 myself.

---

### Post by hoppipolla on 2009-10-14
> **tommcd said:**
> Grub2 no longer uses /boot/grub/menu.lst. Grub2 uses /boot/grub/grub.cfg, which you are not supposed to edit.
Anyway, it looks like you did not completely update to grub2, you may be chainloading grub2 from grub legacy. Follow this tutorial in the wiki about upgrading from grub legacy to grub2:
[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)
Here is another good tutorial on grub2:
[http://members.iinet.net/~herman546/p20.html](http://members.iinet.net/~herman546/p20.html)
I'm still trying to get up to speed with grub2 myself.

ah ok, yeah when I run "grub --version" it just tells me it's 0.97...

Ok I'll try that tutorial :)


EDIT -- Done. I'll see if it works on next boot :)

---

### Post by hoppipolla on 2009-10-14
Thanks for the help tommcd but still nothing from Windows ._.

It just gives me a flashing line like at the prompt and absolutely no life at all.

I wonder where the problem is ._.

---

### Post by falconindy on 2009-10-14
> **hoppipolla said:**
> Thanks for the help tommcd but still nothing from Windows ._.

It just gives me a flashing line like at the prompt and absolutely no life at all.

I wonder where the problem is ._.
Post the output of `sudo fdisk -l`. I suspect the pointer (hd0,0) isn't actually pointing to your Windows bootloader.

---

### Post by hoppipolla on 2009-10-15
> **falconindy said:**
> Post the output of `sudo fdisk -l`. I suspect the pointer (hd0,0) isn't actually pointing to your Windows bootloader.

```
Disk /dev/sda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x31993198

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2946    23662768+   7  HPFS/NTFS
/dev/sda2            2947        4863    15398302+   5  Extended
/dev/sda5            2947        4777    14707476   83  Linux
/dev/sda6            4778        4863      690763+  82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8a898a89

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4865    39078081   83  Linux
```

To be honest I've got NO idea what that Extended partition is at /dev/sda2 but anyway lol

Yeah so Windows is on sda1, Ubuntu is on sda5 and my  second disk I just use for whatever really, it hasn't got an OS on it.

Any thoughts? :-S  Anything else you want me to post here? GRUB 2 did seem to detect Windows XP ok =S

---

### Post by tommcd on 2009-10-15
> **hoppipolla said:**
> 
To be honest I've got NO idea what that Extended partition is at /dev/sda2 but anyway lol
Yeah so Windows is on sda1, Ubuntu is on sda5... 
Any thoughts? :-S  Anything else you want me to post here? GRUB 2 did seem to detect Windows XP ok =S
Your /sda2 is an extended partition that contains the logical partitions /dev/sda5 and /dev/sda6.
If you have successfully upgraded to grub2 you should be able to just rub:
```
sudo update-grub
```
and it should list that it is detecting all your operating systems one by one. Then when you reboot Windows XP should be there. If not, then post what happens when you run "sudo update-grub".

---

### Post by hoppipolla on 2009-10-15
> **tommcd said:**
> Your /sda2 is an extended partition that contains the logical partitions /dev/sda5 and /dev/sda6.
If you have successfully upgraded to grub2 you should be able to just rub:
```
sudo update-grub
```
and it should list that it is detecting all your operating systems one by one. Then when you reboot Windows XP should be there. If not, then post what happens when you run "sudo update-grub".

Oh I see :)

And yes Windows XP has always been in the list, it just doesn't boot. My friend pointed out recently that it's probably just a problem with XP itself as opposed to GRUB, so I'm going to try recovering it and reinstalling GRUB afterwards from the Ubuntu CD :)

Additionally, I changed the bootable partition on my hard disk from sda1 to sda5 (the Ubuntu logical partition) ... is this ok? My friend said I should but I really don't know if it's ok set to a logical partition? It boots fine :)

Thanks guys for your time and help, I'll let you know how I get on with this way of dealing with it ^_^

---

### Post by hoppipolla on 2009-10-16
It works :)

I actually ended up reinstalling XP completely, and then reinstalled GRUB, and it's totally fine! It must have been a problem with Windows itself!

Thanks so much for the help guys, and now at least I can run the few apps I have that need to run on Windows!

See you round,

Hoppi ^_^

---

### Post by tommcd on 2009-10-16
> **hoppipolla said:**
> 
I actually ended up reinstalling XP completely, and then reinstalled GRUB, and it's totally fine! It must have been a problem with Windows itself!

Glad you got it fixed.
I should have thought of that since the same thing happened to me once. I installed Ubuntu onto a hard drive that had XP on it. I could not figure out why grub failed to detect XP during the Ubuntu install. It turns out the XP was corrupted and needed to be reinstalled. Then grub found it with no problem.

---

### Post by hoppipolla on 2009-10-16
> **tommcd said:**
> Glad you got it fixed.
I should have thought of that since the same thing happened to me once. I installed Ubuntu onto a hard drive that had XP on it. I could not figure out why grub failed to detect XP during the Ubuntu install. It turns out the XP was corrupted and needed to be reinstalled. Then grub found it with no problem.

ah well, well it's set up now with no issues :)

I am going to ask this question in the Community Cafe too but - is there any way I can run my Windows partition from within my Ubuntu desktop? Like a VM but... the preinstalled XP on the other partition o.O

Sounds weird I know but it would save me logging out all the time xD

---

### Post by tommcd on 2009-10-16
You can install XP in Ubuntu in virtualbox or other virtualization software like VMware. I don't know if that will allow you to load the XP you have on your hard drive though. I suspect that it would be like a clean install, but just in a virtual machine. 
I have never done a VM install though, so I am the wrong person to ask.

---

### Post by hoppipolla on 2009-10-16
> **tommcd said:**
> You can install XP in Ubuntu in virtualbox or other virtualization software like VMware. I don't know if that will allow you to load the XP you have on your hard drive though. I suspect that it would be like a clean install, but just in a virtual machine. 
I have never done a VM install though, so I am the wrong person to ask.

ok no worries :)  I'll give it a go in a mo i think! :)

---

