---
title: "Will I face hardware problems with my new pc"
date: 2008-09-07
forum: General Help
---

### Post by sowhat12345 on 2008-09-07
I want to buy a new computer with the following configuration:

Gigabyte P31-S3G Bearlake PCI-Ex16 FSB 1333mhz DDR2-800 mhz
intel Quad Core Q6600 2.40 GHZ, 1066MHZ, 8MB
SAMSUNG SERIAL ATA 250 GB 16MB SATA2
XPERTVISION PCX 1 GB 8500 GT DDR2 128bit / DVI TV OUT
BOOST CASE VK-304 28
DD2 800Mhz 2048 MB RAM KINGSTON
SAMSUNG DVD RW  20X SATA / IDE
INFOTEK 3MP CAMERA,8 LED
CREATIVE AUDIGY 2 VALUE 24BIT 7.1 SOUND CARD
LOGITECH X540 70W RMS 5+1 SPEAKER
EVEREST KB-2808 M.M PS2 KEYBOARD

I can chance if any parts will not wok with Ubuntu 8.04.

---

### Post by itix on 2008-09-08
The main problems with Ubuntu and linux in general are network, mainly wireless network, and sound cards...

Make sure those work with Ubuntu and almost good to go.

---

### Post by manishtech on 2008-09-08
Just boot from Live CD and goto Terminal (Applications>Accessories>Terminal) and give the output of the following command

```
lspci| grep -i network
```

AND

```
lspci| grep -i graphics
```

---

### Post by khelben1979 on 2008-09-08
Without knowing all the facts about this specific motherboard, I can tell you that everything you have there should work, except that you might get problems with the digital camera(I don't know about that one here).

Check [this]("http://www.phoronix.com/") site out. It might help you out a little. They have reviews on pc hardware together with Linux. Hope it can help you out a little over there.

---

### Post by manishtech on 2008-09-08
> except that you might get problems with the digital camera

Never ever had problem with any digicam ever

---

