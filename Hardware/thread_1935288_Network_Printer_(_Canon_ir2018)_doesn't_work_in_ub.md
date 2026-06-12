---
title: "Network Printer ( Canon ir2018) doesn't work in ubuntu 11.04"
date: 2012-03-04
forum: Hardware
---

### Post by eveningpolestar on 2012-03-04
I have a network printer in my office. 
Canon ir2018

I tried installing it as a standalone printer and as a windows shared printer. On both cases, it shows printer has been successfully installed. But when I give a print job, nothing happens.

I have installed the Cque drivers provided by canon as well.

Any ideas on why is it not working??

thank you for you help in advance!

Regards
Eveningpolestar

---

### Post by EtoIxPi on 2012-03-04
[https://launchpad.net/~robbiew/+archive/cups-bjnp](https://launchpad.net/~robbiew/+archive/cups-bjnp)

If this canon printer uses the bnjp network interface this package should help you out. Install it and disable your firewall to see if it works(my printer needs ports 8610:8620 tcp/udp to work). I was unable to determine if your printer uses bnjp, so just try it.

Be polite and let us know if this solves your problem so someone else doesn't have to make a thread about it.

---

