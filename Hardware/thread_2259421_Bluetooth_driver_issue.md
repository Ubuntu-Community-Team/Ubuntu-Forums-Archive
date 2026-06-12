---
title: "Bluetooth driver issue"
date: 2015-01-04
forum: Hardware
---

### Post by nickajeglin2 on 2015-01-04
Xubuntu seems to have an issue recognizing the built-in bluetooth card in my acer laptop. 

dmesg | grep Blue says:

```
[   19.722331] Bluetooth: Core ver 2.19
[   19.722372] Bluetooth: HCI device and connection manager initialized
[   19.722384] Bluetooth: HCI socket layer initialized
[   19.722387] Bluetooth: L2CAP socket layer initialized
[   19.722402] Bluetooth: SCO socket layer initialized
[   19.729746] Bluetooth: RFCOMM TTY layer initialized
[   19.729762] Bluetooth: RFCOMM socket layer initialized
[   19.729776] Bluetooth: RFCOMM ver 1.11
[   19.890202] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   19.890209] Bluetooth: BNEP filters: protocol multicast
[   19.890224] Bluetooth: BNEP socket layer initialized


```

rfkill list shows:
```
0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```
But I don't think either of those is the bluetooth device anyways.

Hardware button seems to have no effect, and hciconfig -a returns nothing.

Blueman complains that the device is not on, attemts to turn it on, then shows all controls greyed out.

lsusb just shows the hub and the built-in webcam, and lspci doesn't show anything resembling a bluetooth interface

Either there isn't a bluetooth card in the laptop despite it having a hardware button, or maybe I'm missing a driver. Any ideas?

---

### Post by jeremy31 on 2015-01-04
> **nickajeglin2 said:**
> Xubuntu seems to have an issue recognizing the built-in bluetooth card in my acer laptop. 

dmesg | grep Blue says:

```
[   19.722331] Bluetooth: Core ver 2.19
[   19.722372] Bluetooth: HCI device and connection manager initialized
[   19.722384] Bluetooth: HCI socket layer initialized
[   19.722387] Bluetooth: L2CAP socket layer initialized
[   19.722402] Bluetooth: SCO socket layer initialized
[   19.729746] Bluetooth: RFCOMM TTY layer initialized
[   19.729762] Bluetooth: RFCOMM socket layer initialized
[   19.729776] Bluetooth: RFCOMM ver 1.11
[   19.890202] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   19.890209] Bluetooth: BNEP filters: protocol multicast
[   19.890224] Bluetooth: BNEP socket layer initialized


```

rfkill list shows:
```
0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```
But I don't think either of those is the bluetooth device anyways.

Hardware button seems to have no effect, and hciconfig -a returns nothing.

Blueman complains that the device is not on, attemts to turn it on, then shows all controls greyed out.

lsusb just shows the hub and the built-in webcam, and lspci doesn't show anything resembling a bluetooth interface

Either there isn't a bluetooth card in the laptop despite it having a hardware button, or maybe I'm missing a driver. Any ideas?

Can you post the results of ```
lspci -nnk | grep -iA2 net
``` and ```
lsusb
``` anyway?
It is possible that the bluetooth device isn't labelled bluetooth or even supported by your current kernel

---

