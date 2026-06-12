---
title: "Can't get HSO Option Globetrotter 515 to work on Orange Switzerland"
date: 2010-12-06
forum: Hardware
---

### Post by piquadrat on 2010-12-06
Hi,

I bought a HSO Globetrotter 515m from Orange Switzerland. Network Manager recognizes the device and I'm able to configure my provider (Orange Switzerland) and my plan (Orange Internet Everywhere). When I try to connect, Network Manager errors out after a couple of seconds, saying "GSM - disconnected". In /var/log/daemon.log, I find this:

```
Dec  6 14:21:26 T400 modem-manager: (Option High-Speed): GSM modem /sys/devices/pci0000:00/0000:00:1a.7/usb1/1-1 claimed port hso0
Dec  6 14:21:26 T400 NetworkManager[1070]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1a.7/usb1/1-1/1-1:1.3/net/hso0, iface: hso0)
Dec  6 14:21:26 T400 NetworkManager[1070]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1a.7/usb1/1-1/1-1:1.3/net/hso0, iface: hso0): no ifupdown configuration found.
Dec  6 14:21:33 T400 modem-manager: (/org/freedesktop/ModemManager/Modems/0): data port is hso0
Dec  6 14:21:34 T400 NetworkManager[1070]: <info> (hso0): new GSM device (driver: 'hso' ifindex: 3)
Dec  6 14:21:34 T400 NetworkManager[1070]: <info> (hso0): exported as /org/freedesktop/NetworkManager/Devices/2
Dec  6 14:21:34 T400 NetworkManager[1070]: <info> (hso0): now managed
Dec  6 14:21:34 T400 NetworkManager[1070]: <info> (hso0): device state change: 1 -> 2 (reason 2)
Dec  6 14:21:34 T400 NetworkManager[1070]: <info> (hso0): deactivating device (reason: 2).
Dec  6 14:21:34 T400 NetworkManager[1070]: <info> (hso0): device state change: 2 -> 3 (reason 0)
Dec  6 14:24:51 T400 NetworkManager[1070]: <info> Activation (hso0) starting connection 'Orange Internet Everywhere'
Dec  6 14:24:51 T400 NetworkManager[1070]: <info> (hso0): device state change: 3 -> 4 (reason 0)
Dec  6 14:24:51 T400 NetworkManager[1070]: <info> Activation (hso0) Stage 1 of 5 (Device Prepare) scheduled...
Dec  6 14:24:51 T400 NetworkManager[1070]: <info> Activation (hso0) Stage 1 of 5 (Device Prepare) started...
Dec  6 14:24:51 T400 NetworkManager[1070]: <info> Activation (hso0) Stage 1 of 5 (Device Prepare) complete.
Dec  6 14:25:06 T400 NetworkManager[1070]: <info> (hso0): device state change: 4 -> 9 (reason 1)
Dec  6 14:25:06 T400 NetworkManager[1070]: <warn> Activation (hso0) failed.
Dec  6 14:25:06 T400 NetworkManager[1070]: <info> (hso0): device state change: 9 -> 3 (reason 0)
Dec  6 14:25:06 T400 NetworkManager[1070]: <info> (hso0): deactivating device (reason: 0).
```

I followed all the tutorials on HSO 5x5 devices here (although most of them seem outdated and targeted on Ubuntu 9.10 or 10.4), but nothing helped. What am I doing wrong?

---

