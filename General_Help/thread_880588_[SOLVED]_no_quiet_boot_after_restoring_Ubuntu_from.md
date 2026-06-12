---
title: "[SOLVED] no quiet boot after restoring Ubuntu from backup"
date: 2008-08-05
forum: General Help
---

### Post by Irihapeti on 2008-08-05
I recently had to restore my Ubuntu 8.04 installation from backup. I'd backed it up according to instructions on the wiki, which include not to backup the /sys, /proc, /tmp, /media, /mnt and /lost+found directories. I also decided to exclude /var/cache/apt/archives, because I have copies of these files elsewhere.

Since the restore, I cannot get the system to boot quietly. /boot/grub/menu.lst has the "quiet" option in the kernel line - I've checked that several times - and yet I still get detailed text messages scrolling across the screen. 

I know that this isn't a show-stopper, but I'd like to know what might have happened to cause this, and what I can do to fix it.

Thanks
Irihapeti

---

### Post by logos34 on 2008-08-05
try this:

make sure the options line has just 'splash' and whatever else you need:
> 
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
**# defoptions=splash**
Then run **sudo update-grub**

anything?

---

### Post by Joeb454 on 2008-08-05
*feels intimidated by the 2 black cats*

(also the post above looks like it should work :p)

---

### Post by Irihapeti on 2008-08-05
> **Joeb454 said:**
> *feels intimidated by the 2 black cats*

(also the post above looks like it should work :p)

My cat is a nice cat - but the local rabbits don't think so :)

I'll try the fix shortly and report back.

Irihapeti

---

### Post by coffeecat on 2008-08-05
> **Irihapeti said:**
> I recently had to restore my Ubuntu 8.04 installation from backup.

Did you reformat the swap partition? If you did, checkout [this thread]("http://ubuntuforums.org/showthread.php?t=857565"). Scroll down to my first post. The launchpad link gives the background, but I've posted the fix anyway.

---

### Post by Irihapeti on 2008-08-05
I'm not sure what to make of the swap partition thing. Yes, I did reformat it, and I had to change its designation in /etc/fstab, because it was no longer /dev/sda5 but /dev/sda3 (I dislike UUIDs because they are so easy to overlook, but I got caught anyway.)

Anyway, I've tried the fix, and sorry to say Ubuntu now won't boot at all. (I'm posting this from Puppy Linux.) It gets as far as that pretty screen saying that it's loading essential drivers etc, and sits for ages until displaying a "busybox" message with (initramfs). Booting up with the recovery option, it gets to where it's trying to load all the usb drive and scsi options and just hangs.

I can't think why update-grub should have done that. It looks as though I might be up for another reinstall. Anyway, that won't be tonight. It's nearly midnight here so I'll leave it for now and if anyone has any ideas as to what's happened, I'll be interested.

Thanks
Irihapeti

---

### Post by logos34 on 2008-08-05
*first thing: boot the live cd and restore backup of menu.lst:
-click on / to mount (should do so at default location '/media/disk'
-sudo cp /media/disk/boot/grub/menu.lst /media/disk/boot/grub/menu.lst_20080805
-sudo cp /media/disk/boot/grub/menu.lst~ /media/disk/boot/grub/menu.lst
(after your edited menu.lst prior to running update-grub the system should have automatically made a backup 'menu.lst[COLOR=Red]~[/COLOR]')

post your menu.lst--it's possible the default entry has a typo on one of its lines, or update-grub has rearranged the kernels

Did your root partition # change by any chance? (swap did).  Check sudo fdisk -l as well (although you probably already did that).

OR:

Since this is a restoration, you could try 'refreshing' /boot, and reinstalling grub to mbr.

[http://users.bigpond.net.au/hermanzone/p15.htm#Grub_loading_stage1.5](http://users.bigpond.net.au/hermanzone/p15.htm#Grub_loading_stage1.5)
> 
sudo cp /boot/grub/menu.lst .
sudo rm /boot/grub/*
sudo cp menu.lst /boot/grub
sudo grub-install --root-directory=/media/disk /dev/sda*for the last line above replace '/media/disk...' with whatever the mount point is on the live cd, and add that to the paths

---

### Post by caljohnsmith on 2008-08-05
Irihapeti, I agree with Coffeecat that it sounds like you have a problem with your UUIDs and not your menu.lst. I had exactly the same type of problem, but I had to go through a few extra steps to completely fix my problem then what Coffeecat outlines. If his solution doesn't work for you, see [this post]("http://ubuntuforums.org/showthread.php?t=828578&highlight=splash+screen") if you need a step-by-step guide of how to fix it like I did.

---

### Post by logos34 on 2008-08-05
> **caljohnsmith said:**
> Irihapeti, I agree with Coffeecat that it sounds like you have a problem with your UUIDs and not your menu.lst.

But menu.lst ('kernel' line) uses UUIDs too ('root=UUID=xxxxx...')

---

### Post by caljohnsmith on 2008-08-05
> **logos34 said:**
> But menu.lst ('kernel' line) uses UUIDs too ('root=UUID=xxxxx...')
True, but he would not be able to boot at all if he had his UUIDs messed up in menu.lst. He would get a Grub error. :)

---

### Post by logos34 on 2008-08-05
> **caljohnsmith said:**
> True, but he would not be able to boot at all if he had his UUIDs messed up in menu.lst. He would get a Grub error. :)

well, I could be wrong but uuids don't seem to be a factor here--all the more so since the OP may have changed menu.lst to '/dev...' format as well.  

But maybe I should bow out because I seem to have compounded Irihipeti's initial minor problem by suggesting the normally innocuous update-grub command!  

If it was me I'd try to get back the previously working file (menu.lst~) and maybe then try Herman's 'refresh' trick.  Or else just dump it and run **sudo grub-install /dev/sda**, which will generate a new (and hopefully working) menu.lst along with copying the kernel images to /boot.

---

### Post by Irihapeti on 2008-08-05
OK, I'm back in business from Ubuntu. I replaced the backup copy of menu.lst and rebooted. It's back to the old behaviour: "Loading files needed to boot" (or something like that), but at least it's working.

Here's the updated menu.lst:

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

Pretty colours
color white/blue yellow/green ##white/blue yellow/red

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
# kopt=root=UUID=c35bb366-a242-4928-9937-761d0e5b523c ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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
# defoptions=splash

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=c35bb366-a242-4928-9937-761d0e5b523c ro splash
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=c35bb366-a242-4928-9937-761d0e5b523c ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title  .
root
title		Other operating systems:
root

title Puppy Linux 2.17
rootnoverify (hd0,1)
kernel /vmlinuz root=/dev/ram0
initrd /initrd.gz

title Puppy Linux 3.01
rootnoverify (hd0,1)
kernel /puppy301/vmlinuz root=/dev/ram0
initrd /puppy301/initrd.gz

title Puppy Linux 4.00
rootnoverify (hd0,1)
kernel /puppy400/vmlinuz root=/dev/ram0
initrd /puppy400/initrd.gz

```

There are no UUIDs in the previous menu.lst, i.e. the one I'm using now. I did have some trouble with swap not working because I'd changed the designation of the swap partition from /dev/sda5 to /dev/sda3, but fixing fstab corrected that.

Anyway, I'd better post this, because I can see that there are people hanging around here wondering how I've got on. No bad feelings, by the way.

(And as an aside, I'm not a "he" :) )

Irihapeti

---

### Post by logos34 on 2008-08-05
> **Irihapeti said:**
> No bad feelings, by the way.

Glad to hear...makes me feel better.  Because I always strive at the very least to 'do no harm'.

(pardon the gender ref, but it always seems to creep into my sentences, and I hate using 'he/she', etc)

Hopefully someone else can step in with the solution

best wishes

---

### Post by Irihapeti on 2008-08-05
It sounds as though there is a bit more to this issue than appears at first glance - bug reports and all that.

So, maybe I'll just go with what I've got and leave it for a while. That gives the developers and others time to sort out bugs and such like. No one is watching my computer boot up and making disparaging remarks about Ubuntu, after all. :)

And it all goes to show how important it is to have backups. A few live CDs or alternative booting options also come in handy. One of the first things I'd recommend a new user have is SuperGrubDisk. It's got me out of trouble on more than one occasion.

Thanks
Irihapeti

---

### Post by Irihapeti on 2008-08-06
I applied the fix described by caljohnsmith in [[COLOR="Blue"]this thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=828578"), took a deep breath, rebooted and ....

it worked!!

A nice, quiet boot.

That's another one I can add to my list of things I know what to do about next time.

Thanks, all

Irihapeti

P.S. Knowing that one has a recent backup does wonders for the confidence. :)

---

### Post by logos34 on 2008-08-06
> **Irihapeti said:**
> I applied the fix described by caljohnsmith in [[COLOR=Blue]this thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=828578"),

hmm...interesting fix...never encountered this bug before, even though I've had my fair share of failed swap mounts at boot due to mismatched uuids (which have changed for one reason or another)...Maybe because instead of the swap uuid I'm using 'resume=/dev/sda8' (hibernate) option on my menu.lst kernel line (which is also how it's listed in /etc/initramfs-tools/conf.d/resume), so I only have to update the fstab line and everthing works just like before.

---

### Post by Irihapeti on 2008-08-06
I never have liked the UUID idea, at least as it's currently implemented, and this incident rather confirms it. At least /dev/sda1 (or whatever) stays the same when you reformat. UUIDs change, and unless you know that, you can be tearing your hair. I didn't even know there was such a thing as the resume file.

However, as it's working now, I'll leave it.

Irihapeti

---

