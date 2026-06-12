---
title: "Acer Travelmate 4060 Bluetooth issue"
date: 2009-06-24
forum: Hardware
---

### Post by Dysport on 2009-06-24
Hi everyone!

I was wondering whether someone was able to get bluetooth on the Acer Travelmate 4060 up and running? I have done some searching in the forums and Google but turned up with no useable results. I hoped that the problem might resolve with an update to Jaunty, but still no blue "B" in my gnome-panel :(

Here is the output of *dmesg | grep Bluetooth*
```
[    0.567238] Bluetooth: Core ver 2.13
[    0.567238] Bluetooth: HCI device and connection manager initialized
[    0.567238] Bluetooth: HCI socket layer initialized
[    2.115435] Bluetooth: L2CAP ver 2.11
[    2.115437] Bluetooth: L2CAP socket layer initialized
[    2.115440] Bluetooth: SCO (Voice Link) ver 0.6
[    2.115442] Bluetooth: SCO socket layer initialized
[    2.115464] Bluetooth: RFCOMM socket layer initialized
[    2.115471] Bluetooth: RFCOMM TTY layer initialized
[    2.115473] Bluetooth: RFCOMM ver 1.10
[   29.042417] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   29.042422] Bluetooth: BNEP filters: protocol multicast

```

any suggestions?

---

### Post by lorenzo_de_tomasi on 2009-10-02
I have the same problem.
Here's the output of my dmesg | grep Bluetooth
[    0.572507] Bluetooth: Core ver 2.13
[    0.572507] Bluetooth: HCI device and connection manager initialized
[    0.572507] Bluetooth: HCI socket layer initialized
[    2.129763] Bluetooth: L2CAP ver 2.11
[    2.129765] Bluetooth: L2CAP socket layer initialized
[    2.129768] Bluetooth: SCO (Voice Link) ver 0.6
[    2.129769] Bluetooth: SCO socket layer initialized
[    2.129791] Bluetooth: RFCOMM socket layer initialized
[    2.129799] Bluetooth: RFCOMM TTY layer initialized
[    2.129801] Bluetooth: RFCOMM ver 1.10
[   20.391941] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   20.391944] Bluetooth: BNEP filters: protocol multicast

Thanks

---

### Post by lorenzo_de_tomasi on 2009-11-09
Same problem here.

$ dmesg | grep Bluetooth
[    0.401978] Bluetooth: Core ver 2.15
[    0.402008] Bluetooth: HCI device and connection manager initialized
[    0.402011] Bluetooth: HCI socket layer initialized
[    1.206750] Bluetooth: L2CAP ver 2.13
[    1.206752] Bluetooth: L2CAP socket layer initialized
[    1.206757] Bluetooth: SCO (Voice Link) ver 0.6
[    1.206759] Bluetooth: SCO socket layer initialized
[    1.206791] Bluetooth: RFCOMM TTY layer initialized
[    1.206794] Bluetooth: RFCOMM socket layer initialized
[    1.206796] Bluetooth: RFCOMM ver 1.11

---

### Post by chessboxing on 2009-11-10
```
[    1.251153] Bluetooth: L2CAP ver 2.13
[    1.251158] Bluetooth: L2CAP socket layer initialized
[    1.251164] Bluetooth: SCO (Voice Link) ver 0.6
[    1.251168] Bluetooth: SCO socket layer initialized
[    1.251270] Bluetooth: RFCOMM TTY layer initialized
[    1.251277] Bluetooth: RFCOMM socket layer initialized
[    1.251282] Bluetooth: RFCOMM ver 1.11

```
no icon either here on my compaq mini 110. Pls help

---

