---
title: "anyone tried Toshiba P100 laptop with Gutsy?"
date: 2007-10-19
forum: Hardware &amp; Laptops
---

### Post by rax_m on 2007-10-19
Hi all, 

I was wondering if anyones tried Gutsy on their Toshiba P100 series laptop?

If so did you have any issues?

I'm still running feisty and hope the following is sorted:

- Sound working by default
- GPU fan working
- Suspend / Hibernate working properly

Thanks
Rax

---

### Post by arkara on 2007-10-19
sound does not work properly and this is very disappointing

---

### Post by rax_m on 2007-10-20
oh well.... 

Does the GPU fan work?

thanks for the reply!

---

### Post by rax_m on 2007-10-21
bump

---

### Post by Ryanson on 2007-10-21
Fans appear to work fine. I've not tested the suspend/hibernate yet.

Sound is still the main issue though. And no fixes that helped in fiesty work in gutsy.

---

### Post by rax_m on 2007-10-22
ooooohh.. thats bad. But I guess no sounds is better than overheating :) 

Have you tried the ACPI / DSDT fix as well ?

---

### Post by sw_ on 2007-10-22
i tryed just about every howto and tutorial and fix that is available  and everything i get is some faint sound im my headphones

---

### Post by givver on 2007-10-24
I am using a Toshiba P100 and I have managed to get the sound to work as well as the fans (no overheating)  Hibernate and Suspend does not work.  (I am using UbuntuStudio 7.1 Gutsy)

To get the fans to work correctly and not intermittently I had to add **acpi=off** to my kernel line in the Grub menu.lst
ie.
kernel		/boot/vmlinuz-2.6.22-14-rt root=UUID=f6f9f438-1eb3-4ccd-949a-458546c72e4d ro quiet splash acpi=off

To get my sound to work I followed the instructions from the link bellow. The instructions on that we page don't say it but you also need to add  the acpi=off (see above) or it will not work. 

[http://www.linuxforums.org/forum/peripherals-hardware/96259-toshiba-p100-series-sound-fix-ubuntu.html](http://www.linuxforums.org/forum/peripherals-hardware/96259-toshiba-p100-series-sound-fix-ubuntu.html)

I hope this helps.

---

### Post by rax_m on 2007-10-25
I've installed the DSDT fix in feisty and it gives me sound... BUT my Nvidia card fan does not work (which is ok when I'm not playing games.. but it still makes the laptop hot). 

If I try adding the acpi=off parameter then xorg will not start ...

---

### Post by daimaru on 2007-10-27
> **rax_m said:**
> I've installed the DSDT fix in feisty and it gives me sound... BUT my Nvidia card fan does not work (which is ok when I'm not playing games.. but it still makes the laptop hot). 

If I try adding the acpi=off parameter then xorg will not start ...

i have a toshiba p100-239
sound worked out of the box with Conexant Analog , not with conexant digital.
concerning the FAN PROBLEM:

fan does seem to kick in sometimes, but im just now watching my gpu temp climping to 75 and ambient is at 62...still climbing , with acpi=off gpu and ambient stay below 30 which would be nice but turning off acpi really isnt an option when your running your laptop on batteries. 

nvidia-settings tells me that the slowdown threshold is set to 115 degrees, but its greyed out and i cant change it.

does anyone know how to manually activate the gpu fans ? stupid phoenix bios laptop cant use the toshiba utilities and i havn't found any solution to this prob yet 

PLZ help. Temp now at 90 degrees turning off my crappy toshiba ... never buying toshiba again

---

### Post by rax_m on 2007-10-30
Well good news for the GPU fan issue !! 
I found a link from a launchpad bug to a French website and it had an additional fix for the DSDT.. when you make this change and recompile the file GPU fan works!! :) 

Here's the link: [http://ql.homelinux.net/wiki/doku.php?id=ubuntu-7.04:dsdt#le_ventilateur_de_la_gc_nvidia](http://ql.homelinux.net/wiki/doku.php?id=ubuntu-7.04:dsdt#le_ventilateur_de_la_gc_nvidia)

You can translate with google, but it messes up the syntax of the code, so copy the code from the original french site. 

And here's the link to the bugs under Gutsy  ( I am using Feisty). 

Ask me if you have any questions.. 

Cheers
Rax

---

### Post by daimaru on 2007-11-02
hi thank you for your message i hope i can get this to work. but does it only work for feisty? 

> **rax_m said:**
> 
And here's the link to the bugs under Gutsy  ( I am using Feisty). 
Rax

theres no link could you post the gutsy link. i tried the stuff on the french site under the "Le ventilateur de la GC Navidia" not the stuff above with the sound since my sound works fine in gutsy. but when i recompile dsdt i get 18 error messages and i don't get a dsdt.aml file only a dsdt.hex file :confused: . sry don't really know that much about the dsdt stuff. any suggestions what i'm doing wrong . 

thx for the help

---

### Post by daimaru on 2007-11-02
here is what i get when in run command:

```
gg@gg:~$ iasl -tc dsdt.dsl

Intel ACPI Component Architecture
ASL Optimizing Compiler version 20061109 [May 16 2007]
Copyright (C) 2000 - 2006 Intel Corporation
Supports ACPI Specification Revision 3.0a

dsdt.dsl  1870:                                 Name (_T_0, 0x00)
Error    4081 -                     Use of reserved word ^  (_T_0)

dsdt.dsl  1948:                                 Name (_T_0, 0x00)
Error    4081 -                     Use of reserved word ^  (_T_0)

dsdt.dsl  2146:                             Name (_T_0, 0x00)
Error    4081 -                 Use of reserved word ^  (_T_0)

dsdt.dsl  2158:                                         Name (_T_1, 0x00)
Error    4081 -                             Use of reserved word ^  (_T_1)

dsdt.dsl  2192:                                             Name (_T_2, 0x00)
Error    4081 -                                 Use of reserved word ^  (_T_2)

dsdt.dsl  2226:                                                 Name (_T_3, 0x00)
Error    4081 -                                     Use of reserved word ^  (_T_3)

dsdt.dsl  2274:                                                     Name (_T_4, 0x00)
Error    4081 -                                         Use of reserved word ^  (_T_4)

dsdt.dsl  2308:                                                         Name (_T_5, 0x00)
Error    4081 -                                             Use of reserved word ^  (_T_5)

dsdt.dsl  2356:                                                             Name (_T_6, 0x00)
Error    4081 -                                                 Use of reserved word ^  (_T_6)

dsdt.dsl  2404:                                                                 Name (_T_7, 0x00)
Error    4081 -                                                     Use of reserved word ^  (_T_7)

dsdt.dsl  2809:                             Name (_T_0, 0x00)
Error    4081 -                 Use of reserved word ^  (_T_0)

dsdt.dsl  2887:                             Name (_T_0, 0x00)
Error    4081 -                 Use of reserved word ^  (_T_0)

dsdt.dsl  5210:                             Name (_T_0, 0x00)
Error    4081 -                 Use of reserved word ^  (_T_0)

dsdt.dsl  7281:             Method (BTST, 0, NotSerialized)
Warning  1086 -                        ^ Not all control paths return a value (BTST)

dsdt.dsl  7329:             Method (EVNT, 1, NotSerialized)
Warning  1086 -                        ^ Not all control paths return a value (EVNT)

dsdt.dsl  7656:                     Name (_T_0, 0x00)
Error    4081 -         Use of reserved word ^  (_T_0)

dsdt.dsl  7937:             Name (_HID, "*PNP0C14")
Error    4001 -                                  ^ String must be entirely alphanumeric (*PNP0C14)

dsdt.dsl  8088:                 Name (_HID, "*PNP0C14")
Error    4001 - String must be entirely alphanumeric ^  (*PNP0C14)

dsdt.dsl  8147:                         Name (_T_0, 0x00)
Error    4081 -             Use of reserved word ^  (_T_0)

dsdt.dsl  8241:                         Name (_T_0, 0x00)
Error    4081 -             Use of reserved word ^  (_T_0)

ASL Input:  dsdt.dsl - 8739 lines, 324560 bytes, 3504 keywords
Compilation complete. 18 Errors, 2 Warnings, 0 Remarks, 1240 Optimizations
gg@gg:~$ 

```

EDIT: ok after really reading what it says on the french page (the guy has the exact same errors as me :) ) i did everything he said changing the _T_0 stuff to T_0 etc, but now i get 183 errors when trying to compile ... damn

---

### Post by rax_m on 2007-11-07
> **rax_m said:**
> Well good news for the GPU fan issue !! 
I found a link from a launchpad bug to a French website and it had an additional fix for the DSDT.. when you make this change and recompile the file GPU fan works!! :) 

Here's the link: [http://ql.homelinux.net/wiki/doku.php?id=ubuntu-7.04:dsdt#le_ventilateur_de_la_gc_nvidia](http://ql.homelinux.net/wiki/doku.php?id=ubuntu-7.04:dsdt#le_ventilateur_de_la_gc_nvidia)

You can translate with google, but it messes up the syntax of the code, so copy the code from the original french site. 

And here's the link to the bugs under Gutsy  ( I am using Feisty). 

Ask me if you have any questions.. 

Cheers
Rax

Sorry.. just read that I forgot to post the launchpad link:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/136469](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/136469)

---

### Post by rax_m on 2007-11-14
For anyone interested, I installed OpenSuse 10.3 on an ext harddisk on my Tosh P100-429 laptop. The sound and the GPU fan worked out of the box. The only thing that still seems problematic is the suspend/hibernate. 

I may have to do a full migration to OpenSuse at some point, but at the moment there's no rush. 

I just don't like the RPM package management as much as the Debs.

---

### Post by gene6482 on 2007-11-14
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/136469](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/136469) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				if you check the bug report, there is a custom ubuntu kernel that will make the sound work.  Just download and install.

---

### Post by rax_m on 2007-11-15
Do you still need to apply the custom DSDT file with this new kernel?

---

### Post by gene6482 on 2007-11-15
you don't need to, but it doesn't hurt to do it either.  I have the integrated graphics, but some people have nvidia cards in which case the dsdt fixes make the gpu fan work.

---

### Post by daimaru on 2007-11-17
@ rax_m
hi again. i just applied the custom kernel (launchpad link above) and i also recompiled the dsdt.
so far i can say that gpu fan and sound work. gpu @ 40 °C and sound works, but i'm not quite sure if this is really a fix, because it seems like now my fan is running continously just as it did when booting with acpi=off. I will check that again (laptop is turned off right now).

the only advantage so far as opposed to acpi=off is the fact that the battery applet works this way (cause it uses /proc/acpi which does not exist if booting with acpi=off) 

well I'm still happy that at least i have a temp fix for this until the new kernel .24 comes out which i hope will have this fixed since most ppl on lauchpad said that they contacted the kernel guys. 

but still i guess you should stick with 7.04 for now.
greetz

---

### Post by daimaru on 2007-11-20
correction :

gutsy now runs perfectly on my toshiba p100 gpu fan working everything working :p:guitar:

---

### Post by daimaru on 2007-11-20
quick summary [COLOR="DarkRed"]by loliverouge[/COLOR] on launchpad thread see link, for everyone who doesn't want to spend minutes searching for the answer thats hidden in there :)
heres the original thread: [link]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/136469")


- step 1 : download [http://fragglenet.com/tools/toshiba_dsdt_kernel_fix.2.6.22-14_2007111300.tar.gz](http://fragglenet.com/tools/toshiba_dsdt_kernel_fix.2.6.22-14_2007111300.tar.gz)
- step 2 : fix dsdt for nvidia temperature ([http://ql.homelinux.net/wiki/doku.php?id=ubuntu-7.04:dsdt#le_ventilateur_de_la_gc_nvidia](http://ql.homelinux.net/wiki/doku.php?id=ubuntu-7.04:dsdt#le_ventilateur_de_la_gc_nvidia))
- step 3 : open Terminal and enter this commands :
   * tar xvf toshiba_dsdt_kernel_fix.2.6.22-14_2007111300.tar.gz
   * cd toshiba_dsdt_kernel_fix.2.6.22-14_2007111300/
   * dpkg -i *.deb
- step 4 : reboot

---

### Post by rax_m on 2007-11-23
Cheers damiaru... do you know if this will be included as a fix in the Gutsy at some point, or will we have to wait for hardy before all this dilemma is no longer needed ?

---

### Post by daimaru on 2007-11-23
from what i picked up its a kernel problem (with alsa) 2.6.20 did not have the problem 2.6.22 and 23 do have it. so maybe they will have fixed it in the 2.6.24 kernel. i sure hope so.

---

### Post by rax_m on 2007-11-26
Hi daimaru.. 
I couldn't resist the urge and just installed Gutsy! :) 
Regarding the DSDT fix.. do we just apply it as normal .. then does the dpkg -i *.deb automatically install the kernel? Would the dsdt not be then applied to the old kernel? Or am i missing something. 

Thanks
R

---

### Post by rax_m on 2007-11-27
I just wanted to say thanks to everyone for this patch.. it works like a charm!

---

### Post by katsa on 2007-11-27
I would like to thank everybody for this wonderful solution! I was almost giving up on Ubuntu because of this freaky no sound thing! The fix works perfectly on my Toshiba P100, with the "Waikiki" codename nightmare.

---

### Post by rzrgenesys187 on 2007-11-27
Awesome.  I knew a sound fix would happen sooner or later.  Gutsy is definitely awesome in my book.  I just wish toshiba would do something so we don't have to deal with this issue every time a new upgrade is released or we want to try a new distro.

---

### Post by daimaru on 2007-11-28
> **rax_m said:**
> Hi daimaru.. 
I couldn't resist the urge and just installed Gutsy! :) 
Regarding the DSDT fix.. do we just apply it as normal .. then does the dpkg -i *.deb automatically install the kernel? Would the dsdt not be then applied to the old kernel? Or am i missing something. 

Thanks
R

hi rax_m sorry for the late reply, I guess you already solved it. But its nice to hear you switched to gutsy. works like a charm doesn't it :mrgreen:

---

### Post by K0smiC on 2007-12-02
Hi to everybody, I am an Italian consumer of ubuntu-it.org! I immediately explain you the problem that we have us with the toshiba p100-273 with ubuntu gutsy: no audio!! If start with noapic acpi=off have problems with the video card and the relative fan..the audio works...:guitar: I wait for your news thanks!

---

### Post by lukweb on 2007-12-05
Thx Daimaru, i've got a Toshiba P100-473 (PSPAGE Model) with Ubuntu 7.10 and your solution was the good one.
Thx for all buddy ! :KS:KS:KS

---

### Post by daimaru on 2007-12-06
@lukweb
happy to see that you toshiba is working too, but credit still goes to gene6482 and rax_m who pointed me in the right direction, as well as the people on the launchpad thread who figued it out. i only recounted the steps that i found in those many threads so people would not have to search forever like i did.
thx again rax_m and gene6482

---

### Post by daimaru on 2008-04-27
Hi all,
I opened a new thread with a howto for hardy heron, because you don't need to patch the kernel anymore. hope it helps.

[new thread loaction]("http://ubuntuforums.org/showthread.php?t=771223")

---

