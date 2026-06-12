---
title: "computer upgraded some stuff, now mouse doesn't work and computer freezes"
date: 2009-07-29
forum: Installation &amp; Upgrades
---

### Post by Meuro on 2009-07-29
Hey guys,

Earlier today Ubuntu suggested I update some packages.  I just said yes to everything and now my mouse (logitech MX1000) doesn't work and even worse, teh computer starts freezing and locking up.  

Atm I'm using a PS/2 mouse (old school ball mouse) and its not freezing.  Is there anyway to find out what programs were updated and then get things working again.  

I'm pretty new to this and any help you can give would be fantastic.  Cheers,

Meuro

---

### Post by slumbergod on 2009-07-29
Perhpas the solution on this recent thread applies to you:
[http://ubuntuforums.org/showthread.php?t=1226182](http://ubuntuforums.org/showthread.php?t=1226182)

---

### Post by Meuro on 2009-07-30
the post you've linked talks about grub errors which I don't have.  does this still apply?

---

### Post by finito on 2010-05-01
did u get it working?

---

### Post by Meuro on 2010-05-01
'fraid not finito.  Never got it working.  Just been using a standard PS/2 mouse :/

---

### Post by finito on 2010-05-01
Sux balls, well i found this, rather amusing.

[http://www.drivers.mrjuan.com/download-9222-29-mx1000-laser-cordless-mouse-linux-ubuntu-10-04-lucid-lynx.html](http://www.drivers.mrjuan.com/download-9222-29-mx1000-laser-cordless-mouse-linux-ubuntu-10-04-lucid-lynx.html)

---

### Post by finito on 2010-05-01
found the solution
[https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/550288](https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/550288)

change a line in /lib/udev/rules.d/70-hid2hci.rules

from
```

# Logitech devices
KERNEL=="hiddev*", ATTRS{idVendor}=="046d", ATTRS{idProduct}=="c70[345abce]|c71[34bc]", \
  RUN+="hid2hci --method=logitech-hid --devpath=%p"

```
to
```

KERNEL=="hidraw*", ATTRS{idVendor}=="046d", ATTRS{idProduct}=="c70[345abce]|c71[34bc]", \
  RUN+="hid2hci --method=logitech-hid --devpath=%p"

```

---

