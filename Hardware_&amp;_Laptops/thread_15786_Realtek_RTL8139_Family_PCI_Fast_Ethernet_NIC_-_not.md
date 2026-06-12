---
title: "Realtek RTL8139 Family PCI Fast Ethernet NIC - not recognised + dhcpcd?"
date: 2005-02-16
forum: Hardware &amp; Laptops
---

### Post by G.I.Josh on 2005-02-16
I have a **Realtek RTL8139 Family PCI Fast Ethernet** NIC, and most distrobutions have recognised it in the past.  However, I do not believe that Ubuntu has.   How do I get it to?  As a note, I read the starter and instllation guides and searched the forums for my NIC.

I typed ifconfig in the shell, and only loopback info was displayed.  eth0 wasn't even listed.  Just loopback.  I thought it had recognised it because it prompted me to autoconfigure it during installation, but I suppose that could've been for my 1394 card.  I didn't look because I assumed it was my ethernet card.

Also, dhcpcd is not installed.  Should it not be, and if so, what am I supposed to use?

Thanks,
Josh

---

### Post by G.I.Josh on 2005-02-16
My apologies.  Being tired, I left out an important detail.  

I'm connected directly to a cable modem via ethernet.

---

### Post by G.I.Josh on 2005-02-16
More information. :)  A friend told me to get relevant parts of the bootup message via :

dmesg | grep -i "eth0"

I pulled up:

eth0:  Realtek at *hex*, *more hex*, IRQ number
eth0: identified 8139 chip type "RTL - 8101"

---

