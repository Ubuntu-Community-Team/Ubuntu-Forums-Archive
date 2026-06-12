---
title: "Help me setting my atheros AR50007EG wireless lan"
date: 2007-12-05
forum: Hardware &amp; Laptops
---

### Post by cid_leonhart on 2007-12-05
I just bought a new Acer laptop Model 4715Z...
I already install Ubuntu 7.10 but it cannot detect my wireless lan...
my wireless lan is Atheros AR5007EG.

I already install ndsiwrapper and install windows driver for my wireless lan card and hardware status is present. so i continue to next statement:

sudo ndiswrapper -m (set wlan0 as alias to my wireless lan card)
sudo ndiswrapper -ma (write it to /etc/modprob.d/ndiswrapper)
sudo loadndisdriver

all statement executed smoothly and no error...

but when i check it with iwconfig i only get "eth0" and "lo" listed and status for both hardware is "no wireless extention"

so i check my network manager but there is only two item listed, wired network and modem. but no wireless network.

Anyone help me please...

---

