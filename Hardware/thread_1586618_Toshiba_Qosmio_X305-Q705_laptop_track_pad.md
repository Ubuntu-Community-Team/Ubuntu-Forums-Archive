---
title: "Toshiba Qosmio X305-Q705 laptop track pad"
date: 2010-10-02
forum: Hardware
---

### Post by mikelaurenzana on 2010-10-02
HI there.

I recently installed Ubuntu 10.4 64bit on my Toshiba Qosmio X305-Q705 laptop. I booted it up and the track pad mouse along with the right and left click buttons were not working. I since have been forced to use a USB mouse. If anyone can help me with this problem I would appreciate it.

Thanks.
-Mike

---

### Post by mikelaurenzana on 2010-10-03
bump

---

### Post by P4man on 2010-10-03
Can you open a terminal and type in these two commands:
```

lspci
lsusb
```

Copy paste the output here. That will show us exactly what hardware you have.

It might also help me to boot the laptop without the USB mouse, only connect it when you need it, and then attach the output of dmesg. This will be too large to copy/paste, so save the output to a file. 

```
dmesg > dmesg.txt
```

Attach that file here.

---

### Post by mikelaurenzana on 2010-10-03
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 003: ID 093a:2510 Pixart Imaging, Inc. Hama Optical Mouse
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 04f2:b008 Chicony Electronics Co., Ltd USB 2.0 Camera
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by P4man on 2010-10-03
Thats only USB, there is no touchpad in there. Can you post lspci and perhaps dmesg as well?

---

### Post by mikelaurenzana on 2010-10-07
The latest update for Ubuntu took care of it. Thanks for the help though.

---

