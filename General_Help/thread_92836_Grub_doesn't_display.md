---
title: "Grub doesn't display"
date: 2005-11-20
forum: General Help
---

### Post by qbproger on 2005-11-20
When i'm booting my computer with the grun installed with ubuntu it doesn't display at all.  I tried out Fedora it displays, but other things on Fedora don't work as well as on ubuntu (i can't get it to go to the console not in X which is a pain and means I can't install nvidia drivers).  Does anyone have any suggestions on how to get grub on ubuntu to display.  It's working because if i press down and enter it boots to windows, but i can't see anything, so I'm pretty much guessing when to hit it.  Rather annoying.

Any help is appreciated
Joe

---

### Post by taurus on 2005-11-20
Run this command at the prompt and post the output of it,

sudo more /boot/grub/menu.lst

---

### Post by qbproger on 2005-11-20
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

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
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=/dev/hda2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

## should update-grub create alternative automagic boot options
## e.g. alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
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
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## ## End Default Options ##

title           Ubuntu, kernel 2.6.12-9-686
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.12-9-686 root=/dev/hda2 ro quiet splash
initrd          /boot/initrd.img-2.6.12-9-686
savedefault
boot

title           Ubuntu, kernel 2.6.12-9-686 (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.12-9-686 root=/dev/hda2 ro single
initrd          /boot/initrd.img-2.6.12-9-686
boot

title           Ubuntu, kernel 2.6.12-9-386
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/hda2 ro quiet splash
initrd          /boot/initrd.img-2.6.12-9-386
savedefault
boot

title           Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/hda2 ro single
initrd          /boot/initrd.img-2.6.12-9-386
boot

title           Ubuntu, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

```

that's the whole file.

---

### Post by taurus on 2005-11-20
What if you remove the "#" sign in front of hiddenmenu...

---

### Post by qbproger on 2005-11-20
That didn't seem to work.

Any other suggestions?

---

### Post by qbproger on 2005-11-22
bump

anyone have any ideas?

Please

---

### Post by amohanty on 2005-11-23
Your menu.lst file looks fine. I cant see any obvious problems.

This might sound sort of stupid but what does the screen look like? Is it all white? The thing is that the default grub display is white on black, so if by some chance all you see is white that could be a problem there.

AM

---

### Post by qbproger on 2005-11-24
the entire screen is black, I don't see anything at all.  I know something is going on behind the scenes though, cause if i press up and down i can get to windows XP, just it's really a pain trying to guess where i am.

---

### Post by qbproger on 2005-11-26
bump

any other suggestions?

Thanks in advance.

---

### Post by paddyg on 2005-11-26
this may sound stupid too, but let's try changing colours, say yellow/blue
```

# Pretty colours
color yellow/blue

```
(uncomment the color line and select some colours you like...)

---

### Post by qbproger on 2005-11-26
after i edit menu.lst i don't have to run any grub app do i?

---

### Post by paddyg on 2005-11-26
Nope

---

### Post by qbproger on 2005-11-26
ok, then that didn't work.

Any other suggestions?

---

### Post by amohanty on 2005-11-26
In the absence of anything obviously wrong with your setup, I suggest you do thwo things:
1. Search the forum and check all GRUB related posts, there are tons of them.
2. AND/OR just reinstall grub ala:
[http://ubuntuforums.org/showthread.php?t=24113&highlight=reinstall+grub](http://ubuntuforums.org/showthread.php?t=24113&highlight=reinstall+grub)

HTH
AM

EDIT: somethign I found on google, take a look and see if it is a similar problem:
[http://www.hyperborea.org/journal/archives/2005/04/29/invisible-grub-boot-menu/](http://www.hyperborea.org/journal/archives/2005/04/29/invisible-grub-boot-menu/)

---

### Post by qbproger on 2005-11-27
that second link is what did the trick here is what i did:

looked at this grub.conf cause we don't have one in ubuntu.  I added the splashimage line to the menu.lst file.

splashimage=(hd0,1)/boot/splash.xpm.gz
(i put it in the /boot/ folder)

I used this splash.xpm.gz:
[http://cvs.opensolaris.org/source/xref/on/usr/src/grub/splash.xpm.gz](http://cvs.opensolaris.org/source/xref/on/usr/src/grub/splash.xpm.gz)

Thanks, you rock.

---

