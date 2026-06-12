---
title: "How to boot to Console Mode as an alternative in GRUB menu"
date: 2008-07-18
forum: General Help
---

### Post by cabbarosman on 2008-07-18
Hello,

I`d like to add a new option to the **menu.lst** so that I can boot to ubuntu in console mode without loading the X. Does anyone know how to do this?

```
title		Ubuntu GNU/Linux
root		(hd0,1)
kernel		/vmlinuz-2.6.24-19-generic root=UUID=5ed4c8d2-5e9c-40be-88cb-751182f366dc ro quiet splash
initrd		/initrd.img-2.6.24-19-generic
quiet
```

---

### Post by Potatoj316 on 2008-07-18
run this command in the terminal ```
sudo gedit /boot/grub/menu.lst
``` then scroll all the way to the bottom and paste it under the rest (or perhaps in the middle or the top, wherever you want it to come up in the grub menu)

---

### Post by cabbarosman on 2008-07-18
I guess I wasn't clear enough. 

The code I quoted at the end is the default option in menu.lst. What I want to is to add a new option(or profile, if you will) to the menu.lst which would let me boot to ubuntu without gdm. So it will just be command line interface. You can do this after booting to the *normal* ubuntu with CTRL+Alt+F1. All I want to do is booting directly to the console without spending time on loading gdm.

---

### Post by plucky on 2008-07-18
> **cabbarosman said:**
> I guess I wasn't clear enough. 

The code I quoted at the end is the default option in menu.lst. What I want to is to add a new option(or profile, if you will) to the menu.lst which would let me boot to ubuntu without gdm. So it will just be command line interface. You can do this after booting to the *normal* ubuntu with CTRL+Alt+F1. All I want to do is booting directly to the console without spending time on loading gdm.

It should already be there,it is called **recovery mode** and is the second selection in the grub menu.

Post output of ```
cat /boot/grub/menu.lst
```


Good Luck

---

### Post by cabbarosman on 2008-07-18
Unfortunately, recovery mode is only for "recovery" applications :) and does not provide the regular command line environment [except for the 'root shell', which I don't like especially in a command line-only interface]

I seek a regular ubuntu boot just without the gdm (so the result is similar to ctrl+alt+f1 after a standart boot)

All the solutions I could find online were basically about uninstalling gdm which I don't want since I use the GUI normally.

I hoped to add a new option to the grub menu that would boot to such a console mode. If it's not possible to do it from menu.lst, is there another way to accomplish this?

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
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

## Splash image!
splashimage (hd0,1)/grub/images/spider.xpm.gz

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
# kopt=root=UUID=5ed4c8d2-5e9c-40be-88cb-751182f366dc ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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

title		Ubuntu GNU/Linux
root		(hd0,1)
kernel		/vmlinuz-2.6.24-19-generic root=UUID=5ed4c8d2-5e9c-40be-88cb-751182f366dc ro quiet splash
initrd		/initrd.img-2.6.24-19-generic
quiet

#title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
#root		(hd0,1)
#kernel		/vmlinuz-2.6.24-19-generic root=UUID=5ed4c8d2-5e9c-40be-88cb-751182f366dc ro single
#initrd		/initrd.img-2.6.24-19-generic

#title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
#root		(hd0,1)
#kernel		/vmlinuz-2.6.24-16-generic root=UUID=5ed4c8d2-5e9c-40be-88cb-751182f366dc ro quiet splash
#initrd		/initrd.img-2.6.24-16-generic
#quiet

#title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
#root		(hd0,1)
#kernel		/vmlinuz-2.6.24-16-generic root=UUID=5ed4c8d2-5e9c-40be-88cb-751182f366dc ro single
#initrd		/initrd.img-2.6.24-16-generic

#title		Ubuntu 8.04.1, memtest86+
#root		(hd0,1)
#kernel		/memtest86+.bin
#quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
#title		Other operating systems:
#root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda4
title		Microsoft Windows XP
root		(hd0,3)
savedefault
makeactive
chainloader	+1

```

---

### Post by louieb on 2008-07-18
> **cabbarosman said:**
> ...I hoped to add a new option to the grub menu that would boot to such a console mode. If it's not possible to do it from menu.lst, is there another way to accomplish this?...

You need to somehow make it boot in runlevel 3. Don't know how to do that from GRUB. But heres how to change the default run level. [http://www.debianadmin.com/debian-and-ubuntu-linux-run-levels.html](http://www.debianadmin.com/debian-and-ubuntu-linux-run-levels.html)

Edit Its harder than I thought. In Ubuntu runlevels 2-5 are all the same - that is they all start GDM. Going to have to change one of the runlevels to not start GDM.

---

### Post by shreyasbforu on 2008-09-30
Yeah, you can add an option to grub to boot directly in Console mode.
Basically, copy and paste any boot entry which you want. Add ' 3' at end of the 'kernel' line in the entry. This will make the ubuntu boot in runlevel 3.

You can make this entry default if you want, by changing the value of default in the menu.lst

---

### Post by lswb on 2008-10-04
Ubuntu uses "upstart" rather than the older init system and unfortunately the default startup scripts do not support booting to runlevels other than 2 (default) or S (recovery mode) However it is possible to change the script /etc/event.d/rc-default so that different runlevels can be specified on the kernel command line and recognized at boot time. Here is a blog post that explains it pretty well:
[http://caulfield.info/emmet/2008/03/add-a-textonly-runlevel-to-ubu.html](http://caulfield.info/emmet/2008/03/add-a-textonly-runlevel-to-ubu.html)

I got the idea from the blog author but I use a different modification to /etc/event.d/rc-default on my own system. Here is what I use:
```

# rc - runlevel compatibility
#
# This task guesses what the "default runlevel" should be and starts the
# appropriate script.
#
# Edited to support booting to non-default runlevel by adding a
# single digit from [2345] as last option on kernel command line
# at boot. See elif statement below. lsw 9/7/2008
#

start on stopped rcS

script
	runlevel --reboot || true

	if grep -q -w -- "-s\|single\|S" /proc/cmdline; then
	    telinit S
	elif RL="$(grep -o "[[:blank:]][2345]$" /proc/cmdline || true)"; then
	    if [ -n "$RL" ]; then
		telinit $RL
	    else
		telinit 2
	    fi
	elif [ -r /etc/inittab ]; then
	    RL="$(sed -n -e "/^id:[0-9]*:initdefault:/{s/^id://;s/:.*//;p}" /etc/inittab || true)"
	    if [ -n "$RL" ]; then
		telinit $RL
	    else
		telinit 2
	    fi
	else
	    telinit 2
	fi
end script



```

I wrote my rc-default so that a single digit at the end of the kernel command line would boot up in that runlevel, which is how it is done on most other distributions (and also on earlier versions of ubuntu, IIRC dapper was the last to use the old init system)

Note that as Emmet Caulfield states in his blog you must still configure the different runlevels for the services you want and if you want the choice to show up in your grub menu you must modify /boot/grub/menu.lst appropriately. Also, remember that a typo or error in either /etc/event.d/rc-default or in /boot/grub/menu.lst can make your system unbootable. Make sure you know how to boot it up another way and know how to mount the filesystem and edit these files, just in case!

---

### Post by Gorbon Treeman on 2008-10-24
there has to be a simpler way somehow...

in ubuntu 8.10 u got a little menu in recovery mode, with xfix, clean, etc... and a link with "root - drop to root shell"

that would be usefull in the future (I wanted to update/upgrade from shell without booting to gdm) but networking didn't work.

I tried /etc/init.d/networking start but that didn't work... any ideas on this? how to start at least networking, so you can update/upgrade without gdm?

---

### Post by theDaveTheRave on 2008-10-24
Dear All,

I would like to have a similar ooption available on my server.

I've decided to load on Gnome for my colleagues who may find they need to perform admin tasks on the SQL server, and prefer to use the a GUI rather than the command line,

What I would like my system to do is boot into a fully functioning syste, just without the gnome desktop, but with all the other "server" services running.

Then it can just sit there doing is "stuff" without wasting resources (allthough that isn't exacly a big issue with this server.... I'm not entirely sure why they put a top end graphics card in there when they wanted it to be a server.... maybee I'll have to put Beryl and cubes onto the system just for demo purposes - or grab the card and drop it into my works desktop!?).

anyway, if it is in a command line for login that is fine, then all my colleagues would have to do is run <startx> if they really want a gui.

I suspect however once they get used to it they will do admin from a laptop hardwired through the spare ethernet card and SSH to the server - or similar....

I'm sure that when I set up my home server on Debian this happened automatically - so I'm sure it is possible.

Dave

---

### Post by plucky on 2008-10-24
> **Gorbon Treeman said:**
> there has to be a simpler way somehow...

in ubuntu 8.10 u got a little menu in recovery mode, with xfix, clean, etc... and a link with "root - drop to root shell"

that would be usefull in the future (I wanted to update/upgrade from shell without booting to gdm) but networking didn't work.

I tried /etc/init.d/networking start but that didn't work... any ideas on this? how to start at least networking, so you can update/upgrade without gdm?

Try ```
ifup eth0
``` or whatever your network interface is known by.

Good Luck

---

### Post by lswb on 2008-10-24
> **Gorbon Treeman said:**
> there has to be a simpler way somehow...

in ubuntu 8.10 u got a little menu in recovery mode, with xfix, clean, etc... and a link with "root - drop to root shell"

that would be usefull in the future (I wanted to update/upgrade from shell without booting to gdm) but networking didn't work.

I tried /etc/init.d/networking start but that didn't work... any ideas on this? how to start at least networking, so you can update/upgrade without gdm?

I'm not sure about 8.10, but if it is configured the same way 8.04 is, the problem with trying to start networking from /etc/init.d/networking has to do with Network Manager and the /etc/network/interfaces file. Network Manager likes this file to be basically empty; it won't try to manage any interfaces that are listed there. /etc/init.d/networking calls ifup/ifdown which in turn depend on /etc/network/interfaces for their configuration so it's kind of a catch 22 if you want to use NM for the Desktop but /etc/interfaces for text mode. Some workaround would be to put ifconfig commands to start networking in your /etc/rc.local or just run them on the command line. Assuming you are using wired ethernet & get an ip address through dhcp, the commands are: 

ifconfig eth0 up
dhclient eth0

(Use sudo if on command line as regular user, and change eth0 if necessary to the name of the interface for your system.)

---

### Post by lswb on 2008-10-24
> **theDaveTheRave said:**
> Dear All,

I would like to have a similar option available on my server.

I've decided to load on Gnome for my colleagues who may find they need to perform admin tasks on the SQL server, and prefer to use the a GUI rather than the command line,

What I would like my system to do is boot into a fully functioning syste, just without the gnome desktop, but with all the other "server" services running.

.....

Dave


If you want to always boot to text-mode then all you need to do is have your default run level configured that way. You can change the statup links for ubuntu's default runlevel 2, or use an /etc/inittab file to have the system start in say runlevel 3 and configure rl3 the way you want. That will leave runlevel 2 as the "stock" configuration which you can switch to with the telinit command if desired.

If you decide to use /etc/inittab, you can put this line in it to make the system boot to rl 3

id:3:initdefault:

I like to use the sysv-rc-conf program to set up links for startup. It is in the repositories, or you can use the command line program update-rc.d or change the links manually if you prefer. You want to disable the links for gdm, usplash is not needed, and possibly some others can be eliminated for your text-mode runlevel.

Your server is presumably always using the same network configuration so you don't need network manager, you can do all your network configuration via /etc/network/interfaces. If so I would just uninstall NM from the server if it was brought in when you installed the gnome desktop.

---

