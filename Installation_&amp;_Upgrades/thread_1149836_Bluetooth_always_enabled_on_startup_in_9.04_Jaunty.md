---
title: "Bluetooth always enabled on startup in 9.04 Jaunty"
date: 2009-05-05
forum: Installation &amp; Upgrades
---

### Post by Jored on 2009-05-05
I have just installed 9.04 in an HP nc6000 laptop and the internal Bluetooth adapter is always enabled on startup. The Bluetooth switch does not disable it. I have disabled Bluetooth services in System-->Preferences-->Bluetooth Services but this does not disable the internal hardware adapter and battery life is shortened.

Any ideas on how to turn the adapter off?

---

### Post by mikewhatever on 2009-05-05
You should disable bluetooth service in System->Admin->Services.

---

### Post by Jored on 2009-05-06
Done that. This, however, does not disable the Bluetooth chip on the motherboard and it keeps drawing power from the battery even when the services have been disabled.

---

### Post by mikewhatever on 2009-05-06
You are right, removing the service doesn't disable bluetooth. There are detailed instaructions on how to do it [HERE]("http://www.lesswatts.org/tips/wireless.php") (middle of the page). It also turned out that I didn't have the hci_usb module in Jaunty, but the btusb module instead. Removing btusb seems to have done the trick in my case.

---

### Post by q41 on 2009-05-09
thanks man, that helped me out ;)
the btusb module should be loaded only when you enable bluetooth, not at boot time

---

