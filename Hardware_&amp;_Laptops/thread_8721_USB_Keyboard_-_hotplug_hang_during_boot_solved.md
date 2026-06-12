---
title: "USB Keyboard - hotplug hang during boot solved"
date: 2004-12-20
forum: Hardware &amp; Laptops
---

### Post by daKirsch on 2004-12-20
Should there be uhci AND ohci modules present? lsmod shows both in the standart configuration. Don't they both provide USB1.1? I had a problem with hotplug hanging at boot and it seems to be solved by blacklisting the ohci_hcd. The problem appeared, whenever i had my USB Keyboard plugged in at Boot. This is a Via KT400a Machine. I hope this will help anyone - it did help ME  :-D

---

### Post by matgorb on 2005-02-16
As soon as i get my linux machine back i have to try this

---

