---
title: "grub splash screen in 8.04.2 LTS"
date: 2009-01-27
forum: Installation &amp; Upgrades
---

### Post by linux_challenged on 2009-01-27
Here is the first section of my grub menu:

## ## End Default Options ##
		
title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=ebad1fc5-2b2e-4c4d-8680-92ad00646118 ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet


I can't figure out where to put the line that tells the location of the splash image I would like to use...

I know it is a real gnubee question, but if someone can help me, I sure would appreciate it. 

thanx in advance...

---

### Post by spcwingo on 2009-01-27
You could install startup manager and do it with a GUI.;)

---

### Post by linux_challenged on 2009-01-27
okay but won't that deny me the thrill of working with the cli?

---

### Post by CowzRule on 2009-01-27
Here's where mine is

> ## ## End Default Options ##

[COLOR="Red"]splashimage=(hd1,0)/boot/grub/splash.xpm.gz[/COLOR]

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=fee1734b-b127-4ba0-855c-0648ec89b134 ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet
savedefault
It's right above the first Ubuntu menu entry.

---

### Post by linux_challenged on 2009-01-28
well, nothing has worked so far - following is my complete boot menu:

## ## End Default Options ##

		splashimage=(hd0,4)/boot/grub/splash.xpm.gz
		
title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=ebad1fc5-2b2e-4c4d-8680-92ad00646118 ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet


title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=ebad1fc5-2b2e-4c4d-8680-92ad00646118 ro single
initrd		/boot/initrd.img-2.6.24-23-generic


title		Ubuntu 8.04.2, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		M$ Windoze XP Pro SP3
root		(hd0,0)
savedefault
makeactive
chainloader	+1


Is it possible that the splashimage line isn't correct? I forgot to mention that this is a dual boot setup.

---

### Post by CowzRule on 2009-01-29
Open a terminal and type:
> sudo update-grub
The output should look something like this:
> Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... found: /boot/grub/splash.xpm.gz
Found kernel: /boot/vmlinuz-2.6.24-23-generic
Updating /boot/grub/menu.lst ... done
That will automatically put the correct line in your menu.lst file (in the spot I showed you).
If it showed any errors, copy and paste them here and we'll go from there.

---

