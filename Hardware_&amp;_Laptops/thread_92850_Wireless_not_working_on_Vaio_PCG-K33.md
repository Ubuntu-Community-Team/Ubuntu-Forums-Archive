---
title: "Wireless not working on Vaio PCG-K33"
date: 2005-11-20
forum: Hardware &amp; Laptops
---

### Post by boily on 2005-11-20
My friend has a Vaio laptop (PCG-K33) with built-in wireless card. Madwifi recognizes it, Ubuntu sees it, we got a signal of about 89%, we receive some packets, but we are unable to get the connection working.

In short, everything works, except the essential: the internet.

Also, if we boot with the card being activated, the computer freezes before starting GDM except if we boot in recovery mode. Then, we must deactivate the card in order  to get the computer working.

I don't know if it is related, but when we enter recovery mode, we get an error from Gnome saying that HAL doesn't work. More recently, ACPI too sends us an error message.

We would be very pleased to get help.

P.S.: I apologize for my bad English, it isn't my mother language.

---

### Post by caish5 on 2006-02-06
Same problem here with the freezing, although my wireless does work as long as you don't boot with it actuvated. I have a sony pcg-k17

---

### Post by beowulf on 2006-02-08
I'm crossposting this thread as it seems to be a similar issue

[http://ubuntuforums.org/showthread.php?t=126716](http://ubuntuforums.org/showthread.php?t=126716)

---

### Post by blackgecko on 2006-02-13
put this in /etc/network/interfaces

iface ath0 inet dhcp
wireless-mode managed
wireless-essid youressid
wireless-key-open yourkey
wireless-channel 11


mine is a pcg-k35 so very similar and have it working very well, mine doesnt work until y put all this things.

---

