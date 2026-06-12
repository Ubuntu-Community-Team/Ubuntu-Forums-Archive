---
title: "HP AIO Desktop Compatibility?"
date: 2016-01-25
forum: Hardware
---

### Post by Terence_Eden on 2016-01-25
Does anyone have experience installing Ubuntu on the latest version of the HP All In One Desktops?  (NB, I'm not talking about the AIO printer/scanners).

A few years ago [HP released a Linux compatible AIO]("http://www.omgubuntu.co.uk/2013/03/hp-launch-ubuntu-all-in-one-pc-for-349") but I can't find any information about their more recent models - e.g. [20-2320na All-in-One PC]("http://www.ebuyer.com/698079-hp-20-2320na-all-in-one-pc-l0v45ea-abu") / [ Pavilion All-in-One 23-p250na ]("http://amzn.to/1lKtwIO")

If not, any suggestions for devices with a similar form factor which will run Ubuntu?

---

### Post by Vladlenin5000 on 2016-01-25
The form factor is irrelevant, the hardware inside is what matters. That said, at a quick glance over the specs, I don't foresee complications. The only component that may require some action is the integrated WiFi.

---

### Post by Terence_Eden on 2016-01-26
The form factor is not irrelevant to me - that's the sort of machine I'm after :-)

 What do you mean by the wifi "may require some action"?

---

### Post by Vladlenin5000 on 2016-01-26
Regarding hardware support it's the hardware itself that matters, not how it's "packaged" (traditional desktop, AIO, notebook, miniPC box or stick, ...).
The one you linked in the OP, regardless of the OS bundled, has pretty standard hardware known to work out-of-the-box with Ubuntu except, perhaps, the WiFi which might need additional drivers and/or tweaks.

Checking the drivers download section at HP, the options for 20-2320na show Atheros AR9000 series (natively supported), Realtek RTL8723BE (may require different driver) and Realtek RTL8188EE (idem).
For 23-p250na the same three options plus an unspecified Broadcom which may or may not be problematic.

---

