---
title: "Bluetooth on Feisty Problem"
date: 2007-06-21
forum: Hardware &amp; Laptops
---

### Post by CitizenKane on 2007-06-21
Hello Everyone,
I have been trying to get my bluetooth dongle to connect to my cellphone on Feisty.  If i do

```

hcitool cc [bluetoothpin]

```

it will connect briefly but then disconnect.  I have an LG-VX5300 and the bluetooth has worked fine with other computers.  I have attached my hcid.conf and rfcomm.conf.  Any help would be appreciated.

---

### Post by CitizenKane on 2007-06-22
Any help is appreciated.

---

### Post by kpkeerthi on 2007-06-22
Switch to Channel 10 in rfcomm.conf and see if it helps. Make sure you restart bluetooth.

---

