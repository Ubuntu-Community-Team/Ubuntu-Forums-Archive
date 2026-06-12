---
title: "Atheros AR8151 onboard ethernet cable for Gigabyte-Z77 UDH malfunctioning"
date: 2013-08-06
forum: Hardware
---

### Post by john_lau2 on 2013-08-06
I'm having trouble connecting to the internet on Ubuntu 13.04 with my computer. I'm using a GA-Z77 UDH motherboard that comes with an onboard Qualcomm Atheros AR8151 Ethernet card. I've spent the last 3 days trying to find a driver for it but I'm stumped. I'm not advanced programmer or an advanced Ubuntu user. If anybody can help me out, it's greatly appreciate it.

---

### Post by LinXNut on 2013-08-06
This is a tough one from what I am reading [here]("http://tuxthink.blogspot.com/2010/08/enabling-atheros-ethernet-controller-on.html"). By default, no linux systems pick up on that hardware for some reason, so you will have to "make" and install the file so it works properly.

To start, open a terminal(ctrl+alt+t) and type in....
```
lspci -v
```

This will show all your hardware modules. Copy and paste the entire thing on here in "code."

---

### Post by varunendra on 2013-08-07
Welcome to the forums john !

> **john_lau2 said:**
> I'm using a GA-Z77 UDH motherboard that comes with an onboard Qualcomm **Atheros AR8151** Ethernet card.
The network card in my laptop is the same AR8151 one, and works fantastic with "atl1c" driver which is a native one (already present in the kernel). As such, there should be no need to try any external driver.

The blog post that LinXNut referred talks about 10.04. I'm not sure whether the "atl1c" was included in it or not, but it is definitely present in 12.04 that I'm using.

To let us see your exact card ID and the driver in use (if any), please post back the output of -
```
lspci -nnk | grep -iA2 net
```

---

