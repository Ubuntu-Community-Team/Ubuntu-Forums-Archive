---
title: "Memory Card Reader detected, but doesn't read cards."
date: 2008-03-11
forum: Hardware &amp; Laptops
---

### Post by Kivech on 2008-03-11
Ok, I have an odd problem here.

I have a Floppy/Card Reader combo unit, of which the floppy drive is connected through IDE and the card readers through USB directly on the motherboard.
Needless to say lspci will not list it, it just lists the USB ports, not the stuff hooked up to it.

If I do a dmesg after I plugged in a memory card  from my photo camera I get a whole bunch of errors which mainly refer to Linux not being able to read it.
If I check the Hardware Information tool in the menu of Ubuntu, it lists both card ports fine. The problem is though, it doesn't read any cards.

The unit is brandless, so I have no clue who the manufacturer is, and considering it is directly connected to USB, I would say can be considered a general USB device. I found out that it allocated /dev/sdc and /dev/sdd for both devices. So I recon that part is set.

Now all I need to figure out is how to get them to read cards (worked under windows, so the hardware is good).

Any suggestions are highly appreciated.

Kivech

---

### Post by teaker1s on 2008-03-12
dump a card in it and then
```
lsusb
```to se if you can see vendor and product id 


```
fdisk -l
``` see if you can see it's partition

---

### Post by Kivech on 2008-03-13
Thanks for the tip. I'll give that a try later on.

Meanwhile I tried another type of card and that one does seem to be read. So oddly enough it doesn't manage to read the SD card type (the smaller memory cards used in cameras). Since this is a newer type, I'm also thinking it could be that there is some driver or codec missing.

But I'll try your suggestion for sure and will see what output I get from this.

Thanks,

Kivech

---

### Post by Sef on 2008-03-13
> Meanwhile I tried another type of card and that one does seem to be read. So oddly enough it doesn't manage to read the SD card type (the smaller memory cards used in cameras). Since this is a newer type, I'm also thinking it could be that there is some driver or codec missing.

I had a similar problem with the card reader on my printer.  It would read Compact Flash, but not sd cards.  However, once I got a newer driver the problem cleared up, so I think you're correct about your problem.  Check their website for newer drivers.

---

