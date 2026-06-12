---
title: "Acer Aspire 5736z Graphics Driver"
date: 2012-06-14
forum: Hardware
---

### Post by Random0o on 2012-06-14
I have an Acer Aspire 5736z-4790 and just installed ubuntu 12.04  alongside my Windows 7. However the display does not work using my  laptops screen, it does however work with an external monitor. The  graphics chip is Intel GMA 4500m part of the Mobile Intel 4 Series  Express Chipset Family. How do I fix this?

Also, my network adapter doesn't work. No driver is installed for it. I have a Broadcom 802.11n network adapter.

---

### Post by N0oki3 on 2012-06-14
> **Random0o said:**
> However the display does not work using my  laptops screen
When you boot laptop and you get purple screen, click shift. Now you should be in grub. press e and replce "quiet splash" with "nomodeset" without ""

> **Random0o said:**
> 
Also, my network adapter doesn't work. No driver is installed for it. I have a Broadcom 802.11n network adapter.

You can also try to connect to intervia cable and check in additional drivers

Read over [this](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

