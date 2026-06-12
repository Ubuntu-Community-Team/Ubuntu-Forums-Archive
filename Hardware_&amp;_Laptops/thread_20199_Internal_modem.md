---
title: "Internal modem"
date: 2005-03-15
forum: Hardware &amp; Laptops
---

### Post by GingerMegs on 2005-03-15
I have an internal modem card recognised as having a conexant chip, but that's where Ubuntu's recognition stops.

How do I get U to find and configure the card please. Am aiming to set up a dial-up POP3 connection to email and 'Net O:)

---

### Post by alastair on 2005-03-15
What sort of modem?

Go to : [www.linmodems.org](www.linmodems.org)

and have a read. Download "scanmodem" and see what it thinks about your mode. It produces a lot of useful information - take some time to digest it.

---

### Post by az on 2005-03-15
The only driver available for linux is proprietairy and costs about the some as a new modem would cost you. The driver they will sell you will work for a year. When you upgrade your kernel, you may have to purchase the driver again.

They do not care about your freedom to use open source software.

A modem with a better record is one based on the intel chipset or the lucent chipset. Some intel chipset modems can be run on (mostly) GPL drivers while the Lucent ones are free, but proprietairy (no source code)

---

### Post by trigg on 2005-03-16
[QUOTE=alastair]What sort of modem?

Go to : [www.linmodems.org](www.linmodems.org)

and have a read. Download "scanmodem" and see what it thinks about your mode. It produces a lot of useful information - take some time to digest it.[/QUOTE]

I had the same problem with a "winmodem"  I guess that is the downside of having all this processing power (relatively speaking) - the modem companies decided that they didn't need to create indepently supported modems anymore and they just relied on propriatary code within a M$ framework.  I just bought an external Zoom modem - and I refuse to part with it in case my broadband bites the dust (much to the consternation of my wife).

Anyway, not sure about Ubuntu produced kernels, but there are quite a few kernel patches out there  to support "winmodems" if you feel like patching the kernel source yourself - linmodems.org (as alastair pointed out) is a good place to start.

trigg

---

### Post by az on 2005-03-16
Yes, indeed.  One exception is conexant (rockwell) chipsets, who make a point of having proprietairy-only linux drivers.

---

