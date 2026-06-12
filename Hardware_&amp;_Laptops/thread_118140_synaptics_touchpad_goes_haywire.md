---
title: "synaptics touchpad goes haywire"
date: 2006-01-16
forum: Hardware &amp; Laptops
---

### Post by mediumcool on 2006-01-16
toshiba satellite

when in a web browser for instance, after moving from the scrollbar to the web page, the scrollbar continues to follow the mouse pointer.

works fine in a compaq which i assume has a similar synaptics touchpad.

all good apart from that, and ndiswrapper, but i have found pleanty of relevant info on that.

cheers, sean

---

### Post by prizrak on 2006-01-16
Actually Compaq has a Synaptics Touchpad and Toshiba has an ALPS Glidepoint, which are a bit different. I'm using a Satellite meself and I used this guide to get it running like I wanted it to [https://wiki.ubuntu.com/SynapticsTouchpadHowto?highlight=%28touchpad%29](https://wiki.ubuntu.com/SynapticsTouchpadHowto?highlight=%28touchpad%29) you should try that.

---

### Post by AsburyPark on 2006-01-16
give this a shot

```
sudo sh -c "echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe"
```

Then reboot:)

---

### Post by mediumcool on 2006-01-19
Thanks guys. AsburyPark, just ran that comand and rebooted, perfect! fixed :)

---

### Post by AsburyPark on 2006-01-23
[QUOTE=mediumcool]Thanks guys. AsburyPark, just ran that comand and rebooted, perfect! fixed :)[/QUOTE]

Glad to help:)

---

