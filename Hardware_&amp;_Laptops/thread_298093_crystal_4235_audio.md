---
title: "crystal 4235 audio"
date: 2006-11-12
forum: Hardware &amp; Laptops
---

### Post by ratanjska on 2006-11-12
Hi1

I am running Ubuntu on Fujitsu Siemens ErgoPro X typ x365/300. Everything works fine (the computer is a bit slow but it is may testing-ground) except the audio.  The sound card is on board Cirrus Logic Crystal 4235 PnP. The jumper for setting the audio on/off is in position ON.

I tried the following:

ratanjska@ubuntu:~$ modinfo soundcore
filename:		/lib/modules/2.6.15-26-386/kernel/sound/soundcore.ko
description:		Core sound module
author:			Alan Cox
license	:		GPL
alias:			char-major-14-*
vermagic:		2.6.15-26-386 preempt 486 gcc-4.0
depends:
srcversion:     DD426F1CCA2CC5F060F6F92

Than, changed to the map with drivers and:

ratanjska@ubuntu:/lib/modules/2.6.15-27-386/kernel/sound/isa/cs423x$ ls
snd-cs4231.ko      snd-cs4232.ko  snd-cs4236-lib.ko
snd-cs4231-lib.ko  snd-cs4236.ko
ratanjska@ubuntu:/lib/modules/2.6.15-27-386/kernel/sound/isa/cs423x$ sudo modprobe snd-cs4236
FATAL: Error inserting snd_cs4236 (/lib/modules/2.6.15-26-386/kernel/sound/isa/cs423x/snd-cs4236.ko): No such device
ratanjska@ubuntu:/lib/modules/2.6.15-27-386/kernel/sound/isa/cs423x$

What is the problem? 

It seams that Linux can not find the hardware?

According to the documentation of the computer sound card is PNP but (according to what I find on the Net) the buss type is ISA.

Thank you in advance

Ratanjska (is a small river near my hometown)

---

