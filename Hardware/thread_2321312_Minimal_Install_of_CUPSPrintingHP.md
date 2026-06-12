---
title: "Minimal Install of CUPS/Printing/HP"
date: 2016-04-21
forum: Hardware
---

### Post by jakfish on 2016-04-21
I'm using a Mbook M1 netbook, and through a network install, I've put Xubuntu 14.04 on a 4GB partition. Obviously, space is tight, but I have about 500mbs to play with.

I have a HP Deskjet 3500 and I would like to do the lightest possible install of basic printing capability. I just need text printing of docs and email, no scanning. I'm hoping to avoid HPLIP altogether. I've gotten the 3500 to print successfully in Ubuntu (on other old machines) using ancient HP drivers such as the Deskjet 980, so HPLIP was not necessary.

Could someone advise me about how to make very, very light install?

Thanks,
Jake

---

### Post by jakfish on 2016-04-22
This is the way to do it:

sudo apt-get install cups cups-bsd cups-client cups-common

A total of about 18mbs. Avoid HPLIP, etc.

Go to [http://localhost:631](http://localhost:631), set up the HP 3520 (found on the network). For Printer, choose "HP DeskJet 990C Foomatic/chp2200" This driver will work for formatted document texts, emails, etc.

I'd be interested to hear if this driver worked for other current HP Deskjets...

For posterity,
Jake

---

