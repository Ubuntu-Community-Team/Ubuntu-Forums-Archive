---
title: "VIA chipset USB 3.0 not working"
date: 2014-11-16
forum: Hardware
---

### Post by Rishin_Goswami on 2014-11-16
The xhci driver doesn't work properly for the USB 3.0 chipset I have. USB 2.0 is working fine and I can manage without USB 3. However I was jsut wondering if there's a solution at all. Logs below.


```
rishin@morpheus:~$ uname -a
Linux morpheus 3.13.0-39-generic #66-Ubuntu SMP Tue Oct 28 13:30:27 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
rishin@morpheus:~$ 
rishin@morpheus:~$ lspci | grep VIA
02:00.0 USB controller: VIA Technologies, Inc. Device 3483 (rev 01)
03:00.0 USB controller: VIA Technologies, Inc. Device 3483 (rev 01)
rishin@morpheus:~$ 
rishin@morpheus:~$ dmesg | grep -i xhci
[    1.132156] xhci_hcd 0000:02:00.0: xHCI Host Controller
[    1.132160] xhci_hcd 0000:02:00.0: new USB bus registered, assigned bus number 8
[    1.132298] xhci_hcd 0000:02:00.0: irq 73 for MSI/MSI-X
[    1.132349] usb usb8: Product: xHCI Host Controller
[    1.132351] usb usb8: Manufacturer: Linux 3.13.0-39-generic xhci_hcd
[    1.132511] xhci_hcd 0000:02:00.0: xHCI Host Controller
[    1.132514] xhci_hcd 0000:02:00.0: new USB bus registered, assigned bus number 9
[    1.132559] usb usb9: Product: xHCI Host Controller
[    1.132560] usb usb9: Manufacturer: Linux 3.13.0-39-generic xhci_hcd
[    1.148022] xhci_hcd 0000:03:00.0: xHCI Host Controller
[    1.148028] xhci_hcd 0000:03:00.0: new USB bus registered, assigned bus number 10
[    1.148164] xhci_hcd 0000:03:00.0: irq 74 for MSI/MSI-X
[    1.148221] usb usb10: Product: xHCI Host Controller
[    1.148222] usb usb10: Manufacturer: Linux 3.13.0-39-generic xhci_hcd
[    1.148373] xhci_hcd 0000:03:00.0: xHCI Host Controller
[    1.148376] xhci_hcd 0000:03:00.0: new USB bus registered, assigned bus number 11
[    1.148411] usb usb11: Product: xHCI Host Controller
[    1.148412] usb usb11: Manufacturer: Linux 3.13.0-39-generic xhci_hcd
[    2.802158] usb 8-1: new high-speed USB device number 2 using xhci_hcd
[    7.809645] xhci_hcd 0000:02:00.0: Timeout while waiting for address device command
[   16.182449] xhci_hcd 0000:02:00.0: Stopped the command ring failed, maybe the host is dead
[   16.209247] xhci_hcd 0000:02:00.0: Host not halted after 16000 microseconds.
[   16.209248] xhci_hcd 0000:02:00.0: Abort command ring failed
[   16.209274] xhci_hcd 0000:02:00.0: HC died; cleaning up
[   21.417704] xhci_hcd 0000:02:00.0: Timeout while waiting for address device command
[   21.417712] xhci_hcd 0000:02:00.0: Abort the command ring, but the xHCI is dead.
[   26.629458] xhci_hcd 0000:02:00.0: Timeout while waiting for a slot
[   26.629466] xhci_hcd 0000:02:00.0: Abort the command ring, but the xHCI is dead.
[   31.636798] xhci_hcd 0000:02:00.0: Timeout while waiting for a slot
[   31.636806] xhci_hcd 0000:02:00.0: Abort the command ring, but the xHCI is dead.
[   36.644194] xhci_hcd 0000:02:00.0: Timeout while waiting for a slot
[   36.644202] xhci_hcd 0000:02:00.0: Abort the command ring, but the xHCI is dead.
[   36.756438] usb 10-1: new high-speed USB device number 2 using xhci_hcd
[   41.763748] xhci_hcd 0000:03:00.0: Timeout while waiting for address device command
[   50.141287] xhci_hcd 0000:03:00.0: Stopped the command ring failed, maybe the host is dead
[   50.168058] xhci_hcd 0000:03:00.0: Host not halted after 16000 microseconds.
[   50.168060] xhci_hcd 0000:03:00.0: Abort command ring failed
[   50.168134] xhci_hcd 0000:03:00.0: HC died; cleaning up
[   55.378923] xhci_hcd 0000:03:00.0: Timeout while waiting for address device command
[   55.378928] xhci_hcd 0000:03:00.0: Abort the command ring, but the xHCI is dead.
[   60.590669] xhci_hcd 0000:03:00.0: Timeout while waiting for a slot
[   60.590673] xhci_hcd 0000:03:00.0: Abort the command ring, but the xHCI is dead.
[   65.598020] xhci_hcd 0000:03:00.0: Timeout while waiting for a slot
[   65.598029] xhci_hcd 0000:03:00.0: Abort the command ring, but the xHCI is dead.
[   70.605410] xhci_hcd 0000:03:00.0: Timeout while waiting for a slot
[   70.605414] xhci_hcd 0000:03:00.0: Abort the command ring, but the xHCI is dead.

```

Details of the USB 3 controllers:

```
02:00.0 USB controller: VIA Technologies, Inc. Device 3483 (rev 01) (prog-if 30 [XHCI])
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device 7693
    Flags: bus master, fast devsel, latency 0, IRQ 73
    Memory at fe800000 (64-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: xhci_hcd

03:00.0 USB controller: VIA Technologies, Inc. Device 3483 (rev 01) (prog-if 30 [XHCI])
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device 7693
    Flags: bus master, fast devsel, latency 0, IRQ 74
    Memory at fe700000 (64-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: xhci_hcd

```

And the IOMMU related logs:

```
rishin@morpheus:~$ dmesg | egrep -i "iommu|amd-vi"
[    0.000000] Please enable the IOMMU option in the BIOS setup
[    0.711080] AMD-Vi: Found IOMMU at 0000:00:00.2 cap 0x40
[    0.711083] AMD-Vi: Interrupt remapping enabled
[    0.721322] AMD-Vi: Lazy IO/TLB flushing enabled
[    1.134945] AMD-Vi: Event logged [IO_PAGE_FAULT device=02:00.0 domain=0x0015 address=0x000000010000e000 flags=0x0030]
[    1.134954] AMD-Vi: Event logged [IO_PAGE_FAULT device=02:00.0 domain=0x0015 address=0x000000010000e040 flags=0x0030]
[    1.134960] AMD-Vi: Event logged [IO_PAGE_FAULT device=02:00.0 domain=0x0015 address=0x000000010000e080 flags=0x0030]
...
...
...
[    1.150850] AMD-Vi: Event logged [IO_PAGE_FAULT device=03:00.0 domain=0x0016 address=0x000000010000e000 flags=0x0030]
[    1.150859] AMD-Vi: Event logged [IO_PAGE_FAULT device=03:00.0 domain=0x0016 address=0x000000010000e040 flags=0x0030]
[    1.150864] AMD-Vi: Event logged [IO_PAGE_FAULT device=03:00.0 domain=0x0016 address=0x000000010000e080 flags=0x0030]
[    1.150868] AMD-Vi: Event logged [IO_PAGE_FAULT device=03:00.0 domain=0x0016 address=0x000000010000e0c0 flags=0x0030]
...
...
...
[   16.553493] AMD IOMMUv2 driver by Joerg Roedel <joerg.roedel@amd.com>
[   16.553496] AMD IOMMUv2 functionality not available on this system
[   16.575590] <6>[fglrx] IOMMU is enabled, CrossFire are not supported on this platform
[   16.575593] <6>[fglrx] Disable IOMMU in BIOS options or kernel boot parameters to support CF

```

---

