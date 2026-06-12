---
title: "nonresponsive touchpad issue"
date: 2009-07-14
forum: Hardware
---

### Post by pratik_narain on 2009-07-14
Friends, I've encountered this very strange touchpad issue with my dell inspiron 1545 with ubuntu 9.04 jaunty. When I connect my mobile phone(Nokia N72) via usb cable to use it as a modem, the touchpad becomes erratic and nonreponsive as soon as I connect to the internet. It becomes so difficult to move around that I have to connect the usb mouse. Also, if it moves, the movements are erratic, like automatic clicking-dragging, double clicking etc. I searched the forums for touchpad problems and installed gsynaptics to tweak around. But it didn't work. Also, I don't have the synaptics touchpad entry in the xorg.conf file. Do I need to install synaptics device driver or is it a hardware problem and I should complain to dell. kindly help me.

update: I got a very strange result that the touchpad works fine when running on battery power. The problem occurs only when running on AC. Is it due to more power supply? or a static electricity problem. Also can I disable touchpad temporarily while typing?

Plz. help.

update: Got something more. The problem occurs only when using usb cable to connect to internet. There is no such problem using either LAN cable or bluetooth modem of the same N72 phone.

---

### Post by Orwhaleca on 2009-08-23
I don't know about any of the other problems, but you can disable the touch pad while typing with syndaemon
```
sudo syndaemon
```

---

