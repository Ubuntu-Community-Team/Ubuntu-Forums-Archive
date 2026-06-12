---
title: "Connection interruption problem with USB Wireless Adapter"
date: 2009-05-14
forum: Hardware
---

### Post by malic on 2009-05-14
Hello;

I have an USB Wireless Adapter that is not recognized by Ubuntu. So I installed it using windows driver through ndiswrapper as in below.

```

sudo ndiswrapper -i .../driver.INF
sudo depmod -a
sudo modprobe ndiswrapper

```

Then I added the line "sudo modprobe ndiswrapper" into the "/etc/rc.local" file.

Internet connection interrupts for every five minutes. The same wireless adapter works properly on Slackware Box through ndiswrapper. What is the problem with Ubuntu? Do you have an idea?

Thanks...

([USB Wireless Adapter: Airties WUS-300]("http://www.airties.com/product-details.asp?id=11&pn=WUS-300&ci=12&dil=eng"))

---

### Post by malic on 2009-05-17
I have solved my problem (originated from WPA2 encryption) replacing "GNOME Network Manager" with "Wicd". "Ndiswrapper- WPA2 Encryption-GNOME Network Manager" does not work but "Ndiswrapper- WPA2 Encryption-Wicd" works :)
Thanks for your deal.

---

### Post by popat007 on 2009-07-24
Thanks @malic i do have this adapter will try out.
Is it possible to install another driver like DHP-50U dlink VOIP driver which lacks linux driver.

---

