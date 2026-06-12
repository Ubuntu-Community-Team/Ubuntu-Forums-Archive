---
title: "help neede with nvidia"
date: 2007-03-31
forum: Hardware &amp; Laptops
---

### Post by NIKOSHIBA on 2007-03-31
hi all,
right after fresh install my xorg.conf (sections "device" and "monitor") looked like this:
```
Section "Device"
	Identifier	"nVidia Corporation G70 [GeForce Go 7600]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection
```

max scree resolution was 1024x768
then i just installed nvidia-glx from repos. and my xorg.conf still looked the same. so i manually changed "nv" into "nvidia" and under section "screen" added resolution "1280x800". well it works and resolution is fine. (what tha hell you want then? you would ask...i'm getting there, gimi a sec)

q1 - isn't nvidia-glx suppose to update xorg.conf ?
q2 - HorizSync	28-51 and VertRefresh 43-60. is this a standard?, i couldn't find this specs for my screen
q3 - should i uninstall preinstalled desktop effects (compiz) from system before i install beryl. and should i install beryl from repos or accordingly beryl project web page?


after i ran after fresh install of feisty ```
sudo apt-get dist-upgrade
``` i got in menu.lst two versions of ubuntu:
```
title		Ubuntu, kernel 2.6.20-13-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-13-generic root=UUID=cbb13fc7-568f-4200-9f42-94caa40f207b ro quiet splash
initrd		/boot/initrd.img-2.6.20-13-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-13-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-13-generic root=UUID=cbb13fc7-568f-4200-9f42-94caa40f207b ro single
initrd		/boot/initrd.img-2.6.20-13-generic

title		Ubuntu, kernel 2.6.20-12-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-12-generic root=UUID=cbb13fc7-568f-4200-9f42-94caa40f207b ro quiet splash
initrd		/boot/initrd.img-2.6.20-12-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-12-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-12-generic root=UUID=cbb13fc7-568f-4200-9f42-94caa40f207b ro single
initrd		/boot/initrd.img-2.6.20-12-generic
```
 
q4 - can someone explain me why?

thnx

my hardware:
[http://nl.computers.toshiba-europe.com/cgi-bin/ToshibaCSG/jsp/productPage.do?service=NL&PRODUCT_ID=122801#0]("http://nl.computers.toshiba-europe.com/cgi-bin/ToshibaCSG/jsp/productPage.do?service=NL&PRODUCT_ID=122801#0")

---

### Post by matburton on 2007-03-31
Q1 - I'm pretty sure its not suppost to change your xorg.conf. If you want something to do that all for you then have a look at [[COLOR="Blue"]automatix,[/COLOR]]("http://www.getautomatix.com/") it will handle installing the driver for you.

Q4 - That's because after your upgrade you have a new kernal version. But in case it has bugs you get the choice to use the old one as well with grub.

---

### Post by compiledkernel on 2007-03-31
Automatix is unsupported software by the community. These forums do not support it either. If you have further difficulties with Automatix, you should refer back to their forums at [www.getautomatix.com](www.getautomatix.com) for further help.

Let me firmly reiterate that Automatix is just as it is --

"automatix is a script that tries to install some software, and often
fails and breaks systems. We don't provide support for it, and we strongly
discourage its use. Problems caused by Automatix are often hard to track
and solve, and it might sometimes be easier to !install a fresh copy of
Ubuntu."

---

### Post by NIKOSHIBA on 2007-04-01
> **compiledkernel said:**
> Automatix is unsupported software by the community. These forums do not support it either. If you have further difficulties with Automatix, you should refer back to their forums at [www.getautomatix.com](www.getautomatix.com) for further help.

Let me firmly reiterate that Automatix is just as it is --

"automatix is a script that tries to install some software, and often
fails and breaks systems. We don't provide support for it, and we strongly
discourage its use. Problems caused by Automatix are often hard to track
and solve, and it might sometimes be easier to !install a fresh copy of
Ubuntu."

i have never sad that i used automatix, and i endeed havn't. is my english that bad that you couldn't get that from my post?

---

