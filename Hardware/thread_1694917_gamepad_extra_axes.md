---
title: "gamepad extra axes"
date: 2011-02-25
forum: Hardware
---

### Post by anmelegov on 2011-02-25
There is a gamepad Speedlink Strike. The problem is that the system thinks that he has seven axles (it has 6) and on axis 2 always is a signal .... remaining axes are working fine ... How to disable the extra axle?

lsusb
```
Bus 002 Device 014: ID 0079:0006 DragonRise Inc. Generic USB Joystick
```

jstest
```
Axes:  0:     0  1:     0  2:-32767  3:     0  4:     0  5:     0  6:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:off 10:off 11:off
Axes:  0:     0  1:     0  2:     0  3:     0  4:     0  5:     0  6:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:off 10:off 11:off
Axes:  0:     0  1:     0  2:-32767  3:     0  4:     0  5:     0  6:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:off 10:off 11:off
Axes:  0:     0  1:     0  2:     0  3:     0  4:     0  5:     0  6:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:off 10:off 11:off
Axes:  0:     0  1:     0  2:-32767  3:     0  4:     0  5:     0  6:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:off 10:off 11:off
Axes:  0:     0  1:     0  2:     0  3:     0  4:     0  5:     0  6:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:off 10:off 11:off
Axes:  0:     0  1:     0  2:-32767  3:     0  4:     0  5:     0  6:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:off 10:off 11:off
Axes:  0:     0  1:     0  2:     0  3:     0  4:     0  5:     0  6:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:off 10:off 11:off
Axes:  0:     0  1:     0  2:-32767  3:     0  4:     0  5:     0  6:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:off 10:off 11:off
Axes:  0:     0  1:     0  2:     0  3:     0  4:     0  5:     0  6:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:off 10:off 11:off
```

ubuntu 10.10 x86

---

### Post by anmelegov on 2011-02-25
Apologies for the bad English. The Russian-speaking forum ubuntu is my topic was ignored and it just sank

---

