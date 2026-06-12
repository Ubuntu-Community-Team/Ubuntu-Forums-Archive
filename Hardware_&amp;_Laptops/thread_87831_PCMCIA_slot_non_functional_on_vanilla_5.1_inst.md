---
title: "PCMCIA slot non functional on vanilla 5.1 inst"
date: 2005-11-08
forum: Hardware &amp; Laptops
---

### Post by Dirkson on 2005-11-08
I finally decided to make the jump from that other OS to Linux on my laptop computer. I downloaded the 64 bit version of Ubuntu for my Athelon 64 cpu. The install of Ubuntu went smoothly, even automatically installing my wireless mouse, which impressed me quite a bit. 

   Unfortunately, no matter what I do, I cannot get it to recognize my PCMCIA modem. From research I've done, I've figured out that the modem should be telling Linux that it's two usb devices (ttyUSB0 and ttyUSB1) but it does not do that. Looking in the device manager, nothing happens when I insert/remove the card, and various combinations of insertion/removal before and after boot do not seem to do much. Most of my usb ports seem to be controlled by an Nvidia chipset, but the PCMCIA slot seems to reference several chipsets by both Nvidia and Texas Instruments, although most of the TI ones are listed as 'unknown devices' with TI as the author.

   I believe the laptop model is an R3000z; It's a compaq presaio and is about a year old.

   I'm going to try a different PCMCIA card I have, and see if that reacts any differently. Once I've rebooted into the M$ os, which can currently use the modem card, I'll post the results back here.

Any help at all would be -greatly- appreciated. I don't wanna boot M$ anymore :(

-Jeffrey Stewart

---

### Post by Dirkson on 2005-11-08
Ok, the other card shows exactly the same symptoms, so it's likely something with the pcmcia slot, not the individual card. That's good to know, I think... Any ideas?

-Jeffrey

---

### Post by Dirkson on 2005-11-09
Yet another update on this this. After much research, it looks like the cardbus controller is the issue. My laptop uses the Texas Instruments PCI 1620 CardBus, which has some issues. I've posted in a forum for my specific laptop, but I'm not sure that anyone has any fixes for this sort of thing >.< I'm afraid I might have to recompile me kernel, which is a scary thing for as n00bish a linux user as I. Anyway, if anyone here knows anything I could try to make it work, I'd be greatly appreciative.

Thanks

-Jeffrey

---

