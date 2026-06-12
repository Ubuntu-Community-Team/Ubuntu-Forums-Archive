---
title: "[SOLVED] Grub does not recognize Vista"
date: 2008-11-23
forum: General Help
---

### Post by raunchyrex on 2008-11-23
Hello guys.. I'm new in here so pardon me if my questions seem naive.
I use Vista on my 250gb HDD. Last night I got a 160gb Ubuntu 8.10 installed HDD from a friend. I connected both the hard disks. Now, when I boot my PC only Ubuntu loads! I can still find all the partitions on my 250gb HDD in the "Computer" folder though. How do I make GRUB recognize Vista?
:confused:

---

### Post by TeXtonyx on 2008-11-23
Usually I think grub is supposed to see Vista unless you disconnected
one of the drives for the installation. The file to edit is 
/boot/grub/menu.lst  gksudo gedit /boot/grub/menu.lst 
This will be found on your Ubuntu drive.

Make an entry for Vista under Other OS. Assuming Vista/250GB
is your master, its designation will be (hd0,0) which is sda1

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Vista
root		(hd0,0)
savedefault
chainloader	+1


There are more complex entries that require mapping so try
this one first. You can look them up using the Search window.

---

### Post by raunchyrex on 2008-11-23
> Usually I think grub is supposed to see Vista unless you disconnected
one of the drives for the installation.
Yes, as I said I got an Ubuntu pre-installed HDD from a friend. So, all I did was connect a 160gb HDD having Ubuntu 8.10 to my motherboard.

---

### Post by logos34 on 2008-11-23
> **TeXtonyx said:**
> 
title        Vista
root        (hd0,0)
savedefault
chainloader    +1

There are more complex entries that require mapping so try
this one first. You can look them up using the Search window.


raunchyrex,

like TeXtonyx said, you're going to need [mapping like this.  ]("http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk")

check 

sudo fdisk -l

whihc will show which partition vista is on.  It will probably be the first or second (maybe you have a recovery partition first).

so try root (hd1,0) or (hd1,1)

---

### Post by raunchyrex on 2008-11-23
Sorry pal, but I don't think I could understand what you are trying to say(No offense, am a complete n00B!!!) 
All I could make out is you want me to edit a **menu.lst** file.
I opened the file but couldn't understand a word!
I thought it would be only wise to show you how it looks before I change(probably ruin) something.
> 
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
hiddenmenu

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
# kopt=root=UUID=dbe763f0-3cfe-4cd9-8074-d60859f4179a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=dbe763f0-3cfe-4cd9-8074-d60859f4179a

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
# defoptions=quiet splash vga=773

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

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		dbe763f0-3cfe-4cd9-8074-d60859f4179a
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=dbe763f0-3cfe-4cd9-8074-d60859f4179a ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		dbe763f0-3cfe-4cd9-8074-d60859f4179a
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=dbe763f0-3cfe-4cd9-8074-d60859f4179a ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		dbe763f0-3cfe-4cd9-8074-d60859f4179a
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


Now, only if you could tell me how and where to add those lines!

**[COLOR="Red"]btw, I have a dual-boot between XP and Vista on my 250gb HDD(if that changes anything)[/COLOR]**

---

### Post by loomsen on 2008-11-23
Between End Default Options and the very End Of Debian Automagic...
Then run
sudo update-grub
after you saved and closed the file.


But i hope you're aware of that potential harm you could do to your computer ^^

---

### Post by raunchyrex on 2008-11-23
> But i hope you're aware of that potential harm you could do to your computer ^^
hey! what does that mean?? I'm in no mood to format my system! Can you please enlighten me?

---

### Post by TeXtonyx on 2008-11-23
The following is the tail of the file which you just posted, your
menu.lst file. Cut and paste what I added after the your last line
which is 
"### END DEBIAN AUTOMAGIC KERNELS LIST" 
I mean add/use what I wrote between the dotted lines, so that it
looks the same, but with no dotted lines. I want you to use
gksudo gedit /etc/boot/menu.lst 
and then copy and paste what I've added (between the dotted lines)
and append it right after the current last line of your file, menu.lst
which now reads, 
### END DEBIAN AUTOMAGIC KERNELS LIST (<- currently the last line)

I'm repeating the first instruction slightly differently, not 
changing meaning in the second instruction, they both mean the same. 
Merge what I've provided to the end of your menu.lst file. The 
easiest way is to cut and paste it and then save, but you can type it. 


title Ubuntu 8.10, memtest86+
uuid dbe763f0-3cfe-4cd9-8074-d60859f4179a
kernel /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

-------------------------------------------

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1

--------------------------------------------------

Yes, it does make a difference if you dual boot XP and Vista
on the first drive. If Vista is on the second partition which
means it comes after XP, then the Vista bootloader controls
both XP and Vista. So above, where it says, (hd0,0) , change the
0 to a 1 which means the second partition in grubspeak: (hd0,1)

(hd0,0) means first drive/first partition, that's just the way that 
grub numbers. If you use sudo fdisk -l, sda1 means (hd0,0)
first drive/first partition, and sda2 means first drive/second partition (hd0,1)

It can be a little tricky. Because sometimes Vista writes its bootloader
files to the XP partition. So try first, as I have it to be cut & pasted

title		Windows Vista/Longhorn (loader)
root		(hd0,0) 
savedefault
chainloader	+1

and if it doesn't work, just edit (hd0,0) to (hd0,1) and then save it.

I'm not exactly sure where the Vista bootloader files have been installed
to either the first or maybe the second partition. It is easiest for you
to just try the more likely entry first (hdo,0), and then try the other 
entry (hd0,1) if that fails. You have to reboot to test either entry.
Getting both XP and Vista to automatically mount from Ubuntu fstab is the
next step.

---

### Post by Lars2103 on 2008-11-23
I think the problem is in the BIOS, your new disk is now the disk you boot from - fix this in the BIOS, og switch the cables to the disks on the motherboard.

---

### Post by TeXtonyx on 2008-11-23
> **Lars2103 said:**
> I think the problem is in the BIOS, your new disk is now the disk you boot from - fix this in the BIOS, og switch the cables to the disks on the motherboard.

If he does that then he won't be able to boot Ubuntu. He will
have to download and install the free program Easybcd, and add
an OS under Linux, his Ubuntu listing. Either way he is going
to have to do some editing. And he might not have the computer
case open any longer... maybe his friend hooked that up for him.

---

### Post by Lars2103 on 2008-11-23
Sorry I misunderstood the question :-(
Regards Lars

---

### Post by raunchyrex on 2008-11-23
TeXtonyx,
I appended the text like you said and restarted my computer
With **(hd0,0)** set to **0**, I got "Starting up..." message and then nothing happened!
With **(hd0,0)** set to **1**, I got an error message!
So then I tried what **Lars2103** said and swapped the HDD to motherboard connections. Now I get **GRLDR** bootloader. I can load Vista/Xp but not Ubuntu!!!

> And he might not have the computer
case open any longer... maybe his friend hooked that up for him.
No, I did that myself.

---

### Post by TeXtonyx on 2008-11-23
Great! I suppose you need a more involved grub entry which uses
"map". But I'm not a purist who insists on using grub come hades or 
high water. It it ain't broke don't fix it. Easybcd is designed for 
Windows users. It doesn't have the sticker shock of grub's menu.lst 

Now that you've done this, use free Easybcd which is the graphical
boot interface (GUI) for Vista's bootloader method of bcdedit. 

[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1) the download link is way at the bottom

[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)
Here's a step-by-step screenshot guide to installing Ubuntu and getting it to be nice to Windows Vista's bootloader.

What you need is 2/3 of the way towards the bottom,
"Adding Ubuntu to the Vista Bootloader"

The should take you less than 5 minutes. Maybe 3 mintues to
download the program and install it. 2 minutes to launch
Easybcd and follow the pictures to add Ubuntu to Easybcd's menu

Remember that Ubuntu will be on the second drive, which is sdb = hd1
type 83 ext3. Don't pick the linux swap partition.

---

### Post by raunchyrex on 2008-11-23
Hey, TeXtonyx! Easybcd method worked like charm!
thanks!!!

---

### Post by TeXtonyx on 2008-11-23
You are very welcome. In case Windows (first drive) fails, Super
Grub Disk is handy to boot into Ubuntu while fixing Windows.
Another way is to change your drive boot order, to boot Ubuntu
first from the second drive. Besides the way you did it with
changing cables, one can do it from the bios setup, often entered
by tapping the Delete key when the computer very first boots up. I 
include a couple of screenshots so you can be familiar with this way.

You can change what choice is selected with the up and down arrow
keys. And at any one option, use the Enter key to get more choices,
which is how you would change "Third Boot Device" set to HDD-0 in
the screenshot to HDD-1 which is the second drive booting to Ubuntu.
You would move the red highlight from CDROM down a couple of lines so
that Third Boot Device HDD-0 is now hightlight red, and then use Enter
to expand your choice of drives to HDD-1 (or others) then move the
little dot from HDD-0 to HDD-1 with the up or down arrow key, and hit
Enter which closes that editing. Then F10 usually saves your setting changes.
Other manufacturer bios settings usually have a way to do this too. Or you
could change the Second Boot Device, Floppy, to HDD-1 before the HDD-0.

Easy after a few times of practice and you don't have to get grease
underneath your fingernails, an old mechanics joke. :-) Have fun!

---

### Post by raunchyrex on 2008-11-24
That was very insightful .. thanks pal :)

---

