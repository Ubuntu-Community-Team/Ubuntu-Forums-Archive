---
title: "Freeze when using Lexicon Lambda USB card on 13.10"
date: 2013-10-29
forum: Hardware
---

### Post by pierre-6 on 2013-10-29
On one of my systems (haven't tested on my laptop yet) I'm getting some debilitating freezes when I use my Lexicon Lambda USB external soundcard. I've had this thing for some time now and haven't had any issues until today.

Perhaps it's a hardware combination, or perhaps it's some regression in the kernel, I'm not sure. The errors I'm getting, both when I plug the card in, and just prior to freezing, are the following:

```
Oct 29 17:02:51 media kernel: [    5.354870] 3:2:1: cannot get freq at ep 0x82
Oct 29 17:02:51 media kernel: [    5.357502] 3:2:1: cannot get freq at ep 0x82
Oct 29 17:02:51 media kernel: [    5.364494] 3:2:1: cannot get freq at ep 0x82
Oct 29 17:02:51 media kernel: [    5.366994] 3:2:1: cannot get freq at ep 0x82
Oct 29 17:02:51 media kernel: [    5.371633] 3:1:1: cannot get freq at ep 0x1
Oct 29 17:02:51 media kernel: [    5.373974] 3:1:1: cannot get freq at ep 0x1
Oct 29 17:02:51 media kernel: [    5.378111] 3:2:1: cannot get freq at ep 0x82
Oct 29 17:02:51 media kernel: [    5.380631] 3:2:1: cannot get freq at ep 0x82
Oct 29 17:02:51 media kernel: [    5.384736] 3:2:1: cannot get freq at ep 0x82
Oct 29 17:02:51 media kernel: [    5.387234] 3:2:1: cannot get freq at ep 0x82
Oct 29 17:02:51 media kernel: [    5.410720] 3:1:1: cannot get freq at ep 0x1
Oct 29 17:02:51 media kernel: [    5.413088] 3:1:1: cannot get freq at ep 0x1
Oct 29 17:02:51 media kernel: [    5.416461] 3:2:1: cannot get freq at ep 0x82
Oct 29 17:02:51 media kernel: [    5.419112] 3:2:1: cannot get freq at ep 0x82
Oct 29 17:02:51 media kernel: [    5.423596] 3:2:1: cannot get freq at ep 0x82
Oct 29 17:02:51 media kernel: [    5.426081] 3:2:1: cannot get freq at ep 0x82
Oct 29 17:02:51 media kernel: [    5.442944] 3:1:1: cannot get freq at ep 0x1
Oct 29 17:02:51 media kernel: [    5.445423] 3:1:1: cannot get freq at ep 0x1

```

I believe these are just warnings about sample rate frequencies that should be harmless, but somehow I think they are also related as I see them before every freeze (they are the last message in syslog and the freezes go away once I revert to the integrated soundcard on the motherboard.)

Any suggestions? Should I report this somewhere else? I'm not sure where to start

I tried Alsa and Jack and had the same issue. I only seemed to get the freeze in EnergyXT after about 10mins. so it may be a hardware/software combo, or even just software.

an lsusb gives:

```
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 1210:0009 DigiTech 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0bda:8172 Realtek Semiconductor Corp. RTL8191SU 802.11n WLAN Adapter
Bus 001 Device 003: ID 046d:c52e Logitech, Inc. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

syslog:

```

Oct 29 23:04:44 media kernel: [ 2105.651080] usb 3-2: new full-speed USB device number 4 using xhci_hcd
Oct 29 23:04:45 media kernel: [ 2105.728667] usb 3-2: config 1 has an invalid interface number: 6 but max is 5
Oct 29 23:04:45 media kernel: [ 2105.728672] usb 3-2: config 1 has an invalid interface number: 7 but max is 5
Oct 29 23:04:45 media kernel: [ 2105.728675] usb 3-2: config 1 has no interface number 3
Oct 29 23:04:45 media kernel: [ 2105.728677] usb 3-2: config 1 has no interface number 5
Oct 29 23:04:45 media kernel: [ 2105.742666] usb 3-2: New USB device found, idVendor=1210, idProduct=0009
Oct 29 23:04:45 media kernel: [ 2105.742671] usb 3-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Oct 29 23:04:45 media kernel: [ 2105.742673] usb 3-2: Product: Lexicon Lambda
Oct 29 23:04:45 media kernel: [ 2105.742676] usb 3-2: Manufacturer: Lexicon
Oct 29 23:04:45 media kernel: [ 2105.772609] 4:1:1: cannot get freq at ep 0x1
Oct 29 23:04:45 media kernel: [ 2105.780587] 4:1:2: cannot get freq at ep 0x1
Oct 29 23:04:45 media kernel: [ 2105.790599] 4:2:1: cannot get freq at ep 0x82
Oct 29 23:04:45 media kernel: [ 2105.799578] 4:2:2: cannot get freq at ep 0x82
Oct 29 23:04:45 media mtp-probe: checking bus 3, device 4: "/sys/devices/pci0000:00/0000:00:1c.3/0000:04:00.0/usb3/3-2"
Oct 29 23:04:45 media mtp-probe: bus: 3, device: 4 was not an MTP device
Oct 29 23:04:45 media kernel: [ 2105.872542] 4:2:1: cannot get freq at ep 0x82
Oct 29 23:04:45 media kernel: [ 2105.877536] 4:2:1: cannot get freq at ep 0x82
Oct 29 23:04:45 media kernel: [ 2105.900527] 4:1:1: cannot get freq at ep 0x1
Oct 29 23:04:45 media kernel: [ 2105.905652] 4:1:1: cannot get freq at ep 0x1
Oct 29 23:04:45 media kernel: [ 2105.913644] 4:2:1: cannot get freq at ep 0x82
Oct 29 23:04:45 media kernel: [ 2105.919657] 4:2:1: cannot get freq at ep 0x82
Oct 29 23:04:45 media kernel: [ 2105.938495] 4:1:1: cannot get freq at ep 0x1
Oct 29 23:04:45 media kernel: [ 2105.943616] 4:1:1: cannot get freq at ep 0x1
Oct 29 23:04:45 media kernel: [ 2105.952666] 4:2:1: cannot get freq at ep 0x82
Oct 29 23:04:45 media kernel: [ 2105.957636] 4:2:1: cannot get freq at ep 0x82

```

Any suggestions appreciated!

---

