---
title: "External USB hard drive (through JMicron  JM20337) does not work"
date: 2014-01-03
forum: Hardware
---

### Post by campospinto on 2014-01-03
External USB hard drive (through JMicron Technology Corp. USA. JM20337) does not work

I'm trying to install an external HD, but Ubuntu 13.10 fresh install, updated yesterday, does not see the HD.
In Ubuntu Forun found similar problems, and used the lsusb command, connected the hd to the USB port and again sudo lsusb, the new device has emerged, but stopped there, no progress.
The machine I'm using to external hd has ports for SATA and IDE (normal ide and notebook uses an external power source).
The results of the terminal are also being sent.
Is there something that can be done to the external hd function similar to Windows XP or more so?
Thank you.

João Alfredo
  "post translated by Google Translate"

joao@DC7600:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 045e:00cb Microsoft Corp. Basic Optical Mouse v2.0
Bus 004 Device 002: ID 03f0:0024 Hewlett-Packard KU-0316 Keyboard
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
joao@DC7600:~$ sudo lsusb
Bus 001 Device 006: ID 152d:2338 JMicron Technology Corp. / JMicron USA Technology Corp. JM20337 Hi-Speed USB to SATA & PATA Combo Bridge
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 045e:00cb Microsoft Corp. Basic Optical Mouse v2.0
Bus 004 Device 002: ID 03f0:0024 Hewlett-Packard KU-0316 Keyboard
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by campospinto on 2014-01-04
No more problems, solved
thanks

---

### Post by andresfbl on 2014-05-20
Hi campospinto, I have the exact same problem. Could you let me know how you solved it?

Thanks

---

