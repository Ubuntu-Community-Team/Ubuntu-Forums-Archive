---
title: "Synaptics Mouse Driver"
date: 2005-04-07
forum: Hardware &amp; Laptops
---

### Post by 5th Order on 2005-04-07
Anyone know if there is a synaptics mouse driver for Ubuntu?

---

### Post by Technoviking on 2005-04-07
[QUOTE=5th Order]Anyone know if there is a synaptics mouse driver for Ubuntu?[/QUOTE]
Package: xorg-driver-synaptics
Synaptics TouchPad driver for X.Org server

---

### Post by daniels on 2005-04-07
It's even enabled by default on laptops.

---

### Post by blu.gecko on 2005-04-07
what is the issue, the tap function? you can fix that under etc/x11/xorg.config


device        tap     "0"

---

