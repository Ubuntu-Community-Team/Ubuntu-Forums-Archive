---
title: "Xubuntu installation fails"
date: 2011-03-10
forum: Hardware
---

### Post by The_Drizzt on 2011-03-10
Hi,
  I have a IBM ThinkPad A22m Computer. While installing Xubuntu 10.10 I’ll get the message “piix4_smbus 000:00:07:3 IBM system detected. This module may corrupt your serial eeprom. Refusing to load module."
  Even if I try to install Xubuntu 11.04, the installation freezes while the mouse cursor is showing up. 
  Is there any solution?
  Kind regards

---

### Post by The_Drizzt on 2011-03-10
Is there really nobody who can help me?

Regards

---

### Post by Afishionado on 2011-03-10
This post seems to explain your problem with 10.10: [http://www.lm-sensors.org/ticket/1988](http://www.lm-sensors.org/ticket/1988)

With 11.04, are you able to boot to a working desktop on the live CD without performing an install? When you get the display freeze, can you switch to another console via ctrl+alt+F1? If so, we might be able to debug from there.

You could also try out the "alternate" install disk that doesn't load a full gui. I don't know yet whether that will let you get through the install, or whether you'll be able to load a working desktop once the install completes.

Another comment: You need to be a little more patient with the forum here. I never count on getting a reply in less than 24-48 hours.

---

