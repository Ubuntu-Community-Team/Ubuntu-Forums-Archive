---
title: "SD card does not mount"
date: 2007-10-16
forum: Hardware &amp; Laptops
---

### Post by erikf154 on 2007-10-16
I have a built in Ricoh Co Ltd RL5c476 II (rev ac) card reader on my laptop. There's an open source driver for this reader available at sourceforge ([http://sourceforge.net/projects/sdricohcs/](http://sourceforge.net/projects/sdricohcs/)). However to get my particular version of the card reader to work I needed to patch the source (Sascha, the developer made one for me). Once patched and installed things seems to be working fine, I insert the card, it's detected, however it does not mount.

There's the dmesg output:
[100440.444000] pccard: PCMCIA card inserted into slot 0
[100440.444000] cs: memory probe 0xd0200000-0xd02fffff: excluding
0xd0200000-0xd020ffff
[100440.444000] pcmcia: registering new device pcmcia0.0
[100440.660000] sdricoh_cs: Ricoh PCMCIA Secure Digital Interface driver
[100440.660000] sdricoh_cs: Copyright(c) 2006 - 2007 Sascha Sommer
[100440.660000] sdricoh_cs: Searching MMC controller for pcmcia device
RICOH Bay2Controller ...
[100440.660000] sdricoh_cs: MMC controller found

Running the following commands:
# pccardctl info:
PRODID_1="RICOH"
PRODID_2="Bay2Controller"
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=254
PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255

# pccardctl ident
Socket 0:
 product info: "RICOH", "Bay2Controller", "", ""
 manfid: 0x0000, 0x0000
 function: 254 ()
Socket 1:
 no product info available

# pccardctl status
Socket 0:
 3.3V 16-bit PC Card
 Subdevice 0 (function 0) bound to driver "sdricoh_cs"
Socket 1:
 no card

There's no device in /dev called pcmcia0.0 or anything with mmc (as
seen in forums), would anyone happen to know what's wrong. There should
be a node made so I can mount it...

---

### Post by hardyn on 2007-10-16
i have read several documents to enable the ricoh card reader, and i could not get it to work for me.

good luck.

---

