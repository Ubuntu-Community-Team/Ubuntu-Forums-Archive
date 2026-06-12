---
title: "Installing Dapper on a USB drive"
date: 2006-06-01
forum: Hardware &amp; Laptops
---

### Post by jerseyboy91 on 2006-06-01
I've recently bought an external hard drive, so I came up with the idea to install Ubuntu on it. I used [DaBruGo's tutorial]("http://www.ubuntuforums.org/showthread.php?t=80811") to install the OS, and I got through all the steps except the one where you start up Ubuntu for the first time. I got Error 2 on GRUB, but I don't think I messed up on editing the bootloader file on Vim. I could be wrong though. Here's the menu.lst file: 

NOTE: I bolded the areas I edited.

# menu.lst - See: grub( 8 ), info grub, update-grub( 8 )
# grub-install( 8 ), grub-floppy( 8 ),
# grub-md5-crypt, /usr/share/doc/grub
# and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
default 0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line) and entries protected by the
# command 'lock'
# e.g. password topsecret
# password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
[B]# title Windows 95/98/NT/2000
# root (hd0,0)
# makeactive
# chainloader +1[/B]
#
[B]# title Linux
# root (hd0,1)
# kernel /vmlinuz root=/dev/hda2 ro[/B]
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
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/sda1 ro acpi=off

[B]## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)[/B]

## should update-grub create alternative automagic boot options
## e.g. alternative=true
## alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
## lockalternative=false
# lockalternative=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
## altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
## howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
## memtest86=false
# memtest86=true

## ## End Default Options ##

[B]title Ubuntu, kernel 2.6.12-9-386
root (hd0,0)
kernel /boot/vmlinuz-2.6.12-9-386 root=/dev/sda1 ro acpi=off quiet splash
initrd /boot/initrd.img-2.6.12-9-386
savedefault
boot

title Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.12-9-386 root=/dev/sda1 ro acpi=off single
initrd /boot/initrd.img-2.6.12-9-386
boot

title Ubuntu, memtest86+
root (hd0,0)
kernel /boot/memtest86+.bin
boot[/B]

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
[B]title Microsoft Windows XP Home Edition
root (hd1,0)
savedefault
chainloader +1[/B]


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
[B]title Windows NT/2000/XP
root (hd0,0)
savedefault
chainloader +1[/B]

______________________________________

Any ideas? I'm thinking I'm not supposed to put (hd0,0) or something like that, but I'm not patient enough to try over and over. :confused: Thanks in advance.

---

### Post by tonyr on 2006-06-01
Which install cd are you using?  The kernel version in your **menu.lst** is old in terms
of Dapper development releases. The current version is **2.6.15-23**. If
you can access your USB drive, look in /boot to see what version is actually
installed.

---

### Post by tonyr on 2006-06-01
Here's a link to GRUB Errors:
[URL="http://www.uruk.org/orig-grub/errors.html"]
http://www.uruk.org/orig-grub/errors.html[/URL]

FWIW, Error 2 is:
2 : "Selected disk doesn't exist"
This error is returned if the device part of a device- or full filename refers to a disk or BIOS device that is not present or not recognized by the BIOS in the system.

---

### Post by Kelley_Jernigan on 2006-06-01
JB91,

I hope this can be made to work.

I would like to do the same since I need to keep XP Pro on my PC right now.

Plus, if it works, I can take my USB drive with me when I visit family, plug it into thier PC's and it will be just like taking my PC with me.

Kelley

---

### Post by jerseyboy91 on 2006-06-01
[QUOTE=tonyr]Here's a link to GRUB Errors:
[URL="http://www.uruk.org/orig-grub/errors.html"]
http://www.uruk.org/orig-grub/errors.html[/URL]

FWIW, Error 2 is:
2 : "Selected disk doesn't exist"
This error is returned if the device part of a device- or full filename refers to a disk or BIOS device that is not present or not recognized by the BIOS in the system.[/QUOTE]
So I would have to change the (hd0,0) to make the BIOS recognize the USB device?

And tonyr, I'm gonna get the latest version shipped, so I'll try seeing if that works.

---

### Post by tonyr on 2006-06-01
[QUOTE=jerseyboy91]So I would have to change the (hd0,0) to make the BIOS recognize the USB device?
[/QUOTE]

I don't think it's that simple, but I'm not a Grub expert by any means. I found
some references that might provide some clues. The third one is a collection
from a forum.  The relevant message is several entries down the list.  None of
these is about Ubuntu in particular, but Linux is Linux and Grub is Grub.  You
might also try contacting the authors individually.  One of the authors in fact
suggests that you can contact him if you have problems/questions.

It may be a naming problem, but it may also be a timing issue.  Some of these
articles talk about adding a **rootdelay** argument to the **kernel** line in the GRUB
entry to allow the USB module time to load and find the USB drive.  That's about
the best I can offer for now.  Good Luck.

EDIT: I guess it would be a good idea to include the links, since I was so bold as to mention them:
[http://www.mepis.org/node/8785]("http://www.mepis.org/node/8785")
[http://forums.frugalware.org/index.php?t=msg&goto=2875&rid=0&#msg_2875]("http://forums.frugalware.org/index.php?t=msg&goto=2875&rid=0&#msg_2875")
[http://forums.devarticles.com/the-lizard-lounge-10/linux-install-suse-on-an-external-usb-drive-6250.html]("http://forums.devarticles.com/the-lizard-lounge-10/linux-install-suse-on-an-external-usb-drive-6250.html")

---

### Post by jerseyboy91 on 2006-06-01
Thanks, I'm gonna look into these forum links and see if I can come up with anything. I'll edit this message if I get it to work.

---

### Post by jerseyboy91 on 2006-06-02
[QUOTE=tonyr]I don't think it's that simple, but I'm not a Grub expert by any means. I found
some references that might provide some clues. The third one is a collection
from a forum.  The relevant message is several entries down the list.  None of
these is about Ubuntu in particular, but Linux is Linux and Grub is Grub.  You
might also try contacting the authors individually.  One of the authors in fact
suggests that you can contact him if you have problems/questions.

It may be a naming problem, but it may also be a timing issue.  Some of these
articles talk about adding a **rootdelay** argument to the **kernel** line in the GRUB
entry to allow the USB module time to load and find the USB drive.  That's about
the best I can offer for now.  Good Luck.

EDIT: I guess it would be a good idea to include the links, since I was so bold as to mention them:
[http://www.mepis.org/node/8785]("http://www.mepis.org/node/8785")
[http://forums.frugalware.org/index.php?t=msg&goto=2875&rid=0&#msg_2875]("http://forums.frugalware.org/index.php?t=msg&goto=2875&rid=0&#msg_2875")
[http://forums.devarticles.com/the-lizard-lounge-10/linux-install-suse-on-an-external-usb-drive-6250.html]("http://forums.devarticles.com/the-lizard-lounge-10/linux-install-suse-on-an-external-usb-drive-6250.html")[/QUOTE]
I just noticed that I, unfortunately, cannot add the rootdelay argument to the kernel line because I have to start up GRUB for that. I cannot do this because it would say this:

GRUB Loading stage1.5

GRUB loading, please wait...
Error 2

Then it just stops there, and I have to press Ctrl+Alt+Del to restart the computer. I've been trying to edit the menu.lst file to no avail. Right now, I'm wondering if it has something to do with the "groot" part of the file, but I'm not sure.

EDIT: Never mind, found the kernel thing in the menu.lst file.

---

### Post by tonyr on 2006-06-02
I assume you are using a Breezy CD of some kind.  Is it the LiveCD or an Install CD?
You should be able to boot that into a **rescue** or **expert** mode, mount
your USB drive if it's not already mounted, and get at the **menu.lst** file
that way.

---

### Post by jerseyboy91 on 2006-06-02
I've mounted it and gotten to the file and the kernel line, it's just that I don't think the (hd0,0) is the one I'm supposed to use, or it would work by now. Also, I've tried the rootdelay one, but I'm not sure about where in the kernel line it goes: 

kernel /boot/vmlinuz-2.6.12-9-386 root=/dev/sda1 **ro** acpi=off quiet splash

Would I have to replace the "ro" with "rootdelay" or would I put the rootdelay=10 after it? Anyone else's help would be greatly appreciated.

---

### Post by tonyr on 2006-06-02
From what I've read, the system should think that (hd0,0) is your USB drive.
Don't replace the **ro**.  Put the **rootdelay** before the **root=**,
and try 15 first.  If that works (fingers crossed),  you can try 10 later.

EDIT: Well, I read the tutorial a little closer, and it looks like this **rootdelay**
thing just duplicates what is done in **STEP 9** when you added **WAIT=12**
to **initramfs.conf**.  It means this **readonly** thing may not have any effect at all.

---

### Post by Izzie on 2006-06-02
I read in the forums about the same kind of problem in a thread about dual booting
seems grub tends to put itself in the MBR of the internal drive, sometimes it even install itself in the IDE drive MBR while you installed the system on the sata one.

Anyaways, to test if this is the case for you just have to change the disk to boot from in the BIOS to the internal drive (even if it contains no OS). If the grub error disappear that means your problem is grub has installed in the MBR of the wrong disk. to fix it you will have to move grub install to the correct drive.

---

### Post by jerseyboy91 on 2006-06-03
But I told it to not install in the internal hard drive (I put in "No" when it asked me to install it into the MBR). The error isn't there, but I don't see the GRUB menu when I boot from the internal drive, which probably means it's installed into the external drive, so it's a problem in one of the edited files.

---

