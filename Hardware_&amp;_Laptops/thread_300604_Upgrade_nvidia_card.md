---
title: "Upgrade nvidia card"
date: 2006-11-15
forum: Hardware &amp; Laptops
---

### Post by PurplePenguin on 2006-11-15
Here's the deal: I've got two computers with the nvidia driver on a network.  One is running with an nvidia nforce onboard shared graphics chip.  The other has an nvidia MX4000 card in it.

I want to install an nvidia 6200 card in the computer with the MX4000, and move the MX4000 into the first one that's currently using the onboard graphics chipset.

So basically, they're both running with the nvidia driver right now.  What should I do in order to upgrade both of these machines with these new cards?  Will the driver automatically make use of the suddenly larger amount of graphics memory, or do I need to do something else in order to properly upgrade them?

Hopefully I'm making sense here. :)  Thanks for any info!

---

### Post by po0f on 2006-11-15
PurplePenguin,

It should be plug-and-play, unless your box with the onboard video xorg.conf's Device section has an explicit BusID setting.  When you upgrade the box with the MX4000 in it, plug the card into the same slot.

---

### Post by PurplePenguin on 2006-11-16
> **po0f said:**
> It should be plug-and-play, unless your box with the onboard video xorg.conf's Device section has an explicit BusID setting.  

Great advice, thanks!  I checked my xorg.conf on the machine that will be upgraded from the integrated graphics to the MX4000 card, and there does seem to be a BusID setting:

```
Section "Device"
	Identifier	"NVIDIA Corporation NVCrush11 [GeForce2 MX Integrated Graphics]"
	Driver		"nvidia"
	BusID		"PCI:2:0:0"
EndSection
```

I've tried googling it to get a bit of an idea of what this means, but couldn't find anything other than people with problems posting their xorg.conf files. :)  I assume that this will need to be changed, since I'll be going from the onboard graphics chip to an AGP slot.

What's the best way of getting an updated xorg.conf, anyway?  I googled this as well, but found advice saying that it's best to just delete it and it will automatically recreate itself.  This is definitely something I'd be hesitant to do without some reassurance. :-D

---

### Post by livinginx on 2006-11-17
I have an NVidia 6200 128MB AGP card running on this box right now.  NVidia is all that I use, but it is trouble with this board.

Running an MSI uATX board, but if I try and use the NVidia drivers, I get random freezes, keyboard doesn't work, mouse clicks don't, but the mouse will still move the cursor around the screen.

So, be careful if you buy this card.

---

### Post by PurplePenguin on 2006-11-17
Does anybody know if this is a common problem with the 6200?

---

### Post by renzokuken on 2006-11-17
nah, shouldnt be, i swapped from an ATI radeon to a nVidia 6200 about 6 months ago and have never looked back.

as long as the proper nvidia driver is installed and your xorg.conf is set up properly (i beleive the nvidia driver does this for you now anyway) you shouldnt really have any major problems at all

---

