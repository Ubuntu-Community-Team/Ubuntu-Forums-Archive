---
title: "What wireless driver do I need for an MSI Wind U100?"
date: 2010-02-04
forum: Hardware
---

### Post by ryanmh on 2010-02-04
I just got an MSI Wind U100 netbook, and installed Ubuntu netbook remix on it. There were no wireless networks available in the list, so I think I may need a driver for the wireless chipset. I was thinking b43-fwcutter, but I'm not sure. Also, I have the ability to use ethernet, but what's the point of doing that on a netbook?

---

### Post by dabl on 2010-02-04
Open a terminal.

```
lspci
``` will show the devices on your PCI bus, including the ethernet chip and the wireless chip.  You need to know the wireless chip model in order to determine the driver required.  Once you know it, probably a search of this forum will reveal multiple threads where the problem has been solved before.

---

### Post by ryanmh on 2010-02-04
Ok, it says the Network controller is RaLink RT2860, what do I do now?

---

### Post by qwerty2009 on 2010-02-04
install the backport wireles driver from synaptic package manager "linux-backports-modules-wireless-karmic-generic"

---

### Post by raulito on 2010-02-12
It is strange what happended to you.
I have installed Jaunty 32bits and Karmic Netbook remix and in both OS, the wireless was installed and working fine.

---

