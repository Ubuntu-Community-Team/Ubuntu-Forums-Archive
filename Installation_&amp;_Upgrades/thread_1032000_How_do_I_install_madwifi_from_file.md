---
title: "How do I install madwifi from file?"
date: 2009-01-05
forum: Installation &amp; Upgrades
---

### Post by Revhead on 2009-01-05
I have installed Kubuntu Hoary 5.04 on an old Compaq Presario 1685 laptop (K63+@500, 192M RAM, 4.8GB HD, 8MB ATI RAGE LT PRO AGP 2x VGA (640x480), XGA (1024x768), SVGA (800x600), SXGA (1280x1024)

Before anyone asks I chose this distro because it wasn't up to any of the later ones I tried and because it's kinda cute. The install went well expect for the wireless pcmcia card that I got to use with it (no LAN connection).

I understand the card, the D-Link DWL G650, can be made to work using Madwifi drivers but how do I install the drivers from file.

Obviously I don't have internet access and downloaded the madwifi-9.0.4.tar.gz using another PC.

Could someone please find the time to walk me through it?

---

### Post by lemming465 on 2009-01-19
```

tar -xzf madwifi-9.0.4.tar.gz
cd madwifi-9.0.4
sudo make install
sudo reboot
```

---

