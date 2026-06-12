---
title: "Modem setup for Old PCs"
date: 2005-12-18
forum: Hardware &amp; Laptops
---

### Post by Rajan Varadarajan on 2005-12-18
I recently installed ubuntu on a Gateway P2 - 266MHz, 320MB RAM, two hard drives (28gb and 20gb), ethernet card, and a 56k modem. I have connected this machine to a 5-port ethernet switch (which is connected to a DSL modem). The whole install went through smoothly and the performance for this old machine (1997) is not at all bad. I would like this machine to act as fax receiver (in addition to being a Linux desktop), for which I need to configure the modem. I have tried two days with no results.

Thanks in advance for all your suggestions and help.

---

### Post by 23meg on 2005-12-18
You'll have to specify the exact brand and model of the modem and whether it's detected in Device Manager and Networking.

---

### Post by Rajan Varadarajan on 2005-12-19
Thanks. I will find the chipset specs. Found some details - the modem is (I suspect is a winmodem) US Robotics. Gateway calls it Telepath X2 56kbps with fax capability. It is on a PCI card. I found a lot of details about the protocols but not exactly the chipset numbers.

But I still have other issues. Why does the setup require and ISP name and phone number? I already have a DSL connection through a switch/router and there is no need for ISP. I want to configure the modem to receive faxes - my old fax machine died and I don't want to buy another one; instead I want my ubuntu desktop to be able to do the job. Is there a way to configure the modem (after I get the proper drivers) without ISP numbers?

Thanks for all your help/suggestions.

---

### Post by Rajan Varadarajan on 2005-12-26
Finally got around to pulling out the modem card to examine the details:

Gateway 2000 Telepath 56K fax/modem - Gateway part# 60000639
Does not look like a PCI slot but the long EISA slot; the modem itself goes only
half way; so I think it is an ISA card.
Manufactured by US Robotics - the card has the number: 1.012.0478-B
The chipsets (at least the two main ones) are made by Texas Instruments:
Main chip: 1.016.1067; PD17238PJ; HBS-78AC74W
The second big chip: TL16CFM600APJM; 78A90K7; 1.016-1083

Looked in US Robotics site for Linux drivers but couldn't proceed further. Because the selection menu required selecting a model number but none of the above numbers were listed in the drop down option.

Any help is appreciated. I want to set up this modem for receiving faxes; I seldom send any (I can always use my WinXP machine for that).

Thanks very much and happy new year to all of you.

---

