---
title: "USB ports suddenly stopped working in 9.10 (hub_port_status failed)"
date: 2010-03-09
forum: Hardware
---

### Post by GregoryMA on 2010-03-09
My USB ports suddenly stopped working.  They do not respond to anything plugged into them.  

lsusb reads:

```
gregory@gregory-laptop:~$ lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

The relavent bits of dmesg:

```
[ 4520.742273] ehci_hcd 0000:00:13.2: port 1 reset error -110
[ 4520.742296] hub 1-0:1.0: hub_port_status failed (err = -32)
[ 4520.946266] ehci_hcd 0000:00:13.2: port 1 reset error -110
[ 4520.946289] hub 1-0:1.0: hub_port_status failed (err = -32)
[ 4521.150264] ehci_hcd 0000:00:13.2: port 1 reset error -110
[ 4521.150287] hub 1-0:1.0: hub_port_status failed (err = -32)
[ 4521.354266] ehci_hcd 0000:00:13.2: port 1 reset error -110
[ 4521.354318] hub 1-0:1.0: hub_port_status failed (err = -32)
[ 4521.558250] ehci_hcd 0000:00:13.2: port 1 reset error -110
[ 4521.558265] hub 1-0:1.0: hub_port_status failed (err = -32)
[ 4521.558272] hub 1-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[ 4521.558297] hub 1-0:1.0: unable to enumerate USB device on port 1
```

Thanks, Greg

---

### Post by GregoryMA on 2010-03-12
bump

---

### Post by GregoryMA on 2010-05-05
I eventually gave up on this and just waited out for 10.04.  I switched over and much to my chagrin I had the same problem.  I started a new thread here. [http://ubuntuforums.org/showthread.php?t=1473767](http://ubuntuforums.org/showthread.php?t=1473767)

---

