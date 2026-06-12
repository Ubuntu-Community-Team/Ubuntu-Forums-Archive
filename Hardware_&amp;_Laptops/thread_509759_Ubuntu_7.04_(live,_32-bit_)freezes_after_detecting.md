---
title: "Ubuntu 7.04 (live, 32-bit )freezes after detecting CPU"
date: 2007-07-25
forum: Hardware &amp; Laptops
---

### Post by TehDooMCat on 2007-07-25
I have a dying laptop which I've inherited from my dad. It's a bit unstable on Windows, so I hoped it would run Ubuntu slightly better, since Linux just seems to run on broken hardware :D

Sadly, this doesn't seem to be the case. I popped in the LiveCD and it shows me the boot selection screen fine, but as soon as it loads the kernel, nothing happens. I turned off quiet mode and added noapic & nolapic to the boot options, and it seems to halt after detecting the CPU ([167.413285] CPU0: Intel(R) Pentium(R) 4 CPU 2.66GHz Stepping 07). The cursor's still flashing, but it doesn't do anything - the CD drive spins down and the laptop just sits there. :confused:

The laptop's specs are:
2.66GHz Pentium D
512mb RAM
Gf5200 Go
5-in-1 card reader
PCMCIA slot
Builtin sound (can't remember what make).

Windows boots fine and runs games well (sometimes), so I know the hardware isn't completely dead yet (although it does weird things and you have to be really careful when moving it or the screen'll go corrupted or it'll completely freeze or something).

What could be making it stop here?

EDIT: I think it might be acpi... I tried acpi=off and it got a little further, I think it might be booting... I'm bound to hit more problems knowing this laptop though :P

---

### Post by animeboi252 on 2007-07-25
this is from the live cd then did you try another distro saybayon or fedora slack

---

### Post by TehDooMCat on 2007-07-26
Nevermind, I resolved the problem, I had to turn acpi off at boot. Now I have Ubuntu installed perfectly :D

One thing that's bugging me though, is that now that ACPI is off, it can no longer detect whether it's plugged in or running from battery, and so battery life suffers as it's always running full throttle. Is there a way I can get 'round this?

Also, my PCMCIA wifi card is being weird... it can detect networks and shows their signal strength, but it can't connect to them. Any idea why this is? The card is some generic PCMCIA 802.11g card, not sure who the manufacturer is.

Also; I found the device manager but I can't find anything to do with PCMCIA devices/controllers. I know the one in my laptop works 'cause the card's LEDs light up like they should. Where are they in device manager? :confused:

---

