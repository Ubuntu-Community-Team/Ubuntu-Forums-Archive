---
title: "Startech USB 2.0 card"
date: 2007-08-29
forum: Hardware &amp; Laptops
---

### Post by BSK on 2007-08-29
Hi,

I'm on Ubuntu 7.04 and I have a Startech USB card in a PCI slot, Ubuntu seems to "see" the card but any device connected to that card is not recognized.  Can anybody help?

[http://www.startech.com/Product/ItemDetail.aspx?productid=PCI425USB&c=CA](http://www.startech.com/Product/ItemDetail.aspx?productid=PCI425USB&c=CA)

Thanks!

---

### Post by BSK on 2007-08-30
someone ?

is there anything I can check to see if some drivers or modules is loaded or something ?

thanks!

---

### Post by geraldm on 2007-08-30
Hi,
When I goggle the card id, I got only one vendor, and at his price the only thing I would
recommend is returning it.  Low price USB 2.0 cards can be obtained for about ten percent
of his asking price. 
The card is OHCI, so check that the ohci_hcd AND ehci_hcd modules are loaded. 
The command lsmod should provide that information.

Gerald

---

### Post by BSK on 2007-08-31
I got the card for 20$CAD, I was pretty happy with that.

I will check the output of lsmod ASAP.

Thanks a lot for the help!

---

