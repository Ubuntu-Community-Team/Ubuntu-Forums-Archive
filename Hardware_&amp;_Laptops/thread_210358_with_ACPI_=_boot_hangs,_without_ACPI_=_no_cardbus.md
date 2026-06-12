---
title: "with ACPI = boot hangs, without ACPI = no cardbus"
date: 2006-07-06
forum: Hardware &amp; Laptops
---

### Post by jarviw on 2006-07-06
Hi all!
I am relatively new with linux, so please bare with me...

so after messing around with several distros, and have some good general feelings about ubuntu, I installed ubuntu 6.06 on an old notebook, Sony VAIO PCG-FX120.  Then one problem comes with another...

to begin with, the boot will hang at
**ACPI: subsystem revision 12xxxxxx**

so I added **acpi=off** in the boot command, and finally I was able to get into the ubuntu live system, and I was able to install it fine.

Then it's time to get it setup for network...
I did the install at school (with pre-assigned IP and all that) and had no problem getting the notebook online and updated with ethernet.  (but I have lots of problem getting it to work at home with my DHCP mode DSL modem/router... but this is beside the point here.)


So I need to get the wireless card to work.  I have this SMC2635W pcmcia card, which I know I will have to use ndiswrapper and all that fun stuff to get it to work.  (one of the reason why I ended up installing ubuntu.)
I actually have gotten this card to work on my new Toshiba M45-S351 to work under ubuntu and ndiswrapper, so I somewhat know what to deal with it.


but then everytime I plug the pcmcia cardbus in, it tells me in **dmesg**:
**cs: pcmcia_socket0: cardbus cards are not supported**
and the lights on the card do not lit.

cardctl status only tells me "no card"...

reading from else wherelse, I tried to remove acpi=off from the booting command, and magically the light on the cardbus are on during booting, but again the boot hangs!!


Why?  What exactly am I dealing with?  
Are these PCMCIA and ACPI issues with the Kernel 2.6.xx? (I seem to read about this somewhere)
or do I need certain driver for my old hardware?  (Cardbus adapter?)

How should I fix it?
Hope someone can help me here...

---

### Post by Hellkeepa on 2006-07-06
HELLo!

Not exactly your laptop, I know, but maybe this thread might come in helpful:
[http://ubuntuforums.org/showthread.php?t=210153](http://ubuntuforums.org/showthread.php?t=210153)

As for the problems getting DHCP to work no your home LAN:
I've found it best to shot down the NIC you're not using, with "sudo ifconfig eth# down", and then running "sudo dhclient eth#" on the other. This will set up the routes, IP, gateway, resolv.conf and everything else for you.
Most likely the routing information that's not set up correctly, as of now.

Happy codin'!

---

### Post by jarviw on 2006-07-07
hi Hellkeepa,

thanks for the tip.  I will have to try the network thing later!

the link about ACPI didn't work for me however. it still hangs at the boot without ACPI=off.

is there a way to turn on ACPI once the kernel is booted?

thanks anyway!

---

### Post by jarviw on 2006-07-12
okay... so I did a little more research..

What I have found is that this is indeed an ACPI issue.
Sony VAIO PCG-FX120 is known to have a bad ACPI BIOS (bad DSDT) and is being blacklisted in the kernel (since 2.4 if I remembered it right)

[http://acpi.sourceforge.net/documentation/blacklist.html](http://acpi.sourceforge.net/documentation/blacklist.html)

new to linux, I am not exactly sure what "blacklist" mean (they give up on fixing it?), but I just cannot find a patch of anything.


Anyone has a workaround?  or should I just give up?

---

### Post by jarviw on 2006-07-13
Finally got it to work...

I realized that I still have the original version of BIOS (I thought for sure I upgraded it already).

So I got the new version from Sony website, and now the ACPI works, and cardbus is detected automatically.

Hope this will help others who might have similar problem.

---

### Post by gerryg on 2007-12-29
> **jarviw said:**
> Hope this will help others who might have similar problem.

Indeed it did, thx!

The warning about problems with the BIOS update might also be of interest:
"ALL RAM installed in slot #2 (toward front of the system) should be removed prior to flashing the BIOS."
[http://www.wimsbios.com/phpBB2/topic4952.html](http://www.wimsbios.com/phpBB2/topic4952.html)

Cheers,
Gerry

---

