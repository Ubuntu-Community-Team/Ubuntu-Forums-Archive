---
title: "How to install new hardware?"
date: 2007-05-11
forum: Hardware &amp; Laptops
---

### Post by myxiplx on 2007-05-11
Can anyone tell me how to install new hardware in Ubuntu 7.0.4?

I've got a PCMCIA wireless card, and a 3com USB wireless adaptor.  Neither are detected by Ubuntu if I plug them in, and I can't find any way to detect new hardware or install drivers.

Ubuntu seems to detect everything fine during the initial installation, how do I get it to detect new hardware and install drivers now it's running?

Ross

---

### Post by rich.bradshaw on 2007-05-11
If it is plugged in, it should work if Ubuntu supports it.

try lspci and lsusb to see if it can "see" them.

You will most likely need to use ndiswrapper to get them to work...

---

### Post by heiko.nolen on 2007-05-13
Hi!

Concerning the statement: "If it is plugged in, it should work if Ubuntu supports it", I have had a recent experience of a wireless card that used to work just fine but doesn't anymore. I think I had some type of crash when coming out of hibernation, and the pcmcia slot doesn't react anymore.

Do you have any green lights at all?

---

### Post by myxiplx on 2007-05-13
Nah, no lights at all.  Not too worried about it, this card was a 2nd hand one the boss' kids trod on so it's no the most reliable.

Plugged in directly for now, not really interested in getting into the depths of driver troubleshooting in linux yet, still got a lot of the basics to learn.

Will probably try a re-install with a known good card fitted to see if they're supported by default.

---

### Post by heiko.nolen on 2007-05-13
:lolflag: - Had that happen too, but I couldn't blame the boss!

- I've got a pretty obscure card myself and it's recognized by Ubuntu. As long as the card is good I wouldn't be surprised if it's recognized. On my part I have problem with the slot being deactivated or smthng...

Good luck! - This is cool stuff to get into :)

---

