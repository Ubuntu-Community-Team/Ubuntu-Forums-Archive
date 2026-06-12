---
title: "Only one usb port (out of three) is extremely slow"
date: 2009-10-10
forum: Hardware
---

### Post by Steffen' on 2009-10-10
Hi everybody.
I have a problem with one usb port of my Toshiba Satellite M40X laptop.
It is extremely slow, no matter what I connect to it: even the mouse is unusable.
The other two ports work perfectly. This problem does not show up in Windows XP (dual boot) nor it showed up in Ubuntu 8.04 (previous installation) but it did showed up in Debian Lenny (previous installation). I didn't notice any problems in the system logs.
Here's the output of lsusb:

```
stefano@stefano-laptop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c01b Logitech, Inc. MX310 Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```and an extract of lspci

```
...
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
...
```

Thanks a lot for your attention, any help would be truly appreciated

---

### Post by mehmet.ali.anil on 2011-02-08
Though this is an old thread, I am experiencing the same issue here with a netbook. Will try with other mice and report.

---

