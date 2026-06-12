---
title: "Which Kernel image? 386 or 686?"
date: 2005-12-11
forum: Installation &amp; Upgrades
---

### Post by Ruskie on 2005-12-11
Hello everybody,

Browsing through my package list this morning I noticed there are available for download two different kernel images (among others):

[LIST]
[*]linux-image-2.6.12-10-386
[*]linux-image-2.6.12-10-686
[/LIST]

The latter namely for "PPro/Celeron/PII/PIII/PIV".
Which one is the most "optimized", the "faster", or to be clear the most suitable for a modern machine?

By the way, I have an AMD64 (though an i386 32 bit installation of linux), I'm not sure wheter the -686 image is for PENTIUM only or it simply means "advanced assembler instruction"...

Thank you for help in advance. ;)
Marco

---

### Post by dcstar on 2005-12-11
[QUOTE=Ruskie]Hello everybody,

Browsing through my package list this morning I noticed there are available for download two different kernel images (among others):
.......
By the way, I have an AMD64 (though an i386 32 bit installation of linux), I'm not sure wheter the -686 image is for PENTIUM only or it simply means "advanced assembler instruction"...

Thank you for help in advance. ;)
Marco[/QUOTE]
Try the K7 image, it is optimised for AMD processors (but the AMD64 version of Ubuntu would be even better.........)

---

### Post by Ruskie on 2005-12-11
Thanks.
I tried. From your answers I get, however, that i686 images are optimized for the Pentium Family, that is use specific instruction of Pentium, and K7 does the same for AMD.

Curiously enough, I tried the K7 image with no success on my Athlon Xp 64. While I know for having tried that the 64 bit versions of Ubuntu AND Kubuntu install and run smoothly, this K7 image hung up at boot.
No Kernel Panic, it simply started hang after the kubuntu splash, in text mode, when "checking battery state": it run forever at that time...

And you know what? It probably crashed my XP installation, almost. Infact, I suspect it was it that set system clock to 2099 (it was working in Linux prior the reboot), causing XP's famous blue screen of death...

---

### Post by jetpeach on 2005-12-11
How much of a speed different might someone see from switching to K7 instead of i386?  Is it actually worth the time?  Obviously, I guess it would depend on system to system, but I'm just wondering if somebody has a general idea of what the optimized kernel helps with.

Also, do people know if feature releases of Ubuntu will contain optimized kernel versions for K7, 686 etc?  It seems it would be realize nice if this was done by default.

EDIT: it seems this thread is quite useful with info about Kernel stuff:
[http://ubuntuforums.org/showthread.php?t=85917&highlight=i686]("http://ubuntuforums.org/showthread.php?t=85917&highlight=i686")

---

### Post by Ruskie on 2005-12-11
[QUOTE=jetpeach]How much of a speed different might someone see from switching to K7 instead of i386?  Is it actually worth the time?  Obviously, I guess it would depend on system to system, but I'm just wondering if somebody has a general idea of what the optimized kernel helps with.
[/QUOTE]

Well, as dcstar told, it is less than having AMD64 compiled kernel and all... If so, it is not really much.
I've had for a while 64bit Ubuntu with which I made just everyday typical use: some simple game, browsing, installing/uninstalling packages, editing some files etc. etc.
The difference in speed was barely noticeable, and I'm generous: I didn't experience any, but some might yet be. If K7 image is less performing than AMD64 kernel, I doubt you would notice it, unless you do developing or "high resource demanding" activities...

Marco

---

