---
title: "Grub"
date: 2005-05-17
forum: Hardware &amp; Laptops
---

### Post by S3RiOUS on 2005-05-17
hi can anyone tell me how to set up grub so that it boots into xp unless you press a key which then allows you to select the operating system to boot (like in fedora) thanks

---

### Post by spd106 on 2005-05-17
Hi, you need to edit the **/boot/grub/menu.list**

If you set the default to boot xp (remember to start counting at zero).
Then uncomment the line  **#hiddenmenu**. 

This means you just press esc to go through to the menu.

---

### Post by S3RiOUS on 2005-05-17
thanks but it doesnt quite work, it pauses but after it boots no operating system and takes me to the list probably because the default os is set wrong

this is my menu.lst if u know whats wrong, thanks

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
default		1

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

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
## by the debian update-grub script except for the default optons below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/sda5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

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

title		Ubuntu, kernel 2.6.10-5-386 
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/sda5 ro quiet splash
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot


### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows
root		(hd0,1)
savedefault
makeactive
chainloader	+1


```

---

### Post by zupermanz on 2005-05-17
have you tried grubconf?
from there you can set up the default op system at bootup

---

### Post by alastair on 2005-05-17
The "default" (1) is :

```

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

```

Is this correct? The "root" line on its own looks wrong to me (but I have not done any research).

Try removing those 4 lines.

---

### Post by nad on 2005-05-17
Your default line number is 8, I believe.

This is easily tested and adjusted by rebooting. Grubconf is a graphical editor for this file.

---

### Post by spd106 on 2005-05-19
HI, you could try removing the four lines as alastair suggests or i'm quite sure you can change the default to 2 
ie

title		Ubuntu, kernel 2.6.10-5-386        =        0

title		Other operating systems:             =        1

title		Microsoft Windows                        =        2


This should be ok, any trouble use Grubconf as suggested before.

---

