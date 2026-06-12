---
title: "Driver for WiFi chip RT3593 (Ralink)"
date: 2012-12-05
forum: Hardware
---

### Post by mwolfram on 2012-12-05
Hi!

I'm having trouble finding a suitable driver for a Ralink RT3593 WiFi card. 

lspci says:
```
01:00.0 Network controller: Ralink corp. Device 3593
    Subsystem: Ralink corp. Device 3593
    Kernel modules: rt2800pci

```Unfortunately the rt2800pci driver doesn't seem to support my chipset. I don't see any wireless devices, all my other network interfaces work as expected. I'm running an Ubuntu 12.04, currently 32bit, but I'd switch to 64bit if a 64bit driver's available.

Thanks in advance for any hint!
cheers
Máté

---

### Post by jdhoskins on 2013-06-12
HI,

Did you ever find a way to make this card work?  I'm also trying to install the same card with no luck.

John

---

### Post by christophGrz on 2013-06-12
Hi,

I'm working on the same project as Máté. **We had no luck**. I also tried to get support from RALINK because we actually have an OS Image with a working driver (Binary) which seems that it was compiled from one of their provided packages (so at least they have a driver!) but we did not receive an answer. We switched to an Intel chipset...

Sorry,
regards Christoph

---

### Post by jdhoskins on 2013-06-12
Thanks for the quick reply!  I downloaded and installed the linux driver from their site an couldn't get it to work either.  I'm thinking I may have to abandon this card.  I really hate to do that though.

---

