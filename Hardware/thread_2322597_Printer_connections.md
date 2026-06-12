---
title: "Printer connections"
date: 2016-04-29
forum: Hardware
---

### Post by simon_b2 on 2016-04-29
Hi all - I'm having frustrations with my printer connection. The printer IP keeps changing - the other laptops in the house (on windows) don't seem to have problems with this but my laptop with Ubuntu 14.04 doesn't know how to cope. This has only been a problem since we changed routers, the printer is a Canon MP495. I've tried deleting and adding the printer - when I do the printer doesn't show on the network and I have to find it via the IP. I then have to keep changing the printer IP address in the manual set-up every couple of days. It's driving me mad.

---

### Post by kc1di on 2016-04-29
Hi Simon_b2 and Welcome to Ubuntu.
your problem is stemming from your network assigning new ip addresses each time you boot up. 
you need to set the printer IP address to manual and enter an IP address that is not likely to interfere with other Items on the Network.

For example on my network here IP addresses run from 100.162.1.0  up to 100.162.1.100 or so  I set my printer to 100.162.1.50  I will never have 50 devices on this net work so it will never interfere with anything else.  After you've done that go into the printer setup and change the IP address to the one you choose and it shouldn't be a problem any longer -- in a wireless printer net work it's always good to set the printer to a fixed IP address. 
good luck.
P.S. the printer documentation should tell you where the IP can be set.  Your network IP's will be different than the examples listed above.

---

