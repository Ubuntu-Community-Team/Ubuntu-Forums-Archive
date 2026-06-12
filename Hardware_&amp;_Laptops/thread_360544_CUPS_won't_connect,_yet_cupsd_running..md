---
title: "CUPS won't connect, yet cupsd running."
date: 2007-02-13
forum: Hardware &amp; Laptops
---

### Post by sputnik2012 on 2007-02-13
Hi All.

I'm running cups from a default install of edgy.  ps -ax indicated cupsys daemon is running, /etc/init.d/cupsys status also confirms this. lpstat produeces the following message:> Unable to connect to server.  Connections to localhost:163 are rejected.

nothing is being reported in the logs (/var/log/cups/error.log) where can I find more information about the process?  Are there any other daemons I need to configure and does the presence of cups-bsd in my packages intefere with cups?

The printing utility accessed by System -> Preferences replies that it can't connect to the cups server.

Thanks,
       Rob.

Ps. not using a firewall, kernel using netfilter

---

### Post by ozp on 2007-02-15
I have the same problem on a 6.06 box

---

