---
title: "[SOLVED] second printer of a HP jetdirect 500"
date: 2008-01-09
forum: Hardware &amp; Laptops
---

### Post by hutxubix on 2008-01-09
Hi,

I am changing to Ubuntu at work. I have two printers HP (Laserjet 1200 + bussines inkjet 2250) connected via net through a Jetdirect 500 with a fixed IP address. 
If you type the IP address on the browser you can access both printers, and I have both of them installed on WXP.
However, on Ubuntu 7.10, I am only able to install that connected to the Port #1 of the Jetdirect (Laserjet in this case) and I cannot see the other one.

SOLUTION:

System -> Administration -> Printers
Add new printer -> Others -> URI:  socket://IPADRESS:Port  

Example: 

socket://210.13.13.84:9100  (for printer 1)
socket://210.13.13.84:9101  (for printer 2)
socket://210.13.13.84:9102  (for printer 3)

Easy if one knows how.

---

### Post by hutxubix on 2008-01-10
Any idea, please?

---

