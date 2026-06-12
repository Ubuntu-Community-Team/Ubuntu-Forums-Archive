---
title: "XPS 12 9250 Bluetooth Problem After Upgrade 16.04 to 16.10"
date: 2016-11-30
forum: Hardware
---

### Post by oonid on 2016-11-30
Hello,
I have XPS 12 9250 working OK with kubuntu 16.04, I use Bluetooth mouse without any problem.
After I update via online (do-release-upgrade), then update all the package with apt upgrade,
No the computer shows Bluetooth adapter not found.

I have tried to do list with hcitool and rfkill but no device found.

here's output of: dmesg | grep -i bluetooth
```
-------
[    7.134540] Bluetooth: Core ver 2.21
[    7.134551] Bluetooth: HCI device and connection manager initialized
[    7.134554] Bluetooth: HCI socket layer initialized
[    7.134556] Bluetooth: L2CAP socket layer initialized
[    7.134561] Bluetooth: SCO socket layer initialized
[    7.156555] Bluetooth: HCI UART driver ver 2.3
[    7.156557] Bluetooth: HCI UART protocol H4 registered
[    7.156558] Bluetooth: HCI UART protocol BCSP registered
[    7.156559] Bluetooth: HCI UART protocol LL registered
[    7.156559] Bluetooth: HCI UART protocol ATH3K registered
[    7.156560] Bluetooth: HCI UART protocol Three-wire (H5) registered
[    7.156601] Bluetooth: HCI UART protocol Intel registered
[    7.156620] Bluetooth: HCI UART protocol BCM registered
[    7.156620] Bluetooth: HCI UART protocol QCA registered
[    7.156621] Bluetooth: HCI UART protocol AG6XX registered
[   20.393775] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   20.393779] Bluetooth: BNEP filters: protocol multicast
[   20.393786] Bluetooth: BNEP socket layer initialized
-------
```

any idea how to fix this without downgrade to kubuntu 16.04?

thank you for your help.

---

