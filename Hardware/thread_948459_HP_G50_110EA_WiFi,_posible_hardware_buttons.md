---
title: "HP G50 110EA WiFi, posible hardware buttons"
date: 2008-10-15
forum: Hardware
---

### Post by Nerden on 2008-10-15
Hello,
I bought a HP G50 110EA (technicaly a pavillion) it dosent seem to have been bought by anyone other than me, there are NO forums at all relating to it.

Anyhoo, i installed hardy heron, had to disable the ACPI tho, i cant get the WiFi which is an Atheros chip.

Im assuming its something to do with the hardware button which is red, in windows is blue unless i disable wifi. "iwconfig" dosent mention any wireless cards, just eth0 and l0.

This is a new laptop so im not 100% sure, first thing i did was remove windows, ill dual boot if needed.

Does anyone have any ideas as how to solve this and make my wifi work (with either madwifi or other drivers)??

Thanks for any help

---

### Post by itkeepsrepeating on 2008-12-02
> **Nerden said:**
> 

Im assuming its something to do with the hardware button which is red, in windows is blue unless i disable wifi. "iwconfig" dosent mention any wireless cards, just eth0 and l0.


There are guides that are working for some people with similar laptops, in these forums. Have a search and take your pick. 

As a headstart, I understand Vista is shutting the card off on shutdown, and *buntu doesn't know how to turn it on for some reason. Even people who got it working usually complain the light stays red, and/or connections dropping. 

Ho-hum. I'm waiting on a fix, patiently.

---

### Post by chstrig on 2009-02-20
where are the guides?

---

### Post by jamminben on 2009-03-24
I have this laptop with Ubuntu 8.10. Don't worry it is not the button. The wireless toggels on/off but the button stays brown in Ubuntu.

The issue is the card, run:

$ lspci | grep -i net

You should get something like:

Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter

It's the Atheros AR24x 802.11abg PCI that is the issue.

This forum should help you:
[http://ubuntuforums.org/showthread.php?t=967654&highlight=Atheros+AR+24](http://ubuntuforums.org/showthread.php?t=967654&highlight=Atheros+AR+24)

Just remember, you might need to switch the button.

---

