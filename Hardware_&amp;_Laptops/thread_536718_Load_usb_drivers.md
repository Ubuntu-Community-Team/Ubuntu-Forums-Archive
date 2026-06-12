---
title: "Load usb drivers"
date: 2007-08-28
forum: Hardware &amp; Laptops
---

### Post by ripit on 2007-08-28
Hi,
I hava a usb tvcard and when I plug it in I dont't think it's properly recognized. It is a Pinnacle PCTV 310e. lsusb shows: 

Bus 005 Device 003: ID 13d3:3211 IMC Networks
Bus 005 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

So now I wonder is there a way of telling the pc that this card is a tvcard and if it can be done set it as /dev/video0 or something.

I have read something about udev or hal and if I'm not mistaken I can use one of them to tell the pc what kind of card this is, but I don't know how. I have the v4l drivers installed but they don't get loaded.

If there is anyone who could help me so please do. I have Ubuntu 6.06 on this machine it was installed as a server but when it didn't work with this card I took a big chance of recompiling the kernel but it still didn't work. 

I don't want to use windows but my girlfriend nagging me about getting this to work so we can record things for our son. So please help me if it's possible to get this card to work with ubuntu.

---

### Post by ddrichardson on 2007-08-29
Yes - but you need to locate the correct firmware for the card. [Linux TV]("http://www.linuxtv.org/wiki/index.php/Main_Page") is a good place to start finding out how to get it all working.

---

### Post by ripit on 2007-08-30
Hi,
I can't figure this out do I need the firmware to load the drivers or is it the drivers who loads the firmware?

I thought the drivers where loaded first and I needed to tell in some file witch drivers to load when a usb with a specific id was inserted. And after that load the firmware. If thats so in what file should I tell witch drivers to load?

---

### Post by ddrichardson on 2007-08-30
I know with mine (Freecom DVB-T) once I had the right firmware, I put it in /etc/firmware and the usb sub-system identified it correctly - but that was on Fedora Core not Ubuntu - I'm not sure where the firmware is on Ubuntu.

---

