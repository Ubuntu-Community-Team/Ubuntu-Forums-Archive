---
title: "slow access to Photo Cards on a network printer"
date: 2006-11-28
forum: Hardware &amp; Laptops
---

### Post by kdawg on 2006-11-28
I have a HP photosmart c6180 network printer that works perfectly with ubuntu (I highly recommend it, prints awesome photos)  Setup was a breeze with cups and the hplip drivers.  

Currently it is setup like this: My machine is hard-wired into the router, and the printer is wireless on the network, so when I plug a photocard into the printer, I can run hp-unload and browse the photos on it with a gui and download them if I want.  Problem is, hp-unload is slow and takes forever to suck jpegs off the card.  I think it may be because hp-unload is made for older technologies or something... from the hplip sourceforge page:

> hp-unload provides an alternative for older devices that do not support USB mass storage or for access to photo cards over a network.

So what can I do to speed it up or what other software can I use to access the cards from the printer without mounting them from the camera as a usb drive???  Thanks!

---

### Post by kdawg on 2006-11-28
bump

---

### Post by rnakim on 2008-03-08
You can access the Photo Card reader over the network by using the IP address of the printer. Mine is 192.168.1.100 so I can open the URL smb://192.168.1.100 in Nautilus, or another file/web browser.

---

### Post by pmaconi on 2008-04-26
I have the same problem. My printer is on 192.168.1.103. I can open that address using [http://,](http://,) but not smb://. Is there some type of setting that I need to enable?

---

