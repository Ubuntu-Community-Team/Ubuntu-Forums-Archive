---
title: "problems with dialup on acer laptop"
date: 2006-04-27
forum: Hardware &amp; Laptops
---

### Post by goathunter on 2006-04-27
hello. I have just installed ubuntu on my Acer Aspire 3004LMi Notebook . However it has not detected the internal 56k modem. Is there a way to install the driver and how would I find out what type of modem it is?
Thanks for your time.

---

### Post by dangermouse28 on 2006-04-28
Open a terminal and use lspci to give you the details of your system. Look at the output for the type of modem you have fitted. Chances are it is a "winmodem"  - go to [www.linmodems.org](www.linmodems.org) for a great resource on modems in linux.

---

