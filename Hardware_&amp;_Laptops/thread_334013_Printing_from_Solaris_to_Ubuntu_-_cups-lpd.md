---
title: "Printing from Solaris to Ubuntu - cups-lpd"
date: 2007-01-08
forum: Hardware &amp; Laptops
---

### Post by f3ua on 2007-01-08
Hi everybody.

I've a big question about printing in my network, were I have a Solaris SUN OS 5.x that runs a managerial software. This uses LPD printing system, and I have to install a network printer on a client pc with ubuntu 6.10 installed, so i can print from the solaris.

To do this i've installed on the ubuntu pc "cups-lpd" and configured the network printer on the solaris.

The system works, but there are 2 terrible issues:

1) a banner page is always printed, at each request and i can't disable it (on the banner there is cups logo...) and lot of paper is wasted.

2) Unfortunally my managerial software sends the requests to the printer with the control chars included. So I have to setup cups with a "dumb" driver, elsewhere the request will pass 2 drivers (one on the solaris, and one on cups).
NOTE: if I setup a generic printer on the solaris the request is printed but the layour is worst, so I must change cups driver.

Please help me.
Thanks! :)

---

