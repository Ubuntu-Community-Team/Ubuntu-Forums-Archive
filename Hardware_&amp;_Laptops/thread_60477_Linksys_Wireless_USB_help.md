---
title: "Linksys Wireless USB help"
date: 2005-08-27
forum: Hardware &amp; Laptops
---

### Post by stndrdbc on 2005-08-27
I'm new to Linux and I'm trying to get my Linksys wireless USB adapter to work. The model is the WUSB11. I've looked at other help threads but I am lost. Could someone write or copy and paste a couple of step-by-step ways to get this to work? Thank you.

---

### Post by pmjdebruijn on 2005-08-28
Hi,

Well, first things first... We need to know whether the USB is even supported by Linux. 

Please execute a 'lsusb' in the Terminal when having the Wireless USB device plugged in. Then paste the output in here.

Regards,
Pascal de Bruijn

---

### Post by stndrdbc on 2005-08-29
[QUOTE=pmjdebruijn]Hi,

Well, first things first... We need to know whether the USB is even supported by Linux. 

Please execute a 'lsusb' in the Terminal when having the Wireless USB device plugged in. Then paste the output in here.

Regards,
Pascal de Bruijn[/QUOTE]
 Alright cool, here it is.
Bus 001 Device 002: ID 13b1:000b
Bus 001 Device 001: ID 0000:0000

Is there any wireless USB device supported by Linux?

---

### Post by pmjdebruijn on 2005-08-29
Hmmm, is that it?

Generally a Manufacter or the likes is listed behind is ID code.

Maybe try a 'lsusb -v' ?

Anyway the key step to find out of the adapter can be made to work is to find out which chip is used in the adapter.

*You could try opening the adapter itself, to take a look at the chip, but it's at your own risk.*

**Or** you could try contacting the manufacturers technical support, asking for the chip data.

Regards,
Pascal de Bruijn

---

