---
title: "Brother MFC-j280w compatibility?"
date: 2012-11-23
forum: Hardware
---

### Post by lykwydchykyn on 2012-11-23
I'm in the market for a new all-in-one, and have next to no money for it.  The Brother MFC-j280w looks like a stupendous deal for what I need, but I can't find hard info on its Linux compatibility.

There's some indication that there's a working print driver for it, but it's not in the SANE database for scanning.  EDIT: I found some kind of brscan utility for Linux that works with this device, but I'm not clear if that will allow SANE scanning (esp. over the network).  

Does anyone have any info on this device, or can recommend something with similar functionality (scan/print/copy) in the sub-$100 range?

---

### Post by gifford on 2012-11-24
It seems the drivers are available on the Brother site. As for sane, use the  brscan4 driver on the Brother site. There are step by step instructions for setting it up including on a network. The scanner will work just fine.

My experience with Brother all in ones with Linux has been great. It does take some time to set up but once done works flawlessly.

---

### Post by kurt18947 on 2012-11-24
> **lykwydchykyn said:**
> I'm in the market for a new all-in-one, and have next to no money for it.  The Brother MFC-j280w looks like a stupendous deal for what I need, but I can't find hard info on its Linux compatibility.

There's some indication that there's a working print driver for it, but it's not in the SANE database for scanning.  EDIT: I found some kind of brscan utility for Linux that works with this device, but I'm not clear if that will allow SANE scanning (esp. over the network).  

Does anyone have any info on this device, or can recommend something with similar functionality (scan/print/copy) in the sub-$100 range?

For printing, I recommend the installer script on Brother's web site.  We have a MFC-J430W and printing is trivial to set up.  I haven't set up scanning on that machine but have done so on others.  Scanning is not so simple but if you look at the scanning FAQs on the linux drivers page, you should be able to get along okay.  I've seen the MFC-J430W as low as $49.99.  I also use refillable ink cartridges from inkowl.com on two brother machines.  The only thing I notice is that it's a good idea to print something at least once a week or the print head may become partially plugged.  I don't know if this would be as much of an issue with Brother cartridges.  Bulk ink is cheap enough that I just print something every few days, need it or not.  I will add that when I install network printing, I assign a static I.P. address to the printer and use JetDirect/Socket.  I haven't had much luck with printers being recognized after restarting the O.S. with other network printing.

Edit:  OfficeMax is showing the MFC-J430W for $49.99 but they're sold out online.  If you have an OfficeMax near you, it might be worth checking.
[http://www.officemax.com/technology/printers/inkjet-all-in-one-printers/product-prod3590058?cm_mmc=Googlepla-_-Technology-_-Printers-_-Inkjet%20All-in-One%20Printers&ci_src=17588969&ci_sku=23151884]("http://www.officemax.com/technology/printers/inkjet-all-in-one-printers/product-prod3590058?cm_mmc=Googlepla-_-Technology-_-Printers-_-Inkjet%20All-in-One%20Printers&ci_src=17588969&ci_sku=23151884")

---

### Post by lykwydchykyn on 2012-11-25
Thanks; I decided to go for it, got it off tiger direct for 39.99, which is cheaper than ink cartridges for some of the others.  Will definitely check out the refillable carts.

I have had my printer hooked up to a debian server and shared via CUPS, so I'm not worried about the wireless.  Hopefully this will be a good experience.

---

