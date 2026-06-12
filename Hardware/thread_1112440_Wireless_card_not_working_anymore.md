---
title: "Wireless card not working anymore"
date: 2009-03-31
forum: Hardware
---

### Post by pistacchio on 2009-03-31
Hi to all!
Some hours ago my wireless card stopped working. How can I check if it's a hardware problem or a software one?

my card is:


```

gu@memole:~$ lspci | grep Wire
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)

```

---

### Post by Dark_Stang on 2009-03-31
Did you do any kernel updates? If you did try to boot to an older kernel and see if it works there. Really the only way two ways to test a wireless card is... 1. Have another computer to test the card in or 2. Have another OS on your computer to test the card with.

---

