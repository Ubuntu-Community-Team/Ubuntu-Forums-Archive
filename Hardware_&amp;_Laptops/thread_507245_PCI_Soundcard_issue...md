---
title: "PCI Soundcard issue.."
date: 2007-07-22
forum: Hardware &amp; Laptops
---

### Post by 3saul on 2007-07-22
I've recently purchased a gigabyte motherboard (and Core 2 Duo) to replace my aging AMD based system. The motherboard I purchased was a GA-P35-S3. Everything is working perfectly, except, I have an old PCI soundcard (Echo Audio Darla 20) which is no longer 'seen' by the BIOS. I know this isn't specific to Ubuntu, but I thought I would ask. Normally I would just get a new sound card, however this is a $750 soundcard and I see no reason it shouldn't work.

I've tried giving it a manual IRQ but that hasn't helped.

Any idea's?

---

### Post by fredj on 2007-07-22
The Darla20 is supported by Alsa but of course you need to get the bios to see it first. Since it is an old
card maybe you need to look for items in the bios that enable you to specify the level of PCI support
and change to an earlier version. This might make all your PCI cards slower than they would otherwise
be.  For example you may have to increase the PCI latency timer.
By the way the Bios will only configure your soundcard if the Plug and Play O/S is set to No. Otherwise
it will leave it up to Ubuntu.
It's also possible that an older card won't share an interrupt so you should try to put it in a PCI slot where it isn't
required to share an interrupt.

---

### Post by 3saul on 2007-07-22
Thanks a lot for your response. In my BIOS I only have these PCI options:
There's no option to set PnP/Non PnP

PCI1 IRQ Assignment
Auto BIOS auto-assigns IRQ to the first PCI slot. (Default)
3,4,5,7,9,10,11,12,14,15 Assigns IRQ 3,4,5,7,9,10,11,12,14,15 to the first PCI slot.
PCI2 IRQ Assignment
Auto BIOS auto-assigns IRQ to the second PCI slot. (Default)
3,4,5,7,9,10,11,12,14,15 Assigns IRQ 3,4,5,7,9,10,11,12,14,15 to the second PCI slot.
PCI3 IRQ Assignment
Auto BIOS auto-assigns IRQ to the third PCI slot. (Default)
3,4,5,7,9,10,11,12,14,15 Assigns IRQ 3,4,5,7,9,10,11,12,14,15 to the third PCI slot.

---

### Post by geraldm on 2007-07-23
Look at file /proc/interrupts after booting.  It shows the interrupts assigned.

To view how the system sees the card, use the command
lspci

Also for the Echo card, try the alsa-project.org site, enter the Echo for the soundcard, and follow
as much of the instructions for the darla card as you can.

Gerald

---

