---
title: "Netgear WG111T Wireless Card on Hardy Heron"
date: 2008-05-01
forum: Hardware
---

### Post by fjrreseda on 2008-05-01
I made a clean install of Hardy Heron on my Dell Inspiron 5100 laptop.

I had my Netgear WG111T USB wireless card working when using Gutsy on the same machine.  Using the same setup, I cannot get the card to work anymore.

Using the updated drivers, ndiswrapper shows that the drivers are installed and the hardware is present.  However, I get no reaction from the USB card.  The LED never lights up.

I decided to use an older set of drivers, but now the athfmwdl.inf driver shows the hardware is not present.  The wg11nt.inf shows the hardware present.  I can connect to the wireless network, even with WPA, and the LED lights up.  However, I still can not get any data to stream (i.e. no internet, no transfers between machines).

I checke the router and internet connections with another machine, and everything there is okay.

How do I get ndiswrapper and the athfmwdl.inf driver to detect the the wireless card?  Any help would be appreciated.  Thanks.

---

