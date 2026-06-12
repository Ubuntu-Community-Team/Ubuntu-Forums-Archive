---
title: "Cannot Boot 9.04 CD on PowerMac G4"
date: 2009-07-24
forum: Installation &amp; Upgrades
---

### Post by orgarmo on 2009-07-24
I am both new in mac and linux, and would like to experience ubuntu on mac, but seems it can't be done easily......

I burnt my ubuntu 9.04 i386.iso from a win xp pc, and boot it on my powermac G4, but it cannot regonized the cd. Is it wrong to burn the cd from window xp pc, or should I use unother iso?

The hd of my powermac G4 is in unix format, is it ok?
I was managed to use disk utility to change to into fat32, but the whole disk utility is read-only, all list box and buttons are disabled.

---

### Post by philcamlin on 2009-07-24
hold down c while booting :popcorn:

---

### Post by orgarmo on 2009-07-24
yes, i tried to hold c when boot, not working
also, hold option when boot, not working too
and also, can't find the cd for boot in system preference.

---

### Post by JOHNNYG713 on 2009-07-24
You have the wrong architecture i386 is 32 bit pc, to boot on a mac you need ubuntu "PPC"

---

### Post by starcraft.man on 2009-07-24
The problem is your trying to boot an x86 image on powerPC hardware. Not gonna work unless a wizard comes by and says some magic words :).

[PowerPC ports.]("http://cdimage.ubuntu.com/ports/releases/9.04/release/") Download and burn, then enjoy. I can't support beyond that, I don't own Macs.

---

### Post by orgarmo on 2009-07-24
thank you i dwonloaded the alternative ppc 9.04
it can boot now, but the installation stucks at detect network device

what should I do?

---

### Post by JOHNNYG713 on 2009-07-25
I have had problems to with trying to install 9.04, so what I did (after many trial and errors) was download 8.04 live cd (its the only one I found that loads and works right),and install 8.04, then upgrade from there,If you have a ATI rage 128 video card you will most likely only have a 800X600 resolution, to fix this after 8.04 is installed do this:

[http://ubuntuforums.org/showthread.php?t=854648](http://ubuntuforums.org/showthread.php?t=854648)

this is a how to I wrote and It works every-time for me! (with an ATI 128 8)

you already have 9.0 cd so your up grade should be a snap !
This is the way I did It on my G3 B&W and I duel boot ubuntu and panther!
panther sees very little screen time !:D

---

