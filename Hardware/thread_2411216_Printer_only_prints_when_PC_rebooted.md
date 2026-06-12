---
title: "Printer only prints when PC rebooted"
date: 2019-01-27
forum: Hardware
---

### Post by pecoflyer on 2019-01-27
Hi
using Xubuntu 18.04.1 LTS 
Pc connected by Ethernet to router and printer Canon Pixma TS6150 via WFi to router
I can ping the printer, get the remote admin screen.
Every time a print the document stays in the print queue (says printer cannot be reached),and when I reboot the PC it prints normally.
I am at a loss
Thanks for any help you can provide

---

### Post by kc1di on 2019-01-27
I'm just guessing here. But sounds like you need to make a permanent Network address for the printer.  What happens is each time you add or remove any thing from the network. IE another computer or some other device wireless or hard connect the IP address of the printer changes, with DHCP.  So look in your printer info and see if you can put a fixed IP address on the wireless printer choose one outside the normal DHCP range up in the 250 or so.. So it will look something like 192.168.0.253 or so.  It will depend upon your router what the range is on mine it's in the 10.0.0 .xxx range. [This page ]("https://www.wikihow.com/Assign-an-IP-Address-on-a-Linux-Computer")may be of help.  Good Luck.

---

### Post by pecoflyer on 2019-01-27
Thanks for your reply
The printer has a fixed IP 192.168.0.108. I don't remember how I did it BTW :-)
(sorry for not mentioning it)

---

### Post by kc1di on 2019-01-27
In that case I would try deleting the current printer and reinstalling it. if you have not already tried that.

---

### Post by pecoflyer on 2019-01-27
Thanks, I'll try to find out how, and come back

---

### Post by pecoflyer on 2019-01-27
Tried it, but is stays the same saying that the printer " may not be connected" when I try to print the test page

---

### Post by kc1di on 2019-01-27
does your printer have a sleep function?  if so try turning that off if possible.

---

### Post by kc1di on 2019-01-27
You may also want to try the cannon driver found [here]("https://www.canon.co.uk/support/consumer_products/products/fax__multifunctionals/inkjet/pixma_ts_series/pixma-ts6150.aspx?type=drivers&language=&os=LINUX") (download the debian driver)
Other than that since I do not have that printer to play with, You'll have to wait for someone with more info on your particular printer.

---

### Post by him610 on 2019-01-27
Network setup for your printer, [https://ugp01.c-ij.com/ij/webmanual/Manual/All/TS6100%20series/EN/NTR/faq_003.html#NTRfaq00302]("https://ugp01.c-ij.com/ij/webmanual/Manual/All/TS6100%20series/EN/NTR/faq_003.html#NTRfaq00302")

---

