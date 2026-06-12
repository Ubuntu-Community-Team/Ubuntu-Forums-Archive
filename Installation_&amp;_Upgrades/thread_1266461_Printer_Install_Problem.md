---
title: "Printer Install Problem"
date: 2009-09-14
forum: Installation &amp; Upgrades
---

### Post by Marzipan1 on 2009-09-14
Hello, i m trying to install a network printer after getting the right driver and installing them on the system i get following error (also shown in the screenshot) idle - /usr/lib/cups/backend/lpd failed.

Any ideas how to fix that ?

---

### Post by cariboo on 2009-09-14
Usually you only need lpd when the printer is connected directly to your computer. For connecting to a networked printer I use ipp. eg:

```
ipp://192.168.1.250:631/printers/HPLaserjet
```

My printer is connected to my server, but if it is a stand alone networked printer just use the ipp and the network address.

I always use the cups interface:

[http://localhost:631](http://localhost:631)

to set up my printers.

---

