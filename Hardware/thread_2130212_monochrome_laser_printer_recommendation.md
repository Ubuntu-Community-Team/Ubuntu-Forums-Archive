---
title: "monochrome laser printer recommendation"
date: 2013-03-28
forum: Hardware
---

### Post by arod0405 on 2013-03-28
My HP inkjet just died - 13 years! - and I need a replacement. My usage pattern is:
[LIST]
[*]<250 pages/month
[*]black and white only
[*]printer should be shared among PCs
[/LIST]

I'm looking for a printer with:
[LIST]
[*]low price (<150€)
[*]low cost per page (toner/ink cost)
[*]full linux support and **no proprietary driver/blobs**
[*]long term support (will I find toner cartridges in 10 years?)
[/LIST]

So I guess I should go for a monochrome networked laser/LED printer. I made some research on linux forums ML and wikis, the openprinting DB and hplip website but I'm still confused. In theory I should just buy an HP or some printer supporting a generic language as Postscript or PCL5e/6 but:
[LIST]
[*]just buying an HP doesn't work because new models need a proprietary blob in addition to the open source hplip driver
[*]postscript should always work out of the box but postscript printers are pricey or can be buggy and slow
[*]printers immediately above the ultra cheap GDI moldels claim to support PCL language but some are buggy or hard to configure
[*]there is little to no information about linux support and no reliable sources (the openprinting DB is not up to date)
[/LIST]

I've been looking at Brother hl-2250dn (PCL with some linux userbase), xerox 3250dn (PCL/PS capable) or Samsung ML-2955nd (real cheap with PCL and maybe splix support). It there some particular model you can recommend? Do you have some positive feedback about some model/brand?

Thanks!

---

### Post by sanderj on 2013-03-28
I have a USB-only Brother HL-2030, and it works great under Linux: plug and print. 

So ... I would look for a Brother

---

### Post by foresthill on 2013-03-29
I always recommend these:

[img]http://www.driver-world.com/wp-content/gallery/printer/hp-laserjet-1320.jpg[/img]

HP Laserjet 1320. I got one for $15 at a thrift store a few years back. Very sturdy, well-supported in Linux, easy to find cartridges for, and memory is upgradable to 144 MB via adding a 128 mb stick, as I did. USB and parallel support, but no ethernet or wireless. I use a print server on mine to convert the parallel port to ethernet, though the USB port also works well.

These are one of the printers that gave HP a great reputation, but I find the newer models are flimsy, overpriced, and poorly-supported (in Linux) crap. Hopefully you can find a refurbished one at a good price. Lots of government offices use these and similar models, and will practically give them away when they upgrade. 

[http://refurbexperts.com/product/46/HP-LaserJet-1320-Reconditioned-Laser-Printer?utm_source=productlistingads1&gclid=CLWH7pWUorYCFcw7Mgod2F0AOQ](http://refurbexperts.com/product/46/HP-LaserJet-1320-Reconditioned-Laser-Printer?utm_source=productlistingads1&gclid=CLWH7pWUorYCFcw7Mgod2F0AOQ)

---

### Post by arod0405 on 2013-03-29
> **foresthill said:**
> I always recommend these:
...

HP Laserjet 1320. 

According to his [hplip DB page]("http://hplipopensource.com/hplip-web/models/laserjet/hp_laserjet_1320_series.html") this printer is marked as "not recommended" and "end of support". 

Anyway I prefer buying a new printer.

---

### Post by foresthill on 2013-03-29
> The HP product has reached the end of support life, meaning the HPLIP solution is considered &#8220;As-is&#8221;. No further HPLIP code changes will be implemented by HP.  While monitoring of Launchpad posts by HP personnel will continue, follow-up by HP personnel on these products will be extremely limited. Community members are encouraged to assist others with issues on these printers.  Patches provided to HP to address issues on these products will be considered (but not guaranteed) for inclusion in future HPLIP releases. As of the end-of-support date, device functions and features available from the product and available from HPLIP should continue to function but cannot be guaranteed to continue to work in subsequent HPLIP releases.

Mine works fine, and I don't need any new features. I get that HP would like you to buy a new HP printer. What would you expect them to say? Besides, this printer works even without HPLIP support, AFAIK.

Whatever though, suit yourself. All the new monocrhome laser printers I looked at recently were ridiculously expensive and quite flimsy to boot. Good luck in finding one at a fair price that fits your requirments.

---

### Post by gordintoronto on 2013-03-30
I have a "wireless" Brother laser attached to my router by Ethernet cable, and it works beautifully. It came with a Windows program to set it to use a static IP address, and I did that. I try lots of new versions/distros, and setting up the printer is a piece of cake: Printers/Add/Network, wait a few seconds, then OK/continue until it works.

I don't know if it uses a proprietary driver/blob, but I think just about every printer does.

The specific printer is not a current model, but when it dies, I will almost certainly replace it with another Brother laser.

---

### Post by d0006 on 2013-03-30
I really like the reviews on this site: [http://www.consumersearch.com/laser-printers-monochrome](http://www.consumersearch.com/laser-printers-monochrome)

The Canon imageCLASS LBP6300dn looks nice.  My sister has had good luck with Brother printers.

I have had bad experiences with with every HP product I have bought in the last ten years so I recommend avoiding HP products.

---

### Post by MyR on 2013-04-02
This might help in your search: [Linux monochrome laser printers]("http://linuxdeal.com/printers.php?output=monochrome&tech=laser")

Reviewed by Linux users :D

---

