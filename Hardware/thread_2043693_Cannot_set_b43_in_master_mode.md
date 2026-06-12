---
title: "Cannot set b43 in master mode"
date: 2012-08-17
forum: Hardware
---

### Post by azimout on 2012-08-17
I have a laptop (HP EliteBook 2540p) that contains a Broadcom B4312 (14e4:4315) LP-PHY WiFi chip. I want to set the chip in master mode (ultimate goal: an Ethernet to Wireless bridge).

I have blacklisted the Broadcom STA proprietary driver (wl.ko) and installed the firmware blobs for the open-source b43 driver (firmware-b43-lpphy-installer).

The b43 driver is supposed to support master mode:
[http://www.linuxwireless.org/en/users/Drivers/b43](http://www.linuxwireless.org/en/users/Drivers/b43)

But when I try to enable it (sudo iwconfig wlan0 mode master) I get:
Error for wireless request "Set Mode" (8B06): SET failed for device wlan0; Invalid argument.

The other modes work fine (even monitor mode, for example).

Does anyone know why this doesn't work? Is this an LP-PHY issue?

Thanks!

---

### Post by brodedra on 2012-08-17
I have had the same issue on my Dell Vostro 1310. However, the below links helped me. Give it a shot and see how it goes.

[http://askubuntu.com/questions/141423/dell-vostro-1520-wifi-not-working-with-ubuntu-12-04](http://askubuntu.com/questions/141423/dell-vostro-1520-wifi-not-working-with-ubuntu-12-04)

[http://ubuntuforums.org/showthread.php?t=1867844](http://ubuntuforums.org/showthread.php?t=1867844)

---

### Post by azimout on 2012-08-17
> **brodedra said:**
> I have had the same issue on my Dell Vostro 1310. However, the below links helped me. Give it a shot and see how it goes.

[http://askubuntu.com/questions/141423/dell-vostro-1520-wifi-not-working-with-ubuntu-12-04](http://askubuntu.com/questions/141423/dell-vostro-1520-wifi-not-working-with-ubuntu-12-04)

[http://ubuntuforums.org/showthread.php?t=1867844](http://ubuntuforums.org/showthread.php?t=1867844)

Thank you. However, these two are not what I need. Just to clarify: my WiFi works fine, I can connect to access points and all. The issue is with turning the laptop into an access point, i.e. enabling master mode.

---

### Post by unevenflow on 2012-08-17
Hey, try this
[http://www.ubuntubuzz.com/2012/06/turn-your-ubuntu-laptop-into-wireless.html](http://www.ubuntubuzz.com/2012/06/turn-your-ubuntu-laptop-into-wireless.html)

---

### Post by azimout on 2012-08-20
> **unevenflow said:**
> Hey, try this
[http://www.ubuntubuzz.com/2012/06/turn-your-ubuntu-laptop-into-wireless.html](http://www.ubuntubuzz.com/2012/06/turn-your-ubuntu-laptop-into-wireless.html)

Thanks, it's great to know that it can be done from a GUI. However, in my case I seem to be able to turn on the hotspot (infrastructure mode), but in fact my phone cannot see it.

---

