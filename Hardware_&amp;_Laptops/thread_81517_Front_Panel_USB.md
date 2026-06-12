---
title: "Front Panel USB"
date: 2005-10-24
forum: Hardware &amp; Laptops
---

### Post by serzz on 2005-10-24
I've noticed strange behavior of mine front panel usb ports. When I plug my camera or usb-stick nothing happends. Same time both works fine when I connect them to usb ports on back of my pc. First ones I mentioned are connected via pins to motherboard and last ones intergated to motherboard. Do I need to do some Kernel twicking or there just some packages I need to install?

---

### Post by serzz on 2005-10-24
Found solution for a session.

$ sudo modprobe -r ehci_hcd

How can I remove it permanently?

---

### Post by funkydan2 on 2005-10-24
Add it to hotplug's blacklist : /etc/hotplug/blacklist so that it doesn't get loaded by hotplug.

---

### Post by serzz on 2005-10-24
Nou, blacklist don't keep it from loading.

---

