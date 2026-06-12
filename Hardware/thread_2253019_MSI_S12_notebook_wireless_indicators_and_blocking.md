---
title: "MSI S12 notebook wireless indicators and blocking"
date: 2014-11-16
forum: Hardware
---

### Post by P_Aleksandrov on 2014-11-16
MSI S12 notebook has LED indicators which show whether WiFi or Bluetooth is on. But it seems that under Ubuntu (Lubuntu 14.10 with LXQt) these indicators are always off. For example, I turn on Bluetooth and try to find devices, but the indicator is off. Also when I turn on WiFi (sudo ifconfig wlan0 up ...), the WiFi indicator is off, but iwconfig writes "Tx-Power=20 dBm".
If I am not mistaken, this notebook has a key combination to block all radio devices (Fn+F10, an airplane is drawn on the F10 key). But this key combination doesn't works.
How can I make all this work? And is it possible to "hard" (as in "rfkill") block the radio devices?

---

