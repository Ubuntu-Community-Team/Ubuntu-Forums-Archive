---
title: "Printer problems Minlota Pagepro 1350w"
date: 2006-02-20
forum: Hardware &amp; Laptops
---

### Post by Inv on 2006-02-20
I'm not too optimistic about this, based on what I've read elsewhere, but has anyone been able to get a Konica Minolta Pagepro 1350 working? It is automatically recognized, and the only driver I've been able to locate (min12xxw) is installed, however nothing will print.

The printer status is stuck on: "Ready. Printer off-line."

Some help would be super; rebooting to XP just to print is getting old. :(

---

### Post by StefanPotyra on 2006-06-08
Hi,

as a workaround, you can modify /etc/cups/printers.conf and replace the old DeviceUri with:

DeviceURI file:///dev/usblp0

(and then restart cups).

More info:
[https://launchpad.net/bugs/30282](https://launchpad.net/bugs/30282)

---

### Post by Loco_gr on 2006-06-23
Great help !!
Thanks a lot Stefan !!

---

