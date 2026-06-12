---
title: "Canon IP5000 printing issue"
date: 2016-07-24
forum: Hardware
---

### Post by ricey650 on 2016-07-24
I'm new to Ubuntu and am trying to print to my old Canon IP5000 inkjet but have been unable to find a driver, any help in enabling me to print to it would be appreciated.

---

### Post by gordintoronto on 2016-07-24
What version of Linux?

This is worth trying: run Printers (or perhaps printing) with the printer connected and turned on. Select "Add" or "+" and see if the printer appears. Select it and then OK or proceed, or some such.

---

### Post by ricey650 on 2016-07-25
Hi gordintoronto,
Thanks for your reply, I'm running MATE Desktop Environment 1.12.1 and have just tried your suggestions, but no luck, the PC sees the printer and knows the model but wont print to it...

---

### Post by gordintoronto on 2016-07-25
In Mint 18 Mate, I set up my networked Brother laser. I had to manually enter the "URI" in Printer Properties. I found the URI from my Mint Cinnamon desktop.

Have a look at the Properties to see if there is an error.

---

### Post by mail-2o on 2016-07-26
Assuming that you have simply plugged it in, it is worth looking at CUPS. Type [http://localhost:631](http://localhost:631) into your browser and see what you get. You should be able to administer your printer from the CUPS interface.

---

