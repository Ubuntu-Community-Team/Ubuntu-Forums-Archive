---
title: "3Com network card not found"
date: 2004-10-18
forum: Installation &amp; Upgrades
---

### Post by cmoir on 2004-10-18
I'm a Linux newbie and would love to try Ubuntu - it's 'less is more' approach is exactly what I believe will help wider adoption.

Everything installed fine, however I can't connect to the LAN, even though I'm using a common 3Com ethernet card. What's more Suse Linux 9.1 which I tried previously worked fine.

I think I know what the problem is - the network card (3Com 3c900) has 2 interfaces, a 10base2 coax BNC connector as well as a more usual 10baseT. I'm using the BNC connector.

Windows works fine, and I managed to get the Suse Linux drivers to work by altering a config file to force the card to use the BNC connector. I can't find the same config files for Ubuntu.

There are open source drivers here: [http://www.scyld.com/vortex.html](http://www.scyld.com/vortex.html) which imply that these drivers can be set to be auto-select. I have no idea if these are the divers that Ubuntu uses (I think it is as I can find the the 3c59x.ko file)

The question is, is there a config file somewhere that I can config or force the drivers to auto-select the correct interface or just force it to use the BNC connector?  Any other reason why my network card might not be working?

Any help much appreciated.

---

### Post by ompayne on 2004-10-22
I set up this card using vortex-diag, available from 
[http://www.scyld.com/ethercard_diag.html](http://www.scyld.com/ethercard_diag.html)
You may need to compile it.  IIRC, use the -F flag to set the interface type. 

HTH

---

### Post by cmoir on 2005-01-09
Er, right so how do I compile the C diagnostic utility.  (newbie showing up here).

I thought all you needed to do was a cc filename or make or somethig along those lines in a terminal window. But when I try it complains the cc command is not found.

So how do I compile a C program under ubuntu (sorry for being this basic).

---

