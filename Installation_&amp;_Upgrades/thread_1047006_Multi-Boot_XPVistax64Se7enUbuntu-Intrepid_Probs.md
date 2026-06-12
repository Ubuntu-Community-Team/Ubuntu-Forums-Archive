---
title: "Multi-Boot XP/Vistax64/Se7en/Ubuntu-Intrepid Probs"
date: 2009-01-22
forum: Installation &amp; Upgrades
---

### Post by gcracker on 2009-01-22
I know this is widely discussed, and I am reading and trying to fix with many tools, but I am a n00b to Linux in general and have done enough damage.

I recently decided to multi-boot as the title says with four 230GB partitions on my 1TB drive. I went in order from oldest to newest: XP Pro, Vista Ult-x64, Seven x86, Ubuntu 8.10. I left the fourth and final partition unallocated for Linux to format as ext3 when the time came.

When I installed Ubuntu, I told GPartEd to let me specify manually the partition I had set aside. I chose this instead of the guided options, because they all took over either the XP partition (0,0) or the entire thing. I selected the last unallocated partition and told it to mount "/" to it and format. When asked, I left the checkbox for Windows Vista/Longhorn unchecked and told it to put the bootloader into (hd0) [or was it (hd0,0)? ].

At the very end, I was greeted by the "grub-install" error fatal error message and install halted. 
I rebooted and was greeted by the familiar windows boot loader, instead of Grub. 

I tried reinstalling twice with the same options to no avail, then installed with the checkbox for Windows Vista/Longhorn to see what happened. Now I could use Ubuntu, but not the other versions of MS-Windows. After playing with the SuperGrub boot fixer-upper thingy, I gave up on Ubuntu and did a repair from the windows seven dvd that restored the MBR and boot loader. 

I know that Ubuntu is still there, but the MS bootloader won't list it (or can't). At this point I am reluctant to try any other steps unless I can be reasonably sure they are the right way to go. 

Will the SuperGrubDisk set me right this time?

Installing four operating systems again (for the fourth time in two days) is not what I'm looking forward to.

I have heaps of experience with the DOS-Shell, but very very little with BASH. 

Thank you for your time and any help you can give.

-Graham

---

### Post by Yesideez on 2009-01-22
I've done something similar - multi-booting 4 OSs (XP Pro, XP Pro, Vista, Ubuntu) and without meaning to I went from oldest to newest.

Only difference is because of my HD setup (ample space - 2TB) I had to install Ubuntu into a folder and not a hard drive. Well, a friend did it for me.

We had problems getting Ubuntu to install to a partition on a drive as it wanted to install to the primary on the drive - couldn't do that as Vista was already there and everything was booting just fine.

I was going to add a fifth (Winblows 7) but as 7 is only in beta I thought no - when it expires it's gonna mess my boot-up.

Bit of a noob myself :( hope this may in some slight way be useful to you :)

btw, I found a nice tool called "EasyBCD" for editing the boot-up for Vista - good luck!

---

### Post by logos34 on 2009-01-22
'(hd0)' is the default grub location.

If you mean that you checked the 'Format?' box for Vista the second time around, then you erased it--correct me if I've misunderstood.  You'll either have to reinstall it or try to perform an NTFS partition recovery with TestDisk--see [this]("http://www.cgsecurity.org/wiki/TestDisk") and [this]("http://www.users.bigpond.net.au/hermanzone/p21.html").  Windows 7 was the last version to be installed and consequently its boot manager is the one handling the boot process (althought the actual boot files would have been put on the XP partition I believe)...But the windows bootloader won't list ubuntu for the simple reason it was installed last, after windows. (i.e. it doesn't update itself). 

From the ubuntu live cd run this in a terminal and post the ouput:

sudo fdisk -l

which will show your partition layout.  

But going on what you said about the installation order of windows, you might want to try reinstalling the Grub bootloader and then editing your ubuntu menu.lst to allow you to boot windows:

gksudo gedit /boot/grub/menu.lst

try these windows stanzas:

> title Windows XP/7/Vista
root (hd0,0)
makeactive
chainloader +1

or 
> 
root (hd0,2)

One of those should bring up the Windows 7 boot manager with a choice of XP too (and possibly Vista, even though I think you'll have to restore it before you can actually boot it)

good luck

ADD: like Yesideez suggested, EasyBCD is a great way too, but you'll still have to add linux to it, and restore Vista if in fact you deleted it

---

### Post by ronnielsen1 on 2009-01-22
I use grub to kick in either Linux or windows bootloader. Once I had windows working properly I reinstalled grub but had to remap the windows part of grub to make it appear that windows was on the first partition (it's on the slave hard drive)
Once you give a screenshot of gparted (from a live cd) or give us the output of sudo fdisk -l like logos 34 suggested I'm sure it can be figured out.
> timeout 15
color cyan/blue white/blue
foreground ffffff
background 0639a1

gfxmenu /boot/grub/message



title MEPIS at hda3, kernel 2.6.27-1-mepis-smp
root (hd0,2)
kernel /boot/vmlinuz-2.6.27-1-mepis-smp root=/dev/hda3 nomce quiet splash vga=791 resume=/dev/hda1 
boot



title Windows 7 & Win XP 
 map (hd0) (hd1)
 map (hd1) (hd0)
 rootnoverify (hd1,0)
 chainloader +1
 makeactive


title Ubuntu 8.10, kernel 2.6.27-7-generic
root (hd0,4)
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=bb187c58-bcf7-44b2-9ae2-5b2ed51e2158 ro quiet splash
initrd /boot/initrd.img-2.6.27-7-generic

title MEMTEST
kernel /boot/memtest86+.bin


---

### Post by rolnics on 2009-01-22
Sounds like you've got into a right pickle there! Have you tried a dedicated Grub partition? I've got one and it's great as all the other OS have their bootloader on the partition they are installed on and this dedicated Grub partition just points to the appropriate loader. This might be a good solution for you as it's a safer option, unless you format your whole drive!

Here's some links to take a look at: -
[Making a Dedicate Grub Partition]("http://www.troubleshooters.com/linux/grub/grubpartition.htm") 

[Creating a Dedicated Knoppix Partition]("http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm") this link is about another distro and gives reasons why it's a handy thing to have installed, I haven't done this yet, but I might use the idea soon.

[A thread from these forums.]("http://ubuntuforums.org/showthread.php?t=851492&") louieb the op of this thread seems pretty helpful on this subject, there are also some other links to Psychocats who's another great resource for all us beginners in linux. 

I hope this helps in some way.

---

### Post by gcracker on 2009-01-22
> **logos34 said:**
> '(hd0)' is the default grub location.

If you mean that you checked the 'Format?' box for Vista the second time around, then you erased it--correct me if I've misunderstood.  You'll either have to reinstall it or try to perform an NTFS partition recovery with TestDisk--see [this]("http://www.cgsecurity.org/wiki/TestDisk") and [this]("http://www.users.bigpond.net.au/hermanzone/p21.html").  Windows 7 was the last version to be installed and consequently its boot manager is the one handling the boot process (althought the actual boot files would have been put on the XP partition I believe)...But the windows bootloader won't list ubuntu for the simple reason it was installed last, after windows. (i.e. it doesn't update itself). 

From the ubuntu live cd run this in a terminal and post the ouput:

sudo fdisk -l

which will show your partition layout.  

But going on what you said about the installation order of windows, you might want to try reinstalling the Grub bootloader and then editing your ubuntu menu.lst to allow you to boot windows:

gksudo gedit /boot/grub/menu.lst

try these windows stanzas:



or 


One of those should bring up the Windows 7 boot manager with a choice of XP too (and possibly Vista, even though I think you'll have to restore it before you can actually boot it)

good luck

ADD: like Yesideez suggested, EasyBCD is a great way too, but you'll still have to add linux to it, and restore Vista if in fact you deleted it


No, I didn't install to the Vista partition, just loaded grub there... I selected a separate partition for Ubuntu. All versions of windows work correctly right now. (The reason it says Vista/Longhorn loader is because windows seven is detected/reports that way) The real problem is that the way Ubuntu initially sets up, Grub shows me the linux options and a windows option, but when selected, the windows option just flashed quickly and brought me back to the menu. I have since done a repair of the MBR to get access to windows. 

So my question is this: Can I very simply put grub back and tell it to call to the Windows 7 boot loader from a menu option? Is this a simple process, like just looking in my device assignment from "sudo fdisk -l" and entering the appropriate info to menu.lst?

I have SuperGrubDisk, but am reluctant to disable three OS's for one to work.

---

### Post by gcracker on 2009-01-22
ubuntu@ubuntu:~$ [COLOR="Blue"]sudo fdisk -l[/COLOR]

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdeb1deb1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30400   244187968+   7  HPFS/NTFS
/dev/sda2           30401      121601   732572032+   f  W95 Ext'd (LBA)
/dev/sda5           30401       60800   244187968+   7  HPFS/NTFS
/dev/sda6           60801       91200   244187968+   7  HPFS/NTFS
/dev/sda7           91201      121601   244196001   83  Linux


[COLOR="Red"]=================================================[/COLOR]

Wow, sorry for all the comments... but I don't know for sure that they are ignored...

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
# kopt=root=UUID=82381806-ad5c-4ee8-a035-93dba2dc82a1 ro xforcevesa

## default grub root device
## e.g. groot=(hd0,0)
# groot=82381806-ad5c-4ee8-a035-93dba2dc82a1

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

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		82381806-ad5c-4ee8-a035-93dba2dc82a1
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=82381806-ad5c-4ee8-a035-93dba2dc82a1 ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		82381806-ad5c-4ee8-a035-93dba2dc82a1
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=82381806-ad5c-4ee8-a035-93dba2dc82a1 ro xforcevesa  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		82381806-ad5c-4ee8-a035-93dba2dc82a1
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=82381806-ad5c-4ee8-a035-93dba2dc82a1 ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		82381806-ad5c-4ee8-a035-93dba2dc82a1
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=82381806-ad5c-4ee8-a035-93dba2dc82a1 ro xforcevesa  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		82381806-ad5c-4ee8-a035-93dba2dc82a1
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
[COLOR="DarkGreen"]makeactive[/COLOR] [COLOR="Gray"]This used to say something else, like savedefault?[/COLOR]
chainloader	+1

[COLOR="Red"]=================================================[/COLOR]

So there you are... As an aside, I used the SGD to try to boot to ubuntu 8.10 and it gave an error 15 file not found... probably looking for the grub loader on (hd0,0) and now it's MS-bootloader.

Thanks for the help, guys. I hope someday to be there for you as well.

---

### Post by gcracker on 2009-01-22
> **logos34 said:**
> ...But going on what you said about the installation order of windows, you might want to try reinstalling the Grub bootloader and then editing your ubuntu menu.lst to allow you to boot windows:

What steps do I take to install grub like you mention here? Can I just make a */boot* folder on the booting partition and include */grub* with *stage1/2* and *menu.lst*?

---

### Post by logos34 on 2009-01-22
> **gcracker said:**
> What steps do I take to install grub like you mention here? Can I just make a */boot* folder on the booting partition and include */grub* with *stage1/2* and *menu.lst*?

try this:

boot the ubuntu live cd and in a terminal type this:

[B]sudo grub

find /boot/grub/menu.lst[/B]
(it should output 'hd0,6'--your ext3 ubuntu partition, sda7)

[B]root (hd0,6)
setup (hd0)
quit[/B]

THis will overwrite windows bootloader on the MBR.  Your windows boot files must be on sda1, so the entry you have should work:

> ### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
[COLOR="Red"]root[/COLOR] <--[B]delete this
[/B]

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Windows Vista/Longhorn (loader)
root (hd**0,0**)
makeactive 
savedefault
chainloader +1

---

### Post by gcracker on 2009-01-23
> **logos34 said:**
> try this:

boot the ubuntu live cd and in a terminal type this:

[B]sudo grub

find /boot/grub/menu.lst[/B]
(it should output 'hd0,6'--your ext3 ubuntu partition, sda7)

[B]root (hd0,6)
setup (hd0)
quit[/B]

THis will overwrite windows bootloader on the MBR.  Your windows boot files must be on sda1, so the entry you have should work:

I let SuperGrubDisk do this for me, but I watched it do it's thing and that what it said, exactly. I think the original problem was that it messed up the windows boot loader/MBR, and when I fixed it, it was simply a matter of pointing grub to the proper place. 

Now, when I boot, I get grub loader and can choose windows, which loads the MS-boot-loader and lets me choose which ver of windows to load.

Thank you all for your help!

As a final thought, I'm attaching my new menu.lst and for your thoughts.
[COLOR="Red"]=======================================================================[/COLOR]

[COLOR="Blue"]## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		82381806-ad5c-4ee8-a035-93dba2dc82a1
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=82381806-ad5c-4ee8-a035-93dba2dc82a1 ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		82381806-ad5c-4ee8-a035-93dba2dc82a1
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=82381806-ad5c-4ee8-a035-93dba2dc82a1 ro xforcevesa  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		82381806-ad5c-4ee8-a035-93dba2dc82a1
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=82381806-ad5c-4ee8-a035-93dba2dc82a1 ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		82381806-ad5c-4ee8-a035-93dba2dc82a1
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=82381806-ad5c-4ee8-a035-93dba2dc82a1 ro xforcevesa  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		82381806-ad5c-4ee8-a035-93dba2dc82a1
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
makeactive
chainloader	+1[/COLOR]

---

### Post by gcracker on 2009-01-23
**Logos34**, what will deleting the 'root' at the beginning of the other OS section do for me?

---

### Post by logos34 on 2009-01-24
probably nothing--I wasn't sure if it was supposed to be there. (but I noticed my 8.04 menu.lst has it too, so I guess it's the default).  Sometimes the strangest little things in grub can cause problems.

---

### Post by gcracker on 2009-02-02
Now how can I set this thread to "solved" ?

I have since moved on to different problems... thank you all!!!

---

