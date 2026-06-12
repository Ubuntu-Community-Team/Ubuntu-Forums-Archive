---
title: "Hp deskjet 3752"
date: 2016-11-12
forum: Hardware
---

### Post by modon on 2016-11-12
Don't know if this will help anybody. I bought a cheap wireless HP Deskjet 3752 from Wallyworld for non critical work. I was mistaken that as an HP Printer it would be Linux friendly. While as USB was recognised by my Ubuntu box, the unit would not print using the recommended HP 3740 driver. The 3752 was not easy to set up in a Windows VirtualBox, either. Before returning the unit to the store, I worked on a solution.

To use as USB printer, the PPD to use is  HP Envy 110 Series, hpcups 3.16.3

To print wirelessly, I was able to connect to printer as a wireless SSID, then set up using a browser at the printer's address. This was found by pressing the wireless button and the information buttons simultaneously on the printer which was 
[http://192.168.223.1](http://192.168.223.1).  There I could set the printer to connect to the wireless network.

That will teach me to buy stuff at WallyWorld

---

