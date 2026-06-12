---
title: "SATA drive in non-SATA motherboard?"
date: 2008-05-31
forum: Hardware
---

### Post by popie on 2008-05-31
I have a SATA 500gb drive I'd like to install in an older machine, with an Epox 8KHA motherboard, which doesn't have a SATA interface.

What's the best way to do this? Sata card? IDE adapter if some sort? External enclosure?

My goal is to access this drive via SAMBA for backups. Thanks.

---

### Post by damis648 on 2008-05-31
I think a PCI card from newegg would be the best idea.

---

### Post by acron1 on 2008-05-31
> **damis648 said:**
> I think a PCI card from newegg would be the best idea.
That will be your best option and not too expensive either.

---

### Post by molotov00 on 2008-05-31
I read that the connectors are terribly slow. If you look them up and then read the revies you'll find the same thing. I'd bypass that step and just use the card.

---

### Post by amites on 2008-06-03
the only trick with the PCI cards is that Ubuntu will not natively support them,

I have an Initio PCI SATA adapter and have that it on my tinkering list with my Dual Monitor since I got installed on my main CPU (about a week now)

though with time all these things get easier as everyone figures them out and shares how,

just thought I'd throw in a nugget

---

### Post by popie on 2008-06-03
Hmmmm... some people say certain cards work fine, others say they don't. I wonder if it depends on the chipset of the card.? 

I've been looking at some cards with Silicon Image 3512 chips. Anyone know if they work out of the box?

---

### Post by amites on 2008-06-06
I don't know what works out of the box right now,

it definitely depends on the chipset, some have linux driver support some don't, also there are many standards that cheaper models don't follow making them more difficult to configure

(though if I knew much about that I would be here answering questions rather than making comments)

---

### Post by finito on 2008-06-06
get a SATA enclosure and attach it by USB. and goto your BIOS and boot your usb Drive from there if the option doesn't exist upgrade your firmware.

---

### Post by bigken on 2008-06-06
> **popie said:**
> Hmmmm... some people say certain cards work fine, others say they don't. I wonder if it depends on the chipset of the card.? 

I've been looking at some cards with Silicon Image 3512 chips. Anyone know if they work out of the box?


I have one these and it works ok for me

---

### Post by maxino on 2008-08-06
Sorry to jump in late...

I am currently having problems with a Trust PCI eSata controller card. The chipset from Initio is apparently not supported well and my external eSata hd does not work.
Cheers,

---

### Post by evets25 on 2008-08-06
> **finito said:**
> get a SATA enclosure and attach it by USB. and goto your BIOS and boot your usb Drive from there if the option doesn't exist upgrade your firmware.

Getting a usb hard drive enclosure is a good option, and should work with Linux fairly reliably, however this might not be an option if the drive is going to be the main drive that the OS resides on. In that case, it needs to be internal, connected to to a PCI sata card. If however, this is just an additional drive for storage space, then I would go with an external hard drive enclosure and use it as an external hard drive.

---

