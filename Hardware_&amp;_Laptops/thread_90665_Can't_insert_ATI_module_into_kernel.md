---
title: "Can't insert ATI module into kernel"
date: 2005-11-15
forum: Hardware &amp; Laptops
---

### Post by Ferio on 2005-11-15
I'm trying to install the ATI drivers following the instructions in Ubuntu 5.10 Guide, so I install *xorg-drivers-fglrx* and then I'm supposed to do:

```
echo fglrx | sudo tee -a /etc/modules
sudo depmod -a ; sudo modprobe fglrx
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup 
sudo sed -i -e 's/"ati"/"fglrx"/' /etc/X11/xorg.conf
```

but after the 2nd line I get:

```
FATAL: Error inserting fglrx (/lib/modules/2.6.12-9-686-smp/volatile/fglrx.ko): Operation not permitted
```

though I don't know why, what am I doing wrong?

---

