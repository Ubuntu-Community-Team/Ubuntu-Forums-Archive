---
title: "is there ubuntu drivers fromt my ati card?"
date: 2005-08-11
forum: Hardware &amp; Laptops
---

### Post by syr0kill on 2005-08-11
i have a radion 9200 pci card? when i loaded up ubuntu that i installed today it told me it cant load xserver becuase my graphics i did a lspci -v and i got subsystem:c.p. technoligies co unknown divice 2074 can anyone help me?

---

### Post by amohanty on 2005-08-11
> i have a radion 9200 pci card? when i loaded up ubuntu that i installed today it told me it cant load xserver becuase my graphics i did a lspci -v and i got subsystem:c.p. technoligies co unknown divice 2074 can anyone help me? 

It would be very helpful if you could post the entire error message...

AM

---

### Post by mjkelly on 2005-08-11
its a problem with xorg.conf
go in there and specify for your driver "ati" or "radeon" and make sure it points at the correct BudID, like mine looks like:

Section "Device"
	Identifier	"Radeon"
	Driver		"radeon"
	BusID		"PCI:1:2:0"
EndSection

Is it your first time booting into ubuntu? It might be looking for an onboard graphics chip. You gotta point it in the direction of your PCI card.

And obviously make sure your identifier matches ur monitor section.
Oh and dont even bother trying the fglrx drivers with a 9200, i have a 9250 and it cant be done.

---

### Post by syr0kill on 2005-08-12
is there even a way for me to load into xserver? is there a driver for the 9200? I was gana try to install the XFree86 drivers?? ill post the error in a few minutes.

---

