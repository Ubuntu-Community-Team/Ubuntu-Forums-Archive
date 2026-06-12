---
title: "Wired Network Adapter not starting in Kubuntu"
date: 2010-06-18
forum: Hardware
---

### Post by leithon on 2010-06-18
Hi all!

I've an issue with kubuntu lucid lynx 64bit, I've installed some updates but now, after booting I see the ethernet card off, I use a router and a xDSL connection. The router does not recognize any interface in the line that I plug my laptop.

The card is Marvell, running in a HP Probook 4411s

Any ideas?

Thank you!

---

### Post by leithon on 2010-06-19
Additional information: Network manager appears as not managed, but I changed managed to true in 
/etc/NetworkManager/nm-system-settings.conf

And also I added NetworkingEnabled=true.

But it does not work yet. At least now, the green light in the ethernet card is on, and the NM icon does not say: unmanaged, it just says: not connected. But there is no any connection problem, since I restart and boot in another OS and it works perfectly.

Thank you for your suggestions.

---

### Post by leithon on 2010-06-24
solved installing  wicd!

---

