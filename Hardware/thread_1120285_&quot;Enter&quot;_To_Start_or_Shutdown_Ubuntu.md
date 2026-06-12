---
title: "&quot;Enter&quot; To Start or Shutdown Ubuntu?"
date: 2009-04-08
forum: Hardware
---

### Post by octobermagic on 2009-04-08
**I just installed the latest version of Ubuntu on my Hp Pavillion Notebook. Everything works great.....however I do have this one nagging problem. Whenever I turn on my laptop, it shows the ubuntu logo and the loading bar.....however it would load to a certain point and then I would have to hold down the "Enter" key for it to keep on loading. It also does this whenever I put the pc to sleep or shutdown....again i would have to hold down the "enter" key. Has anyone run into this problem? Any ideas on how to fix it? I did a clean install of the Ubuntu OS......i just don't see what the problem could be.....any help would be appreciated.**

---

### Post by _Purple_ on 2009-04-08
Which version of Ubuntu are you using? 8.10 or 9.04?

---

### Post by octobermagic on 2009-04-08
I am using 8.10.  It seems as if the OS is going into a step by step conformation mode where you have to keep hitting enter to continue....only problem is I can't see it because of the GUI.  Its a normal Ubuntu logo with the loading bar at the bottom and it just halts untill I hold down enter.  Very frustrating.

---

### Post by _Purple_ on 2009-04-08
Try to edit Grub and add acpi=noirq to the end of the first kernel statement. 

```
sudo nano /boot/grub/menu.lst 
```

Then save and reboot. I am not sure if this will fix your problem.

---

### Post by octobermagic on 2009-04-08
I still kind of a linux newb yet but this is the screen i get when i do the sudo command. Exactly where do i put "acpi=noirq "?


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
timeout         3

^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Text^T To Spell

---

### Post by _Purple_ on 2009-04-08
You didn't post the entire grub file. Run the following command:

```
gksudo gedit /boot/grub/menu.lst
```

Can you please post the contents?

---

### Post by octobermagic on 2009-04-08
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
# kopt=root=UUID=05a411ef-7621-49fb-896f-66b6beff50a9 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=05a411ef-7621-49fb-896f-66b6beff50a9

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

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		05a411ef-7621-49fb-896f-66b6beff50a9
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=05a411ef-7621-49fb-896f-66b6beff50a9 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		05a411ef-7621-49fb-896f-66b6beff50a9
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=05a411ef-7621-49fb-896f-66b6beff50a9 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		05a411ef-7621-49fb-896f-66b6beff50a9
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=05a411ef-7621-49fb-896f-66b6beff50a9 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		05a411ef-7621-49fb-896f-66b6beff50a9
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=05a411ef-7621-49fb-896f-66b6beff50a9 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		05a411ef-7621-49fb-896f-66b6beff50a9
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by Stupendoussteve on 2009-04-08
If you hit Alt F1 it will get out of the graphical booting and view the text boot process. You should be able to see if something is causing it to go into interactive mode.

---

### Post by _Purple_ on 2009-04-08
```
# kopt=root=UUID=05a411ef-7621-49fb-896f-66b6beff50a9 ro
```

At the end of this line add acpi=noirq like this:

```
# kopt=root=UUID=05a411ef-7621-49fb-896f-66b6beff50a9 ro acpi=noirq
```


Then save the file and run the following command in terminal:

```
sudo update-grub
```

---

### Post by octobermagic on 2009-04-08
Oo wow thanks soooo much it worked like a charm.  Is there another line in there that I can edit becasue it does the same thing when i have to shutdown or restart.

---

### Post by StooJ on 2009-04-08
> **_Purple_ said:**
> You didn't post the entire grub file. Run the following command:

```
sudo gedit /boot/grub/menu.lst
```

Can you please post the contents?

Just being picky, Purple, but it's recommended to use gksu or gksudo for graphical programmes. Keep sudo for terminal applications.

See [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo) for more info.

Sorry to nag.

---

### Post by _Purple_ on 2009-04-08
> **octobermagic said:**
> Oo wow thanks soooo much it worked like a charm.  Is there another line in there that I can edit becasue it does the same thing when i have to shutdown or restart.

Glad it worked. :)
 Did you try to restart after changing the settings? Are you still having problems?

---

### Post by _Purple_ on 2009-04-08
> **StooJ said:**
> Just being picky, Purple, but it's recommended to use gksu or gksudo for graphical programmes. Keep sudo for terminal applications.

See [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo) for more info.

Sorry to nag.


Thanks for the link. I appreciate it. :)
So far didn't face any problem regarding this as in most cases sudo worked fine.

---

### Post by octobermagic on 2009-04-08
Yeah i restared the computer and it booted up like a charm.  I was wondering though if there is another line in that file that I  can edit becasue i was having the same problem when i shutdown or restard the pc.

---

### Post by _Purple_ on 2009-04-09
> **octobermagic said:**
> Yeah i restared the computer and it booted up like a charm.  I was wondering though if there is another line in that file that I  can edit becasue i was having the same problem when i shutdown or restard the pc.

 I am not sure about that. May be you can take a look at [this](http://ubuntuforums.org/showpost.php?p=2260791&postcount=10). It might solve your problem. :)

---

### Post by octobermagic on 2009-04-09
Thanks a bunch purple everything works.  It turns out I had to restart the PC after I made the changes...then it started to shutdown and restart normally.  TY once again.

---

### Post by _Purple_ on 2009-04-09
Glad to know. My pleasure. :)

---

