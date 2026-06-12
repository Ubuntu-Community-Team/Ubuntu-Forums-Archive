---
title: "[SOLVED] Partition and dual boot help needed"
date: 2008-08-12
forum: General Help
---

### Post by RPG Master on 2008-08-12
So I am ready to make Ubuntu my main OS. But right now Windows is in charge of the dual boot...

So I have two questions:

1. How do I make Ubuntu be the one in charge of the dual boot?
2. How do I make the the partitions bigger? Right now its Ubuntu: 15 gigs, Vista: everything else.

Thanks in advance.

---

### Post by RPG Master on 2008-08-12
I am not sure if it helps but I am using Ubuntu 8.04 64-bit

---

### Post by Crafty Kisses on 2008-08-12
This link maybe helpful to you > [http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)**[B]**[/B]

---

### Post by RPG Master on 2008-08-12
I looked at that guide before I found Wubi and used it to install...
I reread it and it doesn't really help my sitiuation.
But thanks anyway.

---

### Post by houbysoft.xf.cz on 2008-08-12
For making Ubuntu the first on the grub list : post here your grub.conf (/boot/grub/grub.conf).

---

### Post by houbysoft.xf.cz on 2008-08-12
Oh, and for changing the partitions, I suggest you to boot from the liveCD (if you start Ubuntu from your HD you can't partition because you can't unmount the main partition) and use ALT+F2 gksu gparted.

---

### Post by nazish on 2008-08-12
If you want ubuntu to be the default OS to boot when you start the system then you need to post the contents of your menu.lst file here. 
 
It is located at /boot/grub/menu.lst
 
or else type the following commands in your terminal
 
**sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bkup **
 
**sudo gedit /boot/grub/menu.lst**
 
here find a line starting with > default A number should succeed it. usually 0 or 1 or 2 or 3 depending on the number of operating systems you have installed.
 
Now if you further inspect the file you can see that there are many entries that start with > title You may have now noticed that the content of this line appears on your grub menu. Modifying the text that appears after title alters the text in your grub menu. Count the total number of **title **lines, start the count from zero. Note down the **title number** of the OS you want to boot by default. 
 
change the number in the default entry which you saw in the beginning to the title number you just noted.
 
or else
 
install a utility called as startup manager present in the ubuntu repositories and run it.
 
As for your second question you need to resize your partition size. to do this boot thru a live cd ubuntu or knoppix. Start the program gParted and resize the partition.

---

### Post by RPG Master on 2008-08-12
Here is my menu.lst:

> # menu.lst - See: grub(8), info grub, update-grub(8)
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
# kopt=root=UUID=12F7A0772623C18F loop=/ubuntu/disks/root.disk ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=()/ubuntu/disks

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=12F7A0772623C18F loop=/ubuntu/disks/root.disk ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=12F7A0772623C18F loop=/ubuntu/disks/root.disk ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		()/ubuntu/disks
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
chainloader	+1


And keep in mind your working with a 14 year old :)

---

### Post by alzie on 2008-08-12
I'm confused.  Your Grub shows Ubuntu as the default OS.

Are you seeing the Vista Bootloader before you get to Grub?  And if so is this what you want changed?

---

### Post by RPG Master on 2008-08-12
Yes. First it shows the Vista loader asking me witch one I want to boot. Once I choose Ubuntu then it takes me to the Grub loader

I am not sure if this helps but....
Ubuntu is in a folder on Windows and on Ubuntu it says that I am using drive Z instead if C

---

### Post by bodhi.zazen on 2008-08-12
RPG Master installed Ubuntu via Wubi.

RPG Master : You can 
[list=number]
[*]Remove ubuntu form windows and re-install Ubuntu the "standard" way. This is my #1 option.
[*]Convert your wubi installation. [http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)
[*]Configure your windows boot loader to boot Ubuntu directly. I have no Idea how to do this with wubi.
[/list]

---

### Post by RPG Master on 2008-08-12
I am going to to try option 2, Wubi Partition Manager

While I am trying that if anyone has any other suggestions please do tell

And thanks to every one for all the help so far

---

### Post by DeathOnJuice on 2008-08-12
Wait, you just want to switch your bootloader to GRUB? This can be done with the GRUB console.

sudo grub
grub> find /boot/grub/stage1
 (hd0,0)
grub> root(hd0,0) SUBSTITUTE THE OUTPUT OF THE LAST COMMAND HERE
grub> setup(hd0) AGAIN, MAKE SURE TO DO THE RIGHT NUMBER

That should make GRUB the default bootloader.

---

### Post by alzie on 2008-08-12
I just went through the Wubi formus.  When you use Wubi the Vista bootloader stays in place.

The Wubi forums are here: [http://ubuntuforums.org/forumdisplay.php?f=234](http://ubuntuforums.org/forumdisplay.php?f=234)
An excellent place to find help with Wubi specific problems

Anyways... What I would do in this case is install StartUp-Manager from synaptic and set the timeout down to 1 second.  That way when you select Ubuntu it will be almost instant to start booting up.

The other option would be to go to a true Dual Boot and install Ubuntu to a true partition.  The link for the install from codename's post will tell you how to do this and provides instructions on how to ensure grub stays as the bootloader.

I wish I could be more help

---

### Post by bodhi.zazen on 2008-08-12
> **DeathOnJuice said:**
> Wait, you just want to switch your bootloader to GRUB? This can be done with the GRUB console.

sudo grub
grub> find /boot/grub/stage1
 (hd0,0)
grub> root(hd0,0) SUBSTITUTE THE OUTPUT OF THE LAST COMMAND HERE
grub> setup(hd0) AGAIN, MAKE SURE TO DO THE RIGHT NUMBER

That should make GRUB the default bootloader.

I do not think you can do that with wubi

---

### Post by RPG Master on 2008-08-12
I have made a 20 gig (I'll make it bigger once I set up Ubuntu and get some of my files off of Vista) partition and now I need to know what to do next. Do I just do that lvpm thing?

---

### Post by bodhi.zazen on 2008-08-12
Yep, make sure you read and understand the steps first. Ask if you get stuck.

---

### Post by RPG Master on 2008-08-12
I think I just REALLY screwed up...

My Grub loader is getting Error 17

Is their anything I can do?

(posting from our family computer)

---

### Post by RPG Master on 2008-08-12
The partition it made was a ext 3 and using LVPM I changed it to a NTFS.

Thats what made the Error 17 isn't it?

---

### Post by Bart_D on 2008-08-12
Do you already have Vista installed?  If yes, then I was in the same situation as you....the only exception is that I was using Windows XP.  Here's what I did:

When I installed WinXP, I created a partition that was half the size of the hard drive.  The remaining space was just left as unpartitioned.  So, after installing XP, I had one partition with XP and unpartitioned space.

When I installed Ubuntu, I opted to install it to the "Largest Available Space".  I then just followed the remaining installation instructions and now, Ubuntu controls the boot loader.i.e. it is the default option.

How many partitions do you have and do you have any unpartitioned space?

As far as GRUB is concerned, I have no clue what you need to do now to fix it!

*******BACKUP ALL YOUR IMPORTANT FILES NOW*******

---

### Post by RPG Master on 2008-08-12
Yes I have vista and their is no remaining space, both of my partitions have it all

---

### Post by Bart_D on 2008-08-12
Hmmm, yeah better wait for someone with more experience.

---

### Post by RPG Master on 2008-08-12
Does anyone no how to fix my Grub Loader?

Please help... :'(

---

### Post by bodhi.zazen on 2008-08-13
What have you done, what how-to are you following, and what step are you on ?

---

### Post by RPG Master on 2008-08-13
I was using the guide you [linked]("http://lubi.sourceforge.net/lvpm.html") me to. I was done with the installation and it told me to reboot so I did. Grub loaded with the choice of Ubuntu or Vista but if I selected Ubuntu it would come back with an error saying something along the lines of "hard drive is not mounted". Instead of looking/asking around for what to do next I just started up the Partition Manager and to see what I could do about it. I saw that my Vista partition was in NTFS while the Ubuntu one was in ext 3. Thinking that might have something to do with it I change the Ubuntu drive to NTFS. I saved it, logged out of the Partition Manager and rebooted my computer and then I got the Error 17.

And yes, I know this is my fault :(

---

### Post by bodhi.zazen on 2008-08-13
OK, no big deal I think ....

Ubuntu should be in an ext3 partition, so change that back.

Then boot a live CD and perform a fsck on your root partition.

From a live CD, open a terminal and run :

```
sudo sudo e2fsck -C0 -p -f -v /dev/sdxy
```

        if that fails

```
sudo fsck -fvy /dev/sdxy
```

Where "sdxy" = your ubuntu partition (sda4 or whatever).

Then reboot Ubuntu (from hard drive).

If that fails we can try re-installing grub from the live CD:

[uwiki]RecoveringUbuntuAfterInstallingWindows[/uwiki]

---

### Post by RPG Master on 2008-08-13
How do I change it back to a ext 3 if I can't get into Windows or Ubuntu?

---

### Post by RPG Master on 2008-08-13
And I've tried booting off of a live CD that I made before I found Wubi. It didn't work even after I tried messing with the BIOS.

Does this have anything to do with the way Vista burns CDs? Should I ask a friend to burn a new CD? (seeing as how my laptop was the only computer in my house with a CD burner)

---

### Post by bodhi.zazen on 2008-08-13
> **RPG Master said:**
> How do I change it back to a ext 3 if I can't get into Windows or Ubuntu?

How did you change it in the first place ? From Windows ?

You will need to boot a live CD to fix your hard drive. So next step, figure out why you can not boot the disk you have or download / burn a new one.

---

### Post by RPG Master on 2008-08-13
I used the Partition Manager that guide linked me to. I downloaded it while vista so in order to get to it (before the Grub Error) I had to choose Vista in Grub and then choose Partition Manager from the Windows boot.(what ever its called) So now I can't get to it.

And I am going to be getting a new live CD from a friend tomorrow.

---

### Post by bodhi.zazen on 2008-08-13
If you have your Vista CD or a recovery CD/DVD you can try to restore your MBR and boot Vista

Nice walk through :

[http://opesh.blogspot.com/2007/06/restore-vistas-master-boot-loader.html](http://opesh.blogspot.com/2007/06/restore-vistas-master-boot-loader.html)

---

### Post by RPG Master on 2008-08-15
I was unable to get the Live CD today (I still can if needed) but I got a 2 gig thumb drive. Fellowing this [guide]("http://www.pendrivelinux.com/2008/04/09/usb-ubuntu-804-installation-from-windows/") I made a Live USB. But when I boot up the laptop the thumb drive blinks 3 times and nothing else and then I can't do anything else with it. I can only shut it down after that.

Is their anyway I can edit my partitions with a program running off of my thumb drive?

And my laptop didn't come with a Vista back up.

---

### Post by RPG Master on 2008-08-15
Bump

---

### Post by alzie on 2008-08-16
I've been looking around for Grub error 17,  Look at this link to see if there is some help.  [http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=866058](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=866058)

I think your best option is to get the live disk from your friend.  If they haven't already burned one have them burn the iso at a low speed (4x is usually recommended)

Can you post the specs for your computer as well?  It might help here.

---

### Post by RPG Master on 2008-08-16
I have given up and ordered a Windows restore disk from HP...

> burn the iso at a low speed (4x is usually recommended)

Thats might be why I could never get my Live CD to work...
I'll do that when I make my Live CD when I reinstall Ubuntu.

Thanks everyone for trying your best to help me. ;-)

I am marking this thread as solved.

---

### Post by Bart_D on 2008-08-18
Do you mean that you intend on reformatting your entire hard drive and losing all existing data?

---

### Post by RPG Master on 2008-08-21
Got the disc in the mail today. Laptop's up and running on Vista. Now its time to install Ubuntu! (the right way....)

Yep I've lost all my data. Doesn't matter though, all music is from CDs. Games are either on disc, off of the internet for free or off of Steam. And pics are all backed up on CD.

---

