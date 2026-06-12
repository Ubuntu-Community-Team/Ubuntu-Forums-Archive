---
title: "creative zen, no lsusb output"
date: 2009-01-05
forum: Hardware
---

### Post by cong06 on 2009-01-05
So I was trying to get my creative zen hooked up to amarok in my new Intrepid install, and I noticed (eventually...) that lsusb had no output for my creative:

```

Bus 005 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 152d:2338 JMicron Technology Corp. / JMicron USA Technology Corp. JM20337 Hi-Speed USB to SATA & PATA Combo Bridge
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```
That's just my wireless mouse, and external hard drive, creative zen is plugged in, but not showing.

It's obvious it's detected:
/var/log/messages:
```

Jan  5 02:30:52 dirac kernel: [ 1906.040198] usb 5-1: new full speed USB device using uhci_hcd and address 7
Jan  5 02:30:52 dirac kernel: [ 1906.248836] usb 5-1: configuration #1 chosen from 1 choice
Jan  5 02:30:54 dirac kernel: [ 1908.280257] usb 5-1: USB disconnect, address 7
```

(that's me plugging in my zen, and re-connecting it).

Where do I go from here? there's not really any documentation on what to do if your computer's not detecting your device...

---

### Post by flytripper on 2009-01-05
posted wrong info

---

### Post by cong06 on 2009-05-15
so I just noticed that if I do "sudo lsusb" I get another row:
```

Bus 005 Device 006: ID 041e:411e Creative Technology, Ltd Zen Micro
Bus 005 Device 003: ID 152d:2338 JMicron Technology Corp. / JMicron USA Technology Corp. JM20337 Hi-Speed USB to SATA & PATA Combo Bridge
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

And Gnomad2 works, if I run it as root...
But that's not going to cut it, if I want to use amarok, I can't run it as root...

---

