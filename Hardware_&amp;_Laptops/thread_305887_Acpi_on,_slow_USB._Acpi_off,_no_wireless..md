---
title: "Acpi on, slow USB. Acpi off, no wireless."
date: 2006-11-24
forum: Hardware &amp; Laptops
---

### Post by Eproxus on 2006-11-24
Hi,

I'm having some trouble getting USB 2.0 to work on my laptop, a Fujitsu-Siemens A1650G. In a standard boot I cannot get USB 2.0 working with my external hard drive (resulting in unacceptable speeds of 12 Mb/s and below). When I boot with the kernel argument acpi=off I get it working. However, my wireless is now broken. So my dilemma is to either choose between fast USB or wireless network. Any idea what might be causing this?

I have a kernel module (fsam7400) which starts the software kill switch for my network card. It loads at boot and in both cases (with or without acpi) and the light for the network card lights up. It's just that without acpi the card seems to disappear, NetworkManager reports no wireless cards.

Any help appreciated.

---

### Post by Sandriman on 2006-11-24
Greetings from Finland :)

I have a Fujitsu-Siemens laptop myself, and I have a similar problem with ACPI. My solution was to opt for the "fast USB" thingy, and then use command line for accessing and using the wireless interfaces. I don't know if what you're experiencing is genuinely a bug(s), but **iwconfig** will be your friend here. It can tell you if the card is actually detected, and with it you can connect to base stations. For example, to connect to a SSID called "Sp4nk3r" with a key "password" in WEP, you can say:

Assuming your interface is called **eth1**

```

sudo iwconfig eth1 essid "Sp4nk3r"
sudo iwconfig eth1 key s:password

```

And then fetch an IP via DHCP:

```

sudo dhclient eth1

```

Hope it helps :)

---

### Post by Eproxus on 2006-11-27
Solved it!

Okay, I didn't actually bother with trying the command line tools on an invisible device (if that would have worked). And that would be no option for me anyway since I don't want to do that every time I boot or write scripts or anything (NetworkManager is your friend).

Anyway, what I did was to add ```
noapic acpi=noirq
``` to the kernel options in GRUB. This way I can have all the good stuff!

---

