---
title: "Recommended WLAN hardware"
date: 2007-01-21
forum: Hardware &amp; Laptops
---

### Post by SlayerMan on 2007-01-21
Hi!

Which Linux-compatible WLAN adapter (USB or PCI, doesn't matter) would you recommend?

There should be open drivers for it, so it works the Linux-way of doing things (plug it in, works :) ), and it should be available in stores for a reasonable price.

Kind Regards
Steffen

---

### Post by Jussi Kukkonen on 2007-01-21
I suggest you consult the "Linux & Wireless LANs" -document: [http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/](http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/)

There are a few reasons why it's not easy to answer your question. Quoth the document:
> The first problem is that there are now lot's of different vendors and brands, and most I've never heard off (and they tend to be the cheapest, so the most popular). It's almost impossible to track down all of them. Fortunately, there is only a limited number of chipset, so most of those vendors sell the same hardware (or minor derivation) and there is a good probability that it works with an existing Linux driver. 
The other issue is that some vendors use different chipsets in their various products, so some of their cards might be supported and some might not be. They can switch their entire product line to a new chipset pretty quickly, so a "brand" is not a safe bet. Some vendor even sell different chipset under the same model number (example D-Link and Linksys), making it very difficult to know in advance if the card is supported or not.

In the past, most of the "generic" brands selling 802.11b cards were using the Intersil PrismII chipset, which is well supported under Linux (various drivers), so it was not a problem. A lot of them have recently moved to non-supported chipset. For now, if it's faster and better than 802.11b, it's most likely not supported. 

It's easier to blacklist some linux un-friendly companies: Broadcom, TI and nowadays also Conexant are not interested in getting money from linux users.

---

### Post by SlayerMan on 2007-01-21
Hi,

thanks for the fast reply and the valuable link.

Understanding various other sources, it seems that in case of wireless cards, more and more devices work. However, most of them work only with proprietary drivers and/or proprietary firmware. Unfortunately, the Linux kernel gets more and more hostile to proprietary drivers... but this is definitely a subject which does not belong into the support forums.

Thanks again for the link.

Kind regards
Steffen

---

### Post by Jussi Kukkonen on 2007-01-22
> **SlayerMan said:**
> Hi,

thanks for the fast reply and the valuable link.

Understanding various other sources, it seems that in case of wireless cards, more and more devices work. However, most of them work only with proprietary drivers and/or proprietary firmware. Unfortunately, the Linux kernel gets more and more hostile to proprietary drivers... but this is definitely a subject which does not belong into the support forums.

You are probably right about that -- but if you hadn't added that last line, we would have had to argue about who really is hostile towards who... :)

---

