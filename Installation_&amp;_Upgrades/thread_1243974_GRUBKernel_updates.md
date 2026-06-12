---
title: "GRUB/Kernel updates"
date: 2009-08-18
forum: Installation &amp; Upgrades
---

### Post by jkgoose937 on 2009-08-18
I'm noticing that every time there is a kernel update and my menu.lst file gets updated I get "Error 11 Unrecognized Device String". The only easy fix I've found, is to make sure I have a backup of menu.lst that doesn't include the updated kernel in the list. I'm not sure if this is a Ubuntu or a GRUB issue. If someone wants to put some thoughts down...

---

### Post by Herman on 2009-08-19
Error 11 is usually caused by some kind of syntax error or typo or spelling mistake in your booting stanza.
The fact that this error is noticed right after kernel updates suggests there might be an error of some kind somewhere in the Debian Automagic Kernels List area of your menu.lst file which is causing your problem to re-occur.
 What version of GRUB are you using? Can it handle booting by file system UUID numbers?

---

### Post by presence1960 on 2009-08-19
I remember getting those errors on Hardy when I would upgrade kernels. hardy's GRUB uses root (hdx,y) instead of UUIDs. I have an IDE HDD and a SATA. For some reason UBUNTU always lists the IDE as sda even though it was set in BIOS as second boot disk in hard disk boot order. There is the cause of the problem because Ubuntu reads the IDE as (hd0) but in actuality it is (hd1). so everytime my kernel upgraded I had to boot from the live CD and change the settings for root (hdx,y) in menu.lst because they were always incorrect. When using the root (hdx,y) method you need to use the order of the disks in BIOS, which may not necessarily be how fdisk reports them to be.

This continues on in Jaunty, but only in reference to chainloading. jaunty's GRUB uses UUIDs for the kernel lines now.

---

### Post by jkgoose937 on 2009-08-26
> **Herman said:**
> Error 11 is usually caused by some kind of syntax error or typo or spelling mistake in your booting stanza.
The fact that this error is noticed right after kernel updates suggests there might be an error of some kind somewhere in the Debian Automagic Kernels List area of your menu.lst file which is causing your problem to re-occur.
 What version of GRUB are you using? Can it handle booting by file system UUID numbers?
Not too sure which version GRUB I'm using it's the one that comes with 9.04 or if there where any updates since I really don't know. I think I know what the UUID numbers are, like if I use [c,b, or something else] it gives the submenu for that listing, it states like "must load kernal" or something like that. Sorry for the vagueness, but it's been a while since I installed the a new kernal. I just know now not too update the kernal unless [?]Ubutnu releases a new version of the O/S.

---

### Post by Herman on 2009-08-27
Can you get a copy of your /boot/grub/menu.lst file for me and paste it here?
```
gksudo gedit /boot/grub/menu.lst
```
I'll take a look over it for you and see if I can spot any mistakes in it for you.

A copy of 'sudo fdisk -lu' might be useful too,
```
sudo fdisk -lu
```
Regards, Herman  :)

---

### Post by jkgoose937 on 2009-08-27
**** - Before Update - ****

splashimage (hd0,1)/boot/grub/splashimages/kgs.xpm.gz
default 6
timeout 15

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
# kopt=root=UUID=27c91f9c-d071-4092-9111-f1693f5b5034 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=27c91f9c-d071-4092-9111-f1693f5b5034

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

title Ubuntu 9.04, kernel 2.6.28-13-generic
kernel /boot/vmlinuz-2.6.28-13-generic root=UUID=27c91f9c-d071-4092-9111-f1693f5b5034 ro quiet splash
initrd /boot/initrd.img-2.6.28-13-generic

title Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
kernel /boot/vmlinuz-2.6.28-13-generic root=UUID=27c91f9c-d071-4092-9111-f1693f5b5034 ro  single
initrd /boot/initrd.img-2.6.28-13-generic

title Ubuntu 9.04, kernel 2.6.27-7-generic
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=27c91f9c-d071-4092-9111-f1693f5b5034 ro quiet splash
initrd /boot/initrd.img-2.6.27-7-generic

title Ubuntu 9.04, kernel 2.6.27-7-generic (recovery mode)
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=27c91f9c-d071-4092-9111-f1693f5b5034 ro  single
initrd /boot/initrd.img-2.6.27-7-generic

title Ubuntu 9.04, memtest86+
kernel /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

title Other operating systems:
root

title Windows XP Professional x64 Edition
root (hd0,0)
chainloader +1
savedefault
makeactive

**** - After Update - ****

splashimage (hd0,1)/boot/grub/splashimages/kgs.xpm.gz
### default 6
timeout 15

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
# kopt=root=UUID=27c91f9c-d071-4092-9111-f1693f5b5034 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=27c91f9c-d071-4092-9111-f1693f5b5034

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
##      altoptions=(single-user) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

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

title		Debian GNU/Linux, kernel 2.6.28-15-generic
root		27c91f9c-d071-4092-9111-f1693f5b5034
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=27c91f9c-d071-4092-9111-f1693f5b5034 ro quiet splash
initrd		/boot/initrd.img-2.6.28-15-generic

title		Debian GNU/Linux, kernel 2.6.28-15-generic (recovery mode)
root		27c91f9c-d071-4092-9111-f1693f5b5034
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=27c91f9c-d071-4092-9111-f1693f5b5034 ro single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Debian GNU/Linux, kernel 2.6.28-14-generic
root		27c91f9c-d071-4092-9111-f1693f5b5034
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=27c91f9c-d071-4092-9111-f1693f5b5034 ro quiet splash
initrd		/boot/initrd.img-2.6.28-14-generic

title		Debian GNU/Linux, kernel 2.6.28-14-generic (recovery mode)
root		27c91f9c-d071-4092-9111-f1693f5b5034
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=27c91f9c-d071-4092-9111-f1693f5b5034 ro single
initrd		/boot/initrd.img-2.6.28-14-generic

title		Debian GNU/Linux, kernel 2.6.28-13-generic
root		27c91f9c-d071-4092-9111-f1693f5b5034
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=27c91f9c-d071-4092-9111-f1693f5b5034 ro quiet splash
initrd		/boot/initrd.img-2.6.28-13-generic

title		Debian GNU/Linux, kernel 2.6.28-13-generic (recovery mode)
root		27c91f9c-d071-4092-9111-f1693f5b5034
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=27c91f9c-d071-4092-9111-f1693f5b5034 ro single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Debian GNU/Linux, kernel 2.6.27-7-generic
root		27c91f9c-d071-4092-9111-f1693f5b5034
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=27c91f9c-d071-4092-9111-f1693f5b5034 ro quiet splash
initrd		/boot/initrd.img-2.6.27-7-generic

title		Debian GNU/Linux, kernel 2.6.27-7-generic (recovery mode)
root		27c91f9c-d071-4092-9111-f1693f5b5034
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=27c91f9c-d071-4092-9111-f1693f5b5034 ro single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Debian GNU/Linux, kernel memtest86+
root		27c91f9c-d071-4092-9111-f1693f5b5034
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

title Other operating systems:
root

title Windows XP Professional x64 Edition
root (hd0,0)
chainloader +1
savedefault
makeactive


**** - FDISK - ****

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x20000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    61432559    30716248+   7  HPFS/NTFS
/dev/sda2        61432560   100502639    19535040   83  Linux
/dev/sda3       100502640   231368129    65432745   83  Linux
/dev/sda4       231368130   234436544     1534207+  82  Linux swap / Solaris

---

### Post by oldfred on 2009-08-27
You have a default set to 6, so I assume you want windows to boot as the default. But when Ubuntu updates the numbering changes and maybe it is trying to boot from the Other operating systems  - root that is blank.

I suggest moving your windows stanza above the automagic line (right after the timeout) and changing the default to 1.

You could also change the howmany to 2 and manually delete so only 2 show now, so you only see the 2 most current versions of ubuntu after every update and then the numbering should not change.

---

### Post by Herman on 2009-08-28
I suggest you open Synaptic Package Manager and do a search for grub.
Right-click on the line for grub in Synaptic Package Manager and click 'mark for complete removal', and then click 'Apply'.

I hope that will remove all of your grub files including the grub files you have in /usr/sbin, especially your /usr/sbin/update-grub script.

When grub has been completely removed from your operating system then mark it for installation again in Synaptic Package Manager and and then click 'Apply'.
The idea of doing this is to replace all of your grub files with the the same files from the most recent version of GRUB legacy.

After grub has been re-installed in your operating system using Synaptic Package Manager, you will still need to re-install grub files in /boot/grub and also the MBR.

This is to refresh your GRUB files in /boot/grub and re-install GRUB to MBR.
Run,
```
sudo grub-install /dev/sda
```This is to automatically generate a new menu.lst file for you.
```
sudo update-grub
```The Ubuntu boot entries in your new menu.lst should look like this from now on,
```
title        Ubuntu 9.04, kernel 2.6.28-11-generic
[COLOR=Blue]**uuid  **[/COLOR]      27c91f9c-d071-4092-9111-f1693f5b5034
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=27c91f9c-d071-4092-9111-f1693f5b5034 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

```Note that the word 'root' should be replaced with the word 'uuid' in the second line of each of your Ubuntu booting stanzas.

I'm only guessing, but it looks like you might have had an earlier version of Ubuntu and when you upgraded to Jaunty Jackalope and not all of your grub files were updated properly, I especially suspect your update-grub script. 
Your update-grub script, which is run automagically during kernel updates, doesn't seem to match the version of GRUB you're running.
I don't understand why your Ubuntu boot entry is being titled 'Debian GNU/Linux either, that makes me think maybe you had a Debian update-grub script. Strange. Have you had Debian installed in this or another PC at some time? I wonder how that got in there?

In any case, completely removing and then completely re-installing GRUB the way I have just explained should solve your problem I hope.

Regards, Herman :)

---

### Post by jkgoose937 on 2009-08-29
With the previous suggestions out there having to do with some type of mapping to "hx,y", I have installed a GRUB Editor installed acessed through System Setting -> Advanced each linux boot option I have the option to edit an option called "root" and selected (h0,1). This allowed me to boot into any of the boot options. This seems to be a fix for me. I'll back up my menu.lst file and next time this error comes I'll know what to do. Thanks for all the suggestions!

---

