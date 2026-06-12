---
title: "ralink 3090 don't work with xubuntu 11.10"
date: 2011-10-22
forum: Hardware
---

### Post by nelsonsar on 2011-10-22
I have the same problem with 10.10 and 11.04 but with some blacklisting in modprobe it was working. Now with 11.10 version I have the same problem... Can anyone help? I have a LGP420 laptop.

Regards!

---

### Post by cottfcfan on 2011-10-24
I'm using the rt3090sta module in 11.10 & everything works fine.
I think it uses rt2800pci & rt2800lib to work, when I run lsmod.
If you have upgraded though, make sure you don't have anything blacklisted in modprobe.d, else it won't work.

---

### Post by nelsonsar on 2011-10-24
I've managed to use my wireless I'm using rt2800pci and wicd since we have a bug in network manager package.

---

