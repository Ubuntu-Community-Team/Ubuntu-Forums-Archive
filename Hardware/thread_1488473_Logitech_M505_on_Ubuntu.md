---
title: "Logitech M505 on Ubuntu"
date: 2010-05-20
forum: Hardware
---

### Post by A.S. on 2010-05-20
Hello,

does anybody know, if the Logitech M505 mouse is working on Ubuntu?

---

### Post by eurik on 2010-05-20
mine doesn't, or ti does, but causes system freezes :(

---

### Post by efflandt on 2010-05-20
I do not have that mouse, but you might try one or both of the following and confirm if it helps or not.  Either resolved issues with my Logitech diNovo Edge keyboard/mousepad.

Use sudo (or gksu) with your favorite editor to edit **/lib/udev/rules.d/70-hid2hci.rules**

```
# Logitech devices
KERNEL=="hiddev*", ATTRS{idVendor}=="046d", ATTRS{idProduct}=="c70[345abce]|c71[34bc]", \
  RUN+="hid2hci --method=logitech-hid --devpath=%p"
```Change "hiddev*" to "hidraw*" or try just commenting out those 2 lines like this:

```
# Logitech devices
#KERNEL=="hiddev*", ATTRS{idVendor}=="046d", ATTRS{idProduct}=="c70[345abce]|c71[34bc]", \
#  RUN+="hid2hci --method=logitech-hid --devpath=%p"
```Unplug your USB dongle, plug it back in, and see if it works.  If you played around trying to associate them when it was not working, you might need to reassociate the dongle and mouse.

---

### Post by A.S. on 2010-05-21
Hello,

I'd posted the question before I've tried if the mouse is working or not because I wanted to know if I could buy this mouse or not.

So, now I've bought the mouse and it still works on Kubuntu 10.04. There was nothing to do.

---

