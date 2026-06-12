---
title: "USB wakeup not working"
date: 2012-04-29
forum: Hardware
---

### Post by KGigi on 2012-04-29
Hi!

I had a Kubuntu 11.04 and my keyboard waked up my computer after I echoed the USB port into /proc/acpi/wakeup. I did a clean 12.04 install and I cannot make this work. Does anyone have an idea?

```
$ cat /proc/acpi/wakeup
Device  S-state   Status   Sysfs node
PCI0      S5    *disabled  no-bus:pci0000:00
PEX0      S5    *disabled  pci:0000:00:1c.0
PEX1      S5    *disabled  pci:0000:00:1c.1
PEX2      S5    *disabled  
PEX3      S5    *disabled  pci:0000:00:1c.3
PEX4      S5    *disabled  pci:0000:00:1c.4
PEX5      S5    *disabled  pci:0000:00:1c.5
HUB0      S5    *disabled  pci:0000:00:1e.0
UAR1      S3    *disabled   pnp:00:07
USB0      S3    *enabled  pci:0000:00:1d.0
USB1      S3    *enabled  pci:0000:00:1d.1
USB2      S3    *enabled  pci:0000:00:1d.2
USB3      S3    *disabled  
US31      S3    *enabled  pci:0000:00:1a.0
USB4      S3    *enabled   pci:0000:00:1a.1
USB5      S3    *enabled  pci:0000:00:1a.2
USBE      S3    *enabled   pci:0000:00:1d.7
USE2      S3    *enabled   pci:0000:00:1a.7
AZAL      S5    *disabled

$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 046d:c521 Logitech, Inc. Cordless Mouse Receiver
Bus 004 Device 003: ID 046d:c317 Logitech, Inc. Wave Corded Keyboard

$ grep c317 /sys/bus/usb/devices/*/idProduct
/sys/bus/usb/devices/4-2/idProduct:c317

$ cat /sys/bus/usb/devices/4-2/power/wakeup
enabled
```

---

### Post by deckoff on 2012-05-28
Did someone managed to fix this - it is not working here wither

---

