---
title: "Printer Canon Pixma 280s not responding"
date: 2013-09-11
forum: Hardware
---

### Post by dovah on 2013-09-11
Hello everyone, 

I recently have an issue with my printer: it isn't working as it should, neither for printing from my PC (running Ubuntu 12.04LTS) , nor for scanning. I cannot understand the problem, infact if I go in the system settings, I can see the printer there, apparently no problem ( as you can see in screenshot: [https://www.dropbox.com/s/9njuc38ywaa6t5o/Screenshot%20from%202013-09-11%2017%3A28%3A33.png](https://www.dropbox.com/s/9njuc38ywaa6t5o/Screenshot%20from%202013-09-11%2017%3A28%3A33.png) )... 

I tried with differents usb ports, the same problem appears. And, it's not a printer issue car it works with my other PC (Xubuntu 13.04)...

If you can help me it would be very kind.

Thank you in advance and have a nice day!

---

### Post by aikishugyo on 2013-09-12
I suggest deleting the printer and adding it again. There is no information on what driver you are using, but often when the driver S/W is updated, then it is necessary to re-add the printer to CUPS.

---

### Post by dovah on 2013-12-15
I finally found a good solution: I completely removed the printer from the system, then installed the package **scangearmp**, and when running in sudo from terminal, it works both for scanning AND for printing now. 

The mysteries of the command line. :D

---

