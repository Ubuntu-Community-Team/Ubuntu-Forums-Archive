---
title: "Please recommend a motherboard..."
date: 2004-11-03
forum: Hardware &amp; Laptops
---

### Post by haocheng on 2004-11-03
I cannot install Ubuntu on my ASUS P4S800D... 
I want to install Ubuntu on a Seagate SATA HD, 
but the installation always hangs when it tries to load sd_mod module.

If that's really the problem of SIS 655FX, I may consider buying a 
new motherboard.

Therefore, can anyone recommend a MB that I can install Ubuntu on SATA HD?
I am considering buying ASUS P4P800/P4P800 SE (Intel 865P). 
Did anyone successfully install Ubuntu on SATA HD with this MB?

Any help is appreciated and many thanks in advance!  :smile:

---

### Post by jeremy on 2004-11-03
I use a P4P800 SE, with SATA hd, everything works fine without any extra configuration needed.

---

### Post by haocheng on 2004-11-04
Thanks a lot, jeremy  ;-) 

BTW, does Ubuntu support 3COM 3C940 controller on P4P800?

Many thanks in advance~~~  :razz:

---

### Post by Darth on 2004-11-10
I'm looking at installing Ubuntu on my office PC and if all goes well rolling it out to everybody else. Could anybody recomend a M/B? I'm quite fond of MSi so if there's a MSi board that is fully supported I'd love to hear about it.

---

### Post by NRios on 2004-11-10
[QUOTE=jeremy]I use a P4P800 SE, with SATA hd, everything works fine without any extra configuration needed.[/QUOTE]
 !!!
I have a P4P800 DE with a Seagate SATA and have been unable to install anything but Mandrake 10, which itself seems to be dealing with 100.000 interrupts per second from I-don't-know-where, which make it rather slow, (though still usable!)

Ubuntu has these problems:

* It tries to write the boot block to an unexisting /dev/hda instead of /dev/sda
* If I try to skip Grub and install Lilo, installation crashes also
* If I try to skip Grub and Lilo altogether (to fix that later with Knoppix), installation proceeds a bit farther, then hangs when it seems to be about to reset the system and restart
* If I reset and restart manually, I get a big kernel panic.

This is all very funny (as in weird), as the _live_ Ubuntu boots just fine, and shows the SATA drives OK.

Strange that your mobo works ... maybe the difference is in the  SE/DE, and it is the (unused and disabled) RAID controller that is giving me hell.

Any suggestions beside axing down the SATA drive, the motherboard and setting it all on fire?

Regards,
Nacho.

---

### Post by wallijonn on 2004-11-10
I usually want as close to 100% Intel chipsets as possible - which means Intel, some ECS andMatsonic. For NIC it's 3Com or Intel. For sound cards it's Creative. 

nVidia chipsets is a big question mark for me - do nVidia chipsets have problems with Linux?

I don't do VIA, Promise, HighPoint, SIIG.

---

### Post by fng on 2004-11-11
Im a big fan of the soltek ([http://www.soltek.de](http://www.soltek.de)) series. 

There are pretty cheap , but always end up top-3 in tom's hardware tests.
Its also an overclocker's dream, with their built-in anti-burn shield.  You can't fry your cpu with it :)

---

### Post by haocheng on 2004-11-16
Hi guys~~~

I got a ASUS P4P800 SE and I installed Ubuntu on 
my new Seagate SATA HD successfully  :) 

So I guess if you want to install Ubuntu on SATA HD, 
try not to use MB of Sis 655FX  :-( 

Although the installation went without any problem, 
I cannot start X after the installation. 
It showed "No Screens Found"....

I typed 
```
sudo xf86config 
``` to do a setup and it works now~~~
(BTW, I use TNT2...)

Thanks for everyone who offered me advice :o

---

### Post by zenwhen on 2004-11-17
I am running a 3.0C and 1GB of PC3200 in an Abit IS7, which is based on an Intel i865 chipset.

To say that Ubuntu's install, setup, and performance has been smooth sailing would be an understatement. I think you would be very happy as well. If you have any questions, I will be happy to answer them.

While I am not currently running a SATA hard drive on my system, Ubuntu does see the controller. I am sure you will have no issues with Intel's SATA controller.

---

### Post by HiddenWolf on 2004-11-17
Intel's support should be good, you can be assured of that.

---

