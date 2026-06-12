---
title: "Wireless Driver Installation"
date: 2008-05-05
forum: Hardware
---

### Post by Pokeh on 2008-05-05
Someone told me to download [this driver](http://sourceforge.net/forum/forum.php?forum_id=675820) to let me use my Wireless Network Card. Trouble is, I kind of don't know *how* to install it. Does anyone have any ideas?

---

### Post by Pokeh on 2008-05-05
[Just downloaded and installed this](http://www.atheros.cz/download.php?atheros=AR5007EG&system=1) (Through the Windows Wireless Drivers selection under System>>Administration).

Nothing's working, and to be honest, i'm getting a bit pissed off with Ubuntu having poor wireless support 'out-of-the-box'.

---

### Post by cwbar_1 on 2008-05-05
Please post your hardware information.  This will help!

---

### Post by Pokeh on 2008-05-06
> **cwbar_1 said:**
> Please post your hardware information.  This will help!

The wireless network card is a **Atheros 5007EG Wireless Network Adapter**. Anything else you need to know?

And sorry about the late reply.

---

### Post by ivze on 2008-05-06
Hmmm.. I have just installed another card with atheros chip (AR5212/AR5213 - lspci says), and it connected to accesspoints "out-of-the-box". 

However, to make an access point of it (for that it has been bought), i had to do some low-level things (with wlanconfig) and read man-s. The trouble is that the kernel driver does not allow switching modes (ad-hoc/Managed/Master...) without restarting the driver.

---

### Post by Pokeh on 2008-05-06
> **ivze said:**
> Hmmm.. I have just installed another card with atheros chip (AR5212/AR5213 - lspci says), and it connected to accesspoints "out-of-the-box". 

However, to make an access point of it (for that it has been bought), i had to do some low-level things (with wlanconfig) and read man-s. The trouble is that the kernel driver does not allow switching modes (ad-hoc/Managed/Master...) without restarting the driver.Well, how do you access wlanconfig anyway? The search feature doesn't bring anything up.

---

### Post by avtolle on 2008-05-06
> **Pokeh said:**
> The wireless network card is a **Atheros 5007EG Wireless Network Adapter**. Anything else you need to know?

And sorry about the late reply.
The following worked for me:
[http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html](http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html)
Have a read, maybe it's what you are looking for.

---

### Post by ivze on 2008-05-06
You need to have ```
madwifi-tools
``` package installed. You need to use native drivers, that come with Ubuntu. wlanconfig is a tool, included in the package.

---

### Post by Pokeh on 2008-05-06
Finally got it working. It turned out that I somehow had two drivers installed, and under Hardware Drivers this was causing neither of them to work properly. I disabled one of them and entered my wireless settings in to the System>>Administration>>Network box thing.

So yeah, it works now. Woo.

---

### Post by Dragon5000 on 2008-05-12
Pokeh,
How do you disable drivers?!? Still stuck in WinXP mode!
I'm running 7.10...

---

