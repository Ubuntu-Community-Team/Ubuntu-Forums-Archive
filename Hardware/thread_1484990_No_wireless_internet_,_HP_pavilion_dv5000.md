---
title: "No wireless internet , HP pavilion dv5000"
date: 2010-05-16
forum: Hardware
---

### Post by anotherrandomfellow on 2010-05-16
Hi all,

like many I have a problem with my wireless internet connection after installing Ubuntu.

If anybody could give me advice or guidance to get my wireless connection up on my HP pavilion 5000 it would be very much appreciated! :(

---

### Post by anotherrandomfellow on 2010-05-16
I have found the following information:

My card is the following...

Broadcom Corporation BCM4318 [Air Force One 54g] 802.11g Wireless LAN Controller (rev 02)


I tried installing the driver for this card from the Ubuntu install cd, as indicated (I have no internet access)...

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20BCM43xx%20drivers](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20BCM43xx%20drivers)

but it comes up with an 'error message'...I think it is already installed....


Im really really stuck! Please if you could help could you direct me....


Kind regards


Damo

---

### Post by lidex on 2010-05-18
On Ubuntu Linux  Lucid 10.04  and   Karmic 9.10 Broadcom wireless drivers are supported through System -> Administration -> Hardware Drivers

You'll want to install these packages:
```
sudo apt-get install b43-fwcutter linux-backports-modules-wireless-lucid-generic
```

This is lucid, correct?

---

### Post by gqpolo on 2010-06-03
Do you have it hooked up to a wired network? If so disconnect and press the button below the HP logo on the LCD screen...hope it helps...helped me i have the same machine

---

### Post by SyCo123 on 2010-07-08
Enabling the drive in System -> Administration -> Hardware Drivers worked for me. fwcutter gets the drivers off the net and installs them, just needed to reboot and it worked. Compared to previous efforts to get it working it really was easy.

---

