---
title: "Is it possible to turn off laptop wifi and use usb wifi adapter?"
date: 2012-05-14
forum: Hardware
---

### Post by fatski on 2012-05-14
Hi,

I have a laptop that I use as a media pc connected to my TV. Because of where it is situated in my house the Wifi signal isn't great. I have an external USB adapter I can connect with a USB cable to get better reception. However, if I turn off the hardware wifi switch on my laptop Ubuntu will not allow me to enable the USB adapter. I can leave the wifi switch turned on and disable the internal wifi in software but this setting doesn't seem to survive coming back from suspend (i.e. both wifi adapters are enabled again) and this appears to cause problems with my connection.

Anybody know if it is possible to force Ubuntu to allow me to enable the external USB adapter with the laptop wifi switch off?

Thanks

---

### Post by steeldriver on 2012-05-14
Assuming you're using NetworkManager (i.e. not configuring manually via /etc/network/interfaces or using wpa_supplicant / wpa_client) it *should* be possible to disable (technically 'unmanage') the internal card by adding

```

[keyfile]
unmanaged-devices=mac:XX:XX:XX:XX:XX:XX

```to your  /etc/NetworkManager/NetworkManager.conf, where XX:XX:XX:XX:XX:XX is the MAC of the card you want to disable. I seem to remember  the hex digits being case sensitive (only lower case worked for me).

I've used that setup (disabled internal PCI card, use external USB adapter) on a Thinkpad which had PCI bus problems that made it crash randomly with any internal card.

Apologies if that's the software fix you already tried. I don't know how to do it the way you are asking.

---

### Post by fatski on 2012-05-14
Thanks for this. All I was looking for was a way to prevent the internal wifi from re-enabling itself coming back from suspend and this achieves just that.

Cheers again for your help.

---

### Post by steeldriver on 2012-05-14
Glad it worked. Happy to help.

---

