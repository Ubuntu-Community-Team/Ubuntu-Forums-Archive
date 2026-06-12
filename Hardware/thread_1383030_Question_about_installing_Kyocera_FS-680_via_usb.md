---
title: "Question about installing Kyocera FS-680 via usb"
date: 2010-01-16
forum: Hardware
---

### Post by djslimer on 2010-01-16
Hi,

I need your help.
A friend of mine uses kubuntu 9.10 with the current update 2.6.17. He also has an old Kyocera FS-680 printer, connected to the notebook via a USB2Parallell cable.

Since he has switched to kubuntu, we aren't able to get the printer working.

The printer is connected and switched on, the drivers are installed. Neither Cups (1.4) nor usb-deamon get notice from the printer.

```

john@Immobilium:~$ lsusb
Bus 003 Device 002: ID 04d9:a015 Holtek Semiconductor, Inc.
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0424:2502 Standard Microsystems Corp.
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


john@Immobilium:~$ lpinfo -v
direct scsi
direct parallel:/dev/lp0
network socket
network http
serial serial:/dev/ttyS0?baud=115200
network smb
network beh
network ipp
network lpd
direct hp
direct hpfax

```

It seems so, that the connection between PC and printer is somehow corrupted. Do someone know, what I can do?


One problem I have is, what the URI should be. I think, if the printer would be connected to parallel, the uri should be: parallel:/dev/usb, and if it is connected to usb, the URI would look something like this: usb:/dev/usb/lp0.
Is this correct? Certainly, it depends on the value printed by "lpinfo -v". 
There is listed a parallel port on the list above, that's why I'm testing on my PC and I do have a parallel port, in contrary to the laptop of the friend of mine.

So, can you help me to get the printer working?

I offer this bag :popcorn: ;)

---

### Post by gordintoronto on 2010-01-16
> **djslimer said:**
> 
The printer is connected and switched on...
```

john@Immobilium:~$ lsusb
Bus 003 Device 002: ID 04d9:a015 Holtek Semiconductor, Inc.
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0424:2502 Standard Microsystems Corp.
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
It seems so, that the connection between PC and printer is somehow corrupted. Do someone know, what I can do?


Remove spaghetti, replace with actual USB cable.  [smile]  Or plug the cable in properly.

---

### Post by djslimer on 2010-01-17
it is pluged in properly.

---

### Post by djslimer on 2010-01-19
Anyone there, who has any ideas?

---

