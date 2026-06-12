---
title: "usb printer missing after upgrade 14.04 to 16.04"
date: 2017-02-12
forum: Hardware
---

### Post by whoop on 2017-02-12
My canon PIXMA MP210 is not regestering on my server anymore after an upgrade to the latest LTS server

lusb output shows no printer:
```

# lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

syslog tails:
```

Feb 12 22:45:17 ubuserver kernel: [78394.602798] ehci-pci 0000:00:13.2: port 8 reset error -110
Feb 12 22:45:18 ubuserver kernel: [78395.478800] ehci-pci 0000:00:13.2: port 8 reset error -110
Feb 12 22:45:19 ubuserver kernel: [78396.298799] ehci-pci 0000:00:13.2: port 8 reset error -110
Feb 12 22:45:20 ubuserver kernel: [78397.122790] ehci-pci 0000:00:13.2: port 8 reset error -110
Feb 12 22:45:21 ubuserver kernel: [78397.942786] ehci-pci 0000:00:13.2: port 8 reset error -110
Feb 12 22:45:21 ubuserver kernel: [78398.556058] hub 1-0:1.0: Cannot enable port 8.  Maybe the USB cable is bad?
Feb 12 22:45:21 ubuserver kernel: [78398.558164] hub 1-0:1.0: unable to enumerate USB device on port 8

```

The printer is found on a test laptop with same cable so I do not think the cable is bad. Also tried different ports of the server.
Any ideas?

---

