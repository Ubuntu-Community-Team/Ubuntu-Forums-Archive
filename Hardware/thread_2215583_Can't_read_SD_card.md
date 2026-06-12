---
title: "Can't read SD card"
date: 2014-04-07
forum: Hardware
---

### Post by betty3 on 2014-04-07
I have a Sonny VAIO VPCCB25FX that has an SD card entry. This entry doesn't read the card neither when I insert it while the pc is running nor when I reboot with the card inside.
I've already went through the forums and tried several things but nothing has worked. Can anyone help me understand what's wrong and tell me how to fix it?

```

$ lspci | grep Ricoh

02:00.0 SD Host controller: Ricoh Co Ltd PCIe SDXC/MMC Host Controller (rev 07)
02:00.1 System peripheral: Ricoh Co Ltd Device e232 (rev 04)

```

With the card inside or outside I get :
```

$ ls -la /dev/sd*

brw-rw---- 1 root disk 8, 0 avril  7 15:26 /dev/sda
brw-rw---- 1 root disk 8, 1 avril  7 15:26 /dev/sda1
brw-rw---- 1 root disk 8, 2 avril  7 15:26 /dev/sda2
brw-rw---- 1 root disk 8, 5 avril  7 15:26 /dev/sda5

```


```
$ sudo lsusb
Bus 002 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0489:e00f Foxconn / Hon Hai Foxconn T77H114 BCM2070 [Single-Chip Bluetooth 2.1 + EDR Adapter]
Bus 001 Device 003: ID 05ca:18c0 Ricoh Co., Ltd 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```


```

$ sudo lspci -v -nn
...
02:00.0 SD Host controller [0805]: Ricoh Co Ltd PCIe SDXC/MMC Host Controller [1180:e823] (rev 07)    Subsystem: Sony Corporation Device [104d:9081]
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at f6801000 (32-bit, non-prefetchable) [size=256]
    Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [78] Power Management version 3
    Capabilities: [80] Express Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [800] Advanced Error Reporting
    Kernel driver in use: sdhci-pci


02:00.1 System peripheral [0880]: Ricoh Co Ltd Device [1180:e232] (rev 04)
    Subsystem: Sony Corporation Device [104d:9081]
    Flags: bus master, fast devsel, latency 0, IRQ 4
    Memory at f6800000 (32-bit, non-prefetchable) [size=256]
    Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [78] Power Management version 3
    Capabilities: [80] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting

```

---

### Post by tgalati4 on 2014-04-07
How many different SD cards have you tried?  Your hardware is detected.  Look inside the slot with a flashlight for a bent contact or chewing gum.

---

