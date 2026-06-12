---
title: "RT61 driver and d-link pcmcia card woes"
date: 2007-04-04
forum: Hardware &amp; Laptops
---

### Post by moynihan on 2007-04-04
Hi folks,

I've recently installed feisty beta on my laptop and m having a lot of difficulty getting my pcmcia wireless card to work. It's recognised by the OS and is able to detect wireless networks but cannot connect. It's a D-link Dwl g630 rev E2 using the rt61 driver. The output of lspci shows the chipset to be a RaLink RT2561/RT61 rev B 802.11g. iwlist shows available local wireless networks

ra1       Scan completed :
          Cell 01 - Address: FF:FF:FF:FF:FF:FF
                    ESSID:"*******"
                    Mode:Managed
                    Channel:12
                    Encryption key: off
                    Quality:0/100  Signal level:-35 dBm  Noise level:-256 dBm

(mac address and essid of my router altered because I'm a paranoid loon).
I've not seen any information on a card like this being recognised and working to the level that it will detect networks but not join them, so I'm pretty stumped.

Any help that could be offered would be greatly appreciated.

~moynihan

---

### Post by crosscountry on 2007-04-05
Hi,

I have exactly the same card and got it working. You have to install the latest RT61-driver from [http://rt2x00.serialmonkey.com/wiki/index.php/Downloads](http://rt2x00.serialmonkey.com/wiki/index.php/Downloads)  (nightly cvs)and install it. Then you can configure it in the way described in this thread: [http://ubuntuforums.org/showthread.php?t=392415](http://ubuntuforums.org/showthread.php?t=392415) 

lg crosscountry

---

