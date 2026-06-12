---
title: "does ubuntu use more power?"
date: 2006-02-08
forum: Hardware &amp; Laptops
---

### Post by m.musashi on 2006-02-08
I can almost hear the initial reaction to that but here is what I have observed. I've started to use Ubuntu more and more on my laptop but I seem to get less battery life. Today, for example, it ran down in a little more than 2 hours (I usually get 3 or more) and I wasn't really even using it. I was trying to trouble shoot and mostly just reading over config files and then letting it sit. When it went to screen saver I usually brought it back on the assumption that all those graphics would use more processor power. Maybe not.

Another symptom is that the laptop seems to run hotter. Yesterday the bottom got almost too hot to touch. I have not noticed this behavior in Windows so I'm wondering if ubuntu or Linux in general deal with power management differently and perhaps not as well.

Also, my laptop won't go to sleep or hibernate. The screen shuts off but it keeps running. I didn't know this and put it in its case for 30 minutes or so a while back and it had gotten quite warm.

Any thoughts, hints, suggestions?

---

### Post by stangbang on 2006-02-08
It sounds like you are just having a problem with acpi. try adding acpi=force or acpi=strict to your bootup options and see if this changes anything

---

### Post by m.musashi on 2006-02-08
[QUOTE=stangbang]It sounds like you are just having a problem with acpi. try adding acpi=force or acpi=strict to your bootup options and see if this changes anything[/QUOTE]

ACPI again? I've been having nothing but acpi problems on a desktop. Now it's a problem on my laptop too. 

Could you explain how I change boot options? Is it a file I edit or do I do it through preferences -> sessions?

Thanks.

---

### Post by funkydan2 on 2006-02-08
You need to edit a text file.

Run - 'sudo gedit /boot/grub/menu.lst' and put the acpi options into the line that specifies the kernel that you are booting with.

***Beware, you could make your system unbootable by doing this.  It might be best to post your menu.lst file here so that we can show you what to change it to***

---

### Post by m.musashi on 2006-02-09
[QUOTE=funkydan2]You need to edit a text file.

Run - 'sudo gedit /boot/grub/menu.lst' and put the acpi options into the line that specifies the kernel that you are booting with.

***Beware, you could make your system unbootable by doing this.  It might be best to post your menu.lst file here so that we can show you what to change it to***[/QUOTE]
Thanks for the offer to help. Here is the contents of my menu.lst.

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
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hda5 ro

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

title		Ubuntu, kernel 2.6.12-10-386 
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda5 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda5 ro single
initrd		/boot/initrd.img-2.6.12-10-386
boot

title		Ubuntu, kernel 2.6.12-9-386 
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda5 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda5 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		----------
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
makeactive
chainloader	+1
```

Thanks again.

---

### Post by funkydan2 on 2006-02-09
Change the first section after

> 
## ## End Default Options ##

title		Ubuntu, kernel 2.6.12-10-386 
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda5 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-386


and change the "kernel" line to this
> 
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda5 ro quiet splash acpi=force


and then save the file.  Reboot your machine and see what happens.  Alternatively try acpi=strict.

---

### Post by m.musashi on 2006-02-10
Thanks. I'll give that a try tomorrow. I've got network problems and I don't want to change too much at a time.

---

