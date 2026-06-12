---
title: "hibernation"
date: 2006-10-22
forum: Hardware &amp; Laptops
---

### Post by manfredell on 2006-10-22
After updating from 6.06 to 6.20 I can no longer hibernate on my laptop.

When choosing hibernate from the shutdown screen (or whatever it is called) it switches off the display and an error message alnog the lines "unable to find swapfile device" (or so) is displayed and it does not hibernate.

Any help?

Thx

---

### Post by gborzi on 2006-10-22
Have you tried to add resume=/dev/<your swap partition> in the kernel line of grub, e.g. to change
> kernel          /boot/vmlinuz-2.6.15-27-k7 root=/dev/hda1 ro quiet splash
to
> kernel          /boot/vmlinuz-2.6.15-27-k7 root=/dev/hda1 ro quiet splash resume=/dev/hda5
in /boot/grub/menu.lst (where hda5 is the swap partition).

---

### Post by manfredell on 2006-10-22
I'm no linux guru and honestly can only configure via the gui, so no I didn't touch anything you mention.
So I appreciate your help.
Where can I check the partitions, which are installed?

These are contents of my menu.lst:

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
# kopt=root=UUID=78c097cf-8684-4cd6-ba6f-aea44deb2826 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-10-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-386 root=UUID=78c097cf-8684-4cd6-ba6f-aea44deb2826 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-386
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-386 root=UUID=78c097cf-8684-4cd6-ba6f-aea44deb2826 ro single
initrd		/boot/initrd.img-2.6.17-10-386
boot

title		Ubuntu, kernel 2.6.15-27-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=UUID=78c097cf-8684-4cd6-ba6f-aea44deb2826 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=UUID=78c097cf-8684-4cd6-ba6f-aea44deb2826 ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=UUID=78c097cf-8684-4cd6-ba6f-aea44deb2826 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=UUID=78c097cf-8684-4cd6-ba6f-aea44deb2826 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by manfredell on 2006-10-22
It somehow looks as if I don't have a swap partition any longer. Can this be?

---

### Post by KingArthur10 on 2006-10-22
When I first switched to dapper, this happened to me.  Install gparted from synaptic, go to the command line and type "sudo gparted" when it's done installing.  It should show a list of partitions and it will have a black partition with a "?" for partition type.  This probably was your swap (sounds like you could tell the difference), so just reformat that partition as swap and you're good to go.

**I take no responsibility for you accidentally formating the wrong partition ;-)**

---

### Post by manfredell on 2006-10-22
> **KingArthur10 said:**
> When I first switched to dapper, this happened to me.  Install gparted from synaptic, go to the command line and type "sudo gparted" when it's done installing.  It should show a list of partitions and it will have a black partition with a "?" for partition type.  This probably was your swap (sounds like you could tell the difference), so just reformat that partition as swap and you're good to go.

**I take no responsibility for you accidentally formating the wrong partition ;-)**

Did install gparted. This is what I see:

/dev/hda1  ext3
/dev/hda2  extended
/dev/hda5  unknown


So I should format hda5 as linux-swap?? Nothing else to configure, I mean does ubuntu recognize it as swap again without me telling so?


THANKS IN ADVANCE

---

### Post by manfredell on 2006-10-22
OK. I formatted the unknown hda5 as linux-swap. Rebooted. Still same error when trying to hybernate (... try swapon -a.."
Loadad gparted again. Right clicked on hda5 and chose swapon.
Reboot. Still nogo with hybernation.

How can I check that ubuntu is using hda5 as swap partition?

I'm lost...

---

### Post by manfredell on 2006-10-22
Solved it:

Looking at [http://www.ubuntuforums.org/showthread.php?t=270052&highlight=swap+partition](http://www.ubuntuforums.org/showthread.php?t=270052&highlight=swap+partition)
I figured that the Edgy update got the uuid for the swap drive wrong. I copied thw correct uuid from the device manager and pasted it into /etc/fstab.

All is working now!!

I figure this shoukd NOT happen when we update to a new version. This is no good.

---

### Post by benhall on 2006-10-22
Ive got the same problem. Part of it is that now the disks are refered to by a string of characters in /etc/fstab, which change after reformating. These can be found from the symbolic links in /dev/disk/by-uuid/. To get your swap to work again you will need to find out what that has changed to (ls -lrt /dev/disk/by-uuid, and look to see which points to /dev/sda5), and edit your /etc/fstab to match (the line you need to change will have the following line preceding it:
> # /dev/sda5 -- converted during upgrade to edgy
The only issue is that though this will only give you a new working swap, the hibernation problem might remain- that is the swap file becomes corrupt on hibernation. This is what I have found, so I'm sticking to suspend until the situation improves.

Has any one else had hibernate repeatedly corrupt their swap?

---

### Post by viper on 2006-10-22
Go to Menu--System-Admin--Disks, type in your password then under your partitions tab you should see where or if you have a swap file.

---

### Post by viper on 2006-10-22
Bit slow with my reply :) went and made a coffee, came back posted and found all is well and sorted...

---

### Post by manfredell on 2006-10-23
> **viper said:**
> Go to Menu--System-Admin--Disks, type in your password then under your partitions tab you should see where or if you have a swap file.

I can't find this menu!
Do you mean System-Administration? There is no Disks there??

---

### Post by pgilmon on 2006-10-27
I had the same problem. Tried the solution in [http://ubuntuforums.org/showpost.php?p=1656039&postcount=13](http://ubuntuforums.org/showpost.php?p=1656039&postcount=13) and ended up with a corrupted filesystem.

I think it was because that solution provides you with a boot option in the grub menu that always loads the image in the swap. I booted with that option after having worked with ubuntu but not hibernating, so probably got an image of some previous hibernation mixed with some information from the previous session (which I ended by switching off, not hibernating). The case is that after booting that way the system was unstable and when I rebooted with another kernel the filesystem was corrupted, so I installed a clean Edgy and now everything works allright.

Perhaps the explanation I provide does not make much sense, but I can't think of any other thing. I just wanted to warn the rest of the people about what happened to me.

---

### Post by zgornel on 2006-10-29
It seems to be a common problem. [http://www.ubuntuforums.org/showthread.php?t=286135](http://www.ubuntuforums.org/showthread.php?t=286135)

---

