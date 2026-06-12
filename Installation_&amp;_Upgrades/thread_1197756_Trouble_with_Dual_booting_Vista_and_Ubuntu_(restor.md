---
title: "Trouble with Dual booting Vista and Ubuntu (restoring the grub menu)"
date: 2009-06-26
forum: Installation &amp; Upgrades
---

### Post by ferno on 2009-06-26
Hello, I know this is a very common issue, but after trying to figure it out by googling I am still very confused

Well first I installed ubuntu, then vista, and I was following the steps in this tutorial:

[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)

Anyway, I successfully installed both operating systems, but when I restart my computer I can only get the grub CLI instead of the grub menu

i figured out how to boot into vista by using:

grub> rootnoverify (hd0,0)
grub> makeactive
grub> chainloader +1
grub> boot

and i can boot into ubuntu using:

grub> root (hd0,1)
grub> kernel /boot/vmlinuz-2.6.28-13-generic root=/dev/sda2
grub> boot

but how do I get the grub menu to load instead of the grub command line? once I can get that to work I think I know how to edit menu.lst to add vista to the list of options, but I'm not sure how to get the grub menu up

thanks

---

### Post by Bucky Ball on 2009-06-26
Wrong. Other way around! Vista, then Ubuntu. You are going to get all sorts of issues with your grub doing it this way. :(

These can be sorted out, sometimes quickly, sometimes longly, but to get into it, you are much better right now just starting again and going Vista first. Although, you are getting pretty close it seems. It is about Windows flavours wanting to be Primary Partition 1, Disk 1 or you need to trick 'em.

Don't really know what is happening when you are logging into to a CLI. Odd.

You could try downloading SuperGrubDisk and seeing if that can fix things for you. You're definitely getting there, though.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by Nburnes on 2009-06-26
You should have done Vista first then Ubuntu.

---

### Post by ferno on 2009-06-26
Well I installed ubuntu without the intent of installing windows again for a while, but I had to update my bios, and it proved to be almost impossible in ubutnu.

I figured if I can get the grub command line and be able to manually boot into ubuntu or windows it shouldn't be that hard to setup a grub menu ;(

---

### Post by merlinus on 2009-06-26
Woulda, shoulda, coulda.  Maybe, but there well may be a solution.

Open a terminal whilst booted into ubuntu, and post results of:

```

cat /boot/grub/menu.lst

```

and with a bit of editing, we may get it to work.

---

### Post by Bucky Ball on 2009-06-26
Try this, the best I've seen and a huge resource for all things dual boot MS/Ubuntu:

[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

Good luck.

---

### Post by Bucky Ball on 2009-06-26
> **merlinus said:**
> Woulda, shoulda, coulda.  Maybe, but there well may be a solution.


Oh, there will be.

---

### Post by ferno on 2009-06-26
heres what my menu.lst looks like:

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
timeout		3

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
# kopt=root=UUID=f52afc21-ff61-4e75-ac76-3a9b35cc8cca ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=f52afc21-ff61-4e75-ac76-3a9b35cc8cca

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

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		f52afc21-ff61-4e75-ac76-3a9b35cc8cca
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=f52afc21-ff61-4e75-ac76-3a9b35cc8cca ro quiet splash 
i8042.reset i8042.nomux i8042.nopnp i8042.noloop
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		f52afc21-ff61-4e75-ac76-3a9b35cc8cca
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=f52afc21-ff61-4e75-ac76-3a9b35cc8cca ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		f52afc21-ff61-4e75-ac76-3a9b35cc8cca
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=f52afc21-ff61-4e75-ac76-3a9b35cc8cca ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		f52afc21-ff61-4e75-ac76-3a9b35cc8cca
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=f52afc21-ff61-4e75-ac76-3a9b35cc8cca ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		f52afc21-ff61-4e75-ac76-3a9b35cc8cca
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by ajgreeny on 2009-06-26
It should be no major problem once the menu.lst file has been written/rewritten correctly and grub then installed to the first boot device.

As merlinus said, lets see your menu.lst file, and also the output of ```
sudo fdisk -l
``` from your ubuntu install.  It should then be possible to make sure that the menu.lst points to the correct OS on the correct partition.

---

### Post by ferno on 2009-06-26
from fdisk -l:

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6423    51591168    7  HPFS/NTFS
/dev/sda2            6424       37784   251907232+  83  Linux
/dev/sda3           37785       38913     9068692+   5  Extended
/dev/sda5           37785       38913     9068661   82  Linux swap / Solaris

---

### Post by merlinus on 2009-06-26
Add this to the very end of menu.lst:

title Windows
rootnoverify (hd0,0)
makeactive
chainloader +1

Then restart and see what happens.

---

### Post by merlinus on 2009-06-26
If that did not fix the problem, try this next:

```

sudo grub 
root (hd0,1)
setup (hd0)
quit

```

---

### Post by ferno on 2009-06-26
ahh, it works now!!!!

but it may have also been because im kind of an idiot, i dont think there was a menu.lst file, only a menu.lst~, i saved it as menu.lst instead and it seems everything working now

thank you everyone :D

---

### Post by merlinus on 2009-06-26
Great news!  No mistakes, only learning situations.  The only idiots are in Washington, DC.

---

### Post by leviofan on 2009-06-26
Well I installed ubuntu without the intent of installing windows again for a while, but I had to update my bios, and it proved to be almost impossible in ubutnu.

---

### Post by Macedo on 2009-06-26
How can I remove previous versions of Ubuntu?

I want to have only last version of Ubuntu and XP.

[IMG]http://pic.mk/images/dsc00508.jpg[/IMG]

---

### Post by presence1960 on 2009-06-26
To all: please don't take this personally, but where did the myth start that you need to install windows before Ubuntu. Not only does our community documentation guide us on how to install windows after linux but a google on the subject will turn up numerous hits.

There is really no difficulty in installing windows after Linux. Create a primary partition for windows (it doesn't have to be the first partition either!). Insert the windows installation CD and install to the intended windows partition. Boot off the Ubuntu Live CD and restore GRUB to MBR. Quit Live CD and boot your machine. if there is no windows entry in the GRUB menu edit your menu.lst to include a windows entry.

Actually the process is pretty straightforward. You only need the added step of restoring GRUB after the windows install because the windows bootloader will be written to MBR and overwrite GRUB. That is a simple task to restore GRUB, as a matter of fact it is so easy a caveman can do it.

here is a link on the topic: [http://ubuntuforums.org/showthread.php?t=1191763](http://ubuntuforums.org/showthread.php?t=1191763)

Good thing the OP didn't listen to the myth that you must install windows first or he/she would have lost a perfectly good OS (Ubuntu) for nothing.

**you do not have to remove Ubuntu to install windows!**

---

### Post by presence1960 on 2009-06-26
> **merlinus said:**
> Great news!  No mistakes, only learning situations.  The only idiots are in Washington, DC.

I like that merlin!

---

### Post by presence1960 on 2009-06-26
Macedo edit your menu.lst by opening a terminal and running > gksu gedit /boot/grub/menu.lst. When menu.lst opens scroll down to your kernels list and comment out the kernels you do not want to use. See mine as an example :```


## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		c94e2af2-c9a2-49b5-ba8f-357853bf3e23
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=c94e2af2-c9a2-49b5-ba8f-357853bf3e23 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		c94e2af2-c9a2-49b5-ba8f-357853bf3e23
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=c94e2af2-c9a2-49b5-ba8f-357853bf3e23 ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-12-generic
uuid		c94e2af2-c9a2-49b5-ba8f-357853bf3e23
kernel		/boot/vmlinuz-2.6.28-12-generic root=UUID=c94e2af2-c9a2-49b5-ba8f-357853bf3e23 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-12-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-12-generic (recovery mode)
uuid		c94e2af2-c9a2-49b5-ba8f-357853bf3e23
kernel		/boot/vmlinuz-2.6.28-12-generic root=UUID=c94e2af2-c9a2-49b5-ba8f-357853bf3e23 ro  single
initrd		/boot/initrd.img-2.6.28-12-generic

#title		Ubuntu 9.04, kernel 2.6.28-11-generic
#uuid		c94e2af2-c9a2-49b5-ba8f-357853bf3e23
#kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=c94e2af2-c9a2-49b5-ba8f-357853bf3e23 ro quiet splash 
#initrd		/boot/initrd.img-2.6.28-11-generic
#quiet

#title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
#uuid		c94e2af2-c9a2-49b5-ba8f-357853bf3e23
#kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=c94e2af2-c9a2-49b5-ba8f-357853bf3e23 ro  single
#initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		c94e2af2-c9a2-49b5-ba8f-357853bf3e23
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

I commented out kernel 2.6.28-11, it does not show in my GRUB menu on boot. Just use the # before each line of the entries you do not want to see.

---

### Post by Bucky Ball on 2009-06-27
> **presence1960 said:**
> To all: please don't take this personally, but where did the myth start that you need to install windows before Ubuntu. Not only does our community documentation guide us on how to install windows after linux but a google on the subject will turn up numerous hits.

There is really no difficulty in installing windows after Linux. Create a primary partition for windows (it doesn't have to be the first partition either!). Insert the windows installation CD and install to the intended windows partition. Boot off the Ubuntu Live CD and restore GRUB to MBR. Quit Live CD and boot your machine. if there is no windows entry in the GRUB menu edit your menu.lst to include a windows entry.

Actually the process is pretty straightforward. You only need the added step of restoring GRUB after the windows install because the windows bootloader will be written to MBR and overwrite GRUB. That is a simple task to restore GRUB, as a matter of fact it is so easy a caveman can do it.

here is a link on the topic: [http://ubuntuforums.org/showthread.php?t=1191763](http://ubuntuforums.org/showthread.php?t=1191763)

Good thing the OP didn't listen to the myth that you must install windows first or he/she would have lost a perfectly good OS (Ubuntu) for nothing.

**you do not have to remove Ubuntu to install windows!**

No myth and you don't. It is just an easier, sure fire way for someone new to Ubuntu to get things up and rolling quickly. This OP is an exception and caught on quick. Yes, there is minimal effort required to get it working, but if you've never seen a terminal before and are a bit wary, unlike this OP who dived right in (and good for them), this thread could just have easily have gone for 4 or 5 pages and three or four dozen posts. 

No myth, no oogie boogie stuff; just the path of least resistance for most newbies. Some people don't want it anymore involved than it has to be. :)

---

### Post by presence1960 on 2009-06-27
> **Bucky Ball said:**
> No myth and you don't. It is just an easier, sure fire way for someone new to Ubuntu to get things up and rolling quickly. This OP is an exception and caught on quick. Yes, there is minimal effort required to get it working, but if you've never seen a terminal before and are a bit wary, unlike this OP who dived right in (and good for them), this thread could just have easily have gone for 4 or 5 pages and three or four dozen posts. 

No myth, no oogie boogie stuff; just the path of least resistance for most newbies. Some people don't want it anymore involved than it has to be. :)

I agree that installing windows first is a **_little (not much) easier_**. But the reason I posted this is in quite a few threads OPs have been told they should have installed windows first and need to do it that way. Now wiping an already good install of ubuntu and then reinstalling 2 OS's is hardly the path of least resistance. That is really my objection. WE need to help and educate our newbie friends like it was done for us. The best way to learn is to roll your sleeves up and get in there. After all they have a whole community to help them.

P.S. Telling someone who already has Ubuntu installed that they should have installed windows first or need to install windows first is not helpful or logical. The fact remains that it is relatively easy to install windows after Ubuntu.

---

### Post by merlinus on 2009-06-27
+100!!!

To take the easy way often means missing out on tremendous learning opportunities.  Just because so-and-so says so is no reason not to try something different.

Taking risks often leads to knowledge.  But of course the risks need to be within a margin of safety.

And always remember to back up your data!

My $.05 worth...

---

### Post by presence1960 on 2009-06-27
> **merlinus said:**
> +100!!!

To take the easy way often means missing out on tremendous learning opportunities.  Just because so-and-so says so is no reason not to try something different.

Taking risks often leads to knowledge.  But of course the risks need to be within a margin of safety.

And always remember to back up your data!

My $.05 worth...

**amen!**

---

### Post by Macedo on 2009-06-27
> **presence1960 said:**
> Macedo edit your menu.lst by opening a terminal and running . When menu.lst opens scroll down to your kernels list and comment out the kernels you do not want to use. See mine as an example :```


## ## End Default Options ##

title        Ubuntu 9.04, kernel 2.6.28-13-generic
uuid        c94e2af2-c9a2-49b5-ba8f-357853bf3e23
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=c94e2af2-c9a2-49b5-ba8f-357853bf3e23 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid        c94e2af2-c9a2-49b5-ba8f-357853bf3e23
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=c94e2af2-c9a2-49b5-ba8f-357853bf3e23 ro  single
initrd        /boot/initrd.img-2.6.28-13-generic

title        Ubuntu 9.04, kernel 2.6.28-12-generic
uuid        c94e2af2-c9a2-49b5-ba8f-357853bf3e23
kernel        /boot/vmlinuz-2.6.28-12-generic root=UUID=c94e2af2-c9a2-49b5-ba8f-357853bf3e23 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-12-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-12-generic (recovery mode)
uuid        c94e2af2-c9a2-49b5-ba8f-357853bf3e23
kernel        /boot/vmlinuz-2.6.28-12-generic root=UUID=c94e2af2-c9a2-49b5-ba8f-357853bf3e23 ro  single
initrd        /boot/initrd.img-2.6.28-12-generic

#title        Ubuntu 9.04, kernel 2.6.28-11-generic
#uuid        c94e2af2-c9a2-49b5-ba8f-357853bf3e23
#kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=c94e2af2-c9a2-49b5-ba8f-357853bf3e23 ro quiet splash 
#initrd        /boot/initrd.img-2.6.28-11-generic
#quiet

#title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
#uuid        c94e2af2-c9a2-49b5-ba8f-357853bf3e23
#kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=c94e2af2-c9a2-49b5-ba8f-357853bf3e23 ro  single
#initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        c94e2af2-c9a2-49b5-ba8f-357853bf3e23
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```I commented out kernel 2.6.28-11, it does not show in my GRUB menu on boot. Just use the # before each line of the entries you do not want to see.

10x a lot. I'll try that.

---

### Post by ajgreeny on 2009-06-27
To get rid of the unwanted kernels you can also uninstall them using synaptic or apt-get.  If you are short of disk space this can free up a lot of space, but usually these days it is not so important.

Search for the kernel number 2.6.27-7 (or whatever) and then uninstall the kernel packages that way.  I always leave two versions just in case something should go wrong with the newest one, so I always have a fallback to work with.  There is certainly no reason to have 4 versions as you have at the moment.

---

