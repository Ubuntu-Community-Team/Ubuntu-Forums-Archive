---
title: "ubuntu gutsy won't recognize new ethernet card"
date: 2007-12-03
forum: Hardware &amp; Laptops
---

### Post by Phantom784 on 2007-12-03
I installed a second ethernet card into my computer so I could use it as a bridge.  However, when typing "ifconfig", only the first, integrated ethernet device is recognised.  However, booting the live cd detects the pci and integrated ethernet, showing gutsy has the drivers, and just isn't recognising my new card plug and play.  How can I get my install to recognise this card without reinstalling?  It's a command line only install, so please give me stuff to do on the command line and not in gnome (since it doesn't have it...)

---

### Post by Phantom784 on 2007-12-03
After some googling, I realised that adding the lines "auto eth1" and "iface eth1 inet dhcp"  to /etc/network/interfaces would let the second card be recognised.  However, on my other machine, the only interface mentioned in /etc/network/interfaces is lo, making me wonder why it's not a problem on this other machine (also on gutsy) and how to make my other machine behave more automatically, without the need for having either of the physical devices listed in /etc/network/interfaces

---

