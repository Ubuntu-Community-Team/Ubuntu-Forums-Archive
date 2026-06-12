---
title: "Best Wireless Card"
date: 2008-06-05
forum: Hardware
---

### Post by WeEatVista on 2008-06-05
Just recently, I finally gave up trying to make my wireless card work, that came in my laptop, with ubuntu. For my ubuntu laptop, I am just going to buy a new wireless card. Are there any wireless cards that work, out of the box, with ubuntu 8.04? If not out of the box, then with easy to obtain and install Linux drivers. Any suggestions?

Thanks in advance,

WeEatVista

P.S. There was a thread that asked this same question, but that was focused around Dapper Drake.

It seems I put this in the wring thread, sorry about that. While looking on google some more, I found a wiki page so I am set. Problem solved.

---

### Post by stchman on 2008-06-05
> **WeEatVista said:**
> Just recently, I finally gave up trying to make my wireless card work, that came in my laptop, with ubuntu. For my ubuntu laptop, I am just going to buy a new wireless card. Are there any wireless cards that work, out of the box, with ubuntu 8.04? If not out of the box, then with easy to obtain and install Linux drivers. Any suggestions?

Thanks in advance,

WeEatVista

P.S. There was a thread that asked this same question, but that was focused around Dapper Drake.

It seems I put this in the wring thread, sorry about that. While looking on google some more, I found a wiki page so I am set. Problem solved.

Is this a laptop or a desktop?

For a desktop the only problem is that the make of card could have different chipsets.  FOr a laptop most are a mini-PCI.  For that I would recommend an Atheros 5006EG as it works OOB with Hardy.

Here is a site that specializes in Linux compatible hardware.

[http://www.linuxemporium.co.uk/products/wireless/](http://www.linuxemporium.co.uk/products/wireless/)

The Intel 4965 seems to be compatible with Hardy OOB as well.

---

### Post by gss6 on 2008-06-06
> **stchman said:**
> IThe Intel 4965 seems to be compatible with Hardy OOB as well.

Actually, the iwl4965 driver (the driver that the 4965 and 3965 uses) seems to be quite broke in Hardy. You would need to use ndiswrapper to get any kind of connection to an encrypted network. A walkthrough on how to do this can be found [here]("https://help.ubuntu.com/community/WifiDocs/Driver/Intel_4965_AGN_WiFi_Driver/Fiesty").

---

