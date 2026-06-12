---
title: "How to Reinstall Files"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by gshafer on 2009-10-30
I did an an upgrade on a virtual machine to 9.1 and something went wrong as when I reboot networking stops working. I have to manually exceute the following commands:

mkdir /var/run/network
/etc/init.d/networking start
/etc/init.d/apache2 restart

Is there a way to re-run the install to fix whatever is broken?

---

### Post by hal10000 on 2009-10-31
In the system menu go to Administration--->Services, click th unlock button and activate the services you need

---

### Post by gshafer on 2009-10-31
Whoops --- I should have mentioned I am running Ubuntu server. How do I do this from the command line?

---

### Post by hal10000 on 2009-10-31
```
sudo sysv-rc-conf
```

---

