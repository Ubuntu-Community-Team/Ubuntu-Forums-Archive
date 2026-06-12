---
title: "Unable to connect to wpa2 wireless"
date: 2009-04-27
forum: Hardware
---

### Post by rohitvg on 2009-04-27
Hi all,

I am using a Dell Inspiron 5100 with Broadcom Wireless.
I am using the b43-fwcutter for the driver and it does work and I am able to see all the network and also connect to the unsecured ones.
though I am not able to connect to any wpa2 secure network. Is there anything that I can do?

Here are a little more details on my hardware:
02:01.0 Ethernet controller [0200]: Broadcom Corporation BCM4401 100Base-T [14e4:4401] (rev 01)
02:02.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 02)

I am using the latest version of b43-fwcutter as of today (24 April 2009).
Also the wpa2 supplicant package is installed. 

I am not sure if this is a bug or it is a problem  I am facing. 

Any help from your side would be greatly appreciated.

Thanks!

---

### Post by sb92075 on 2009-04-27
[http://ubuntuforums.org/showthread.php?t=202834&highlight=AR242x](http://ubuntuforums.org/showthread.php?t=202834&highlight=AR242x)

---

### Post by stchman on 2009-04-27
> **rohitvg said:**
> Hi all,

I am using a Dell Inspiron 5100 with Broadcom Wireless.
I am using the b43-fwcutter for the driver and it does work and I am able to see all the network and also connect to the unsecured ones.
though I am not able to connect to any wpa2 secure network. Is there anything that I can do?

Here are a little more details on my hardware:
02:01.0 Ethernet controller [0200]: Broadcom Corporation BCM4401 100Base-T [14e4:4401] (rev 01)
02:02.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 02)

I am using the latest version of b43-fwcutter as of today (24 April 2009).
Also the wpa2 supplicant package is installed. 

I am not sure if this is a bug or it is a problem  I am facing. 

Any help from your side would be greatly appreciated.

Thanks!

I don't think the 4306 Broadcom chipset supports WPA2.

---

