---
title: "[SOLVED] My usplash somehow disappeared... how to resotore it?"
date: 2008-10-07
forum: General Help
---

### Post by chenguo4 on 2008-10-07
This is gonna sound pretty stupid, but I removed usplash in terminal, then I realized what I did and reinstalled it. But now, the bar that shows my startup and shutdown progress is gone, there's a text startup and black screen shutdown, but I'd really like my graphical progress bar back. 

I tried startup manager, and I have a grub background working. I set up a usplash screen, but I'm still getting a text startup. 

Thanks in advance!

---

### Post by zxscooby on 2008-10-07
is the nosplash option set in menu.lst?

---

### Post by chenguo4 on 2008-10-07
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color cyan/blue white/blue

#A splash image for the menu
splashimage=(hd0,6)/grub/splashimages/29962-grubuntu.xpm.gz

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
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux



This is my menu.lst. It looks like I have nothing at all regarding "nosplash." In fact it looks like I have nothing at all regarding splash, period.

---

### Post by justleen on 2008-10-07
you have no boot options, even...
are you sure that is your working version??

---

