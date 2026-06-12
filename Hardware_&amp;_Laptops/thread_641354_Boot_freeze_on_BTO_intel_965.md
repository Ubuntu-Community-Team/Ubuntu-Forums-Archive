---
title: "Boot freeze on BTO intel 965"
date: 2007-12-15
forum: Hardware &amp; Laptops
---

### Post by DrCore on 2007-12-15
I'm trying to install Ubuntu on a BTO notebook type 15v125+ ([http://www.btonotebooks.nl/html/detail.asp?PartnerID=31&DisplayPartnerID=34&ProductID=247]("http://www.btonotebooks.nl/html/detail.asp?PartnerID=31&DisplayPartnerID=34&ProductID=247")). Although the brand is Dutch, the hardware is a Vestel motherboard with the Intel 965/ICH8 chipset.

I have tried to boot several Linux live CD's with several boot parameters without success. Ubuntu 7.04 Desktop, Ubuntu 7.10 Desktop and even Ubuntu 8.04 alpha (32-bit and alternate) and OpenSuse 10.3 all got stuck after/during CPU detection.

With Ubuntu 8.04 I started experimenting with boot parameters:
- acpi=off: IRQproblems with USB en SATA, still got stuck at language selection
- noapic: freeze at checking TSC synchronisation [CPU#0 -> CPU#1]
- acpi_osi=!linux noacpi: freeze at PCI: Transparant bridge 0000:00:1e.0
- generic.all_generic_ide=1: freeze at ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
- generic.all_generic_ide irqprobe: freeze at Booting processor 1/1 eip 3000

One other peculiar effect is the very slow build up of the graphical boot selection menu of the live CD. It takes about 5 seconds before all elements have been build up on the screen.

Unfortunately I have no lspci or other dumps as I can not boot. To make sure sure I have no hardware problems, I installed Vista including all drivers without issues.

I there a boot parameter I missed or does someone have any other insight how I can have Ubuntu installed?

---

### Post by leonidas666 on 2007-12-15
You could try installing with the alternate install cd. 
My Laptop also cannot boot with the CD, but the installed Ubuntu works fine.

---

### Post by DrCore on 2007-12-15
Alternate CD also get's stuck. This time after 'Brought up 2 CPUs'.

I also tried the boot options 'lolapic noapic' without luck.

---

### Post by leonidas666 on 2007-12-16
Have you tried fiddling with the options in the bios? Try disabling as many devices as possible, or you could try "load bios defaults" (bios defaults is the fail-safe configuration, setup-defaults is for better performance - if you have such settings in your bios).
Since you already know the brand of the motherboard, have you searched the internet whether somebody else got linux to work on a similar machine? 
Maybe you could also try contacting the dutch manufacturer (yeah,  i know, probably futile...).

---

### Post by DrCore on 2007-12-16
Indeed, the solution was to be found in the BIOS. By default USB Legacy support is on, and this turned out to be the culprit.

After switching it off, the system boots, all devices get recognized and I'm presented with a nice Ubuntu 7.10 desktop.

Thanks.

---

### Post by fxsauvage on 2008-05-21
Hi, and thanks a lot for this post.
I ran in same issue and learned these few things:

1. with 'VESTEL' motherboard 'ARES' bios, I was unable to boot linux from live CD, or any other device.
'VESTEL' is just a reseller, could not find any bios documentation/update

2. setting 'apci=off noapic' when editing boot command line, Linux started.
However, dual-core was not supported, only one [core] processor activated.
$ grep -i core /proc/cpuinfo
model name	: Intel(R) Core(TM)2 Duo CPU     T7500  @ 2.20GHz
core id		: 0
cpu cores	: 1

3. Found out thanks to this post that bios USB Legacy support was activated: just disabled it.
--> when restarting/turning on computer, press 'F2' before your bios splashcreen pops up. It opens the bios edit panel, go to advanced > USB, check if legacy enabled. If yes, just disable, save and restart.

Hopefully, Linux generic kernel boots with ACPI support, dual core 2 processors correctly activated, and start the ball rolling !

fxs

---

