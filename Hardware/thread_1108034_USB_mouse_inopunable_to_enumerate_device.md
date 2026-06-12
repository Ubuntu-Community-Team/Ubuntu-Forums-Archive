---
title: "USB mouse inop/unable to enumerate device"
date: 2009-03-27
forum: Hardware
---

### Post by jasonmichel on 2009-03-27
have an HP dc7-1170us that has been running 8.10 for a few months now.  using the same usb mouse.  Today i boot up and it says can't enumerate usb device..but boots up..when i log in.i can't use the mouse..tried every port..rebooted with it in it, tried a new mouse.  Touchpad works.  

Dmesg

[  470.704181] hub 8-0:1.0: connect-debounce failed, port 2 disabled
[  472.632185] hub 8-0:1.0: connect-debounce failed, port 3 disabled
[  474.556181] hub 8-0:1.0: connect-debounce failed, port 4 disabled
[  476.493079] hub 8-0:1.0: connect-debounce failed, port 2 disabled
[  478.420685] hub 8-0:1.0: connect-debounce failed, port 3 disabled
[  480.088204] hub 8-0:1.0: unable to enumerate USB device on port 4
[  480.308222] hub 1-0:1.0: unable to enumerate USB device on port 1
[  482.228181] hub 8-0:1.0: connect-debounce failed, port 2 disabled
[  484.156182] hub 8-0:1.0: connect-debounce failed, port 3 disabled
[  484.396203] hub 8-0:1.0: unable to enumerate USB device on port 4
[  486.340193] hub 8-0:1.0: connect-debounce failed, port 2 disabled
[  488.284532] hub 8-0:1.0: connect-debounce failed, port 3 disabled
[  488.752567] hub 8-0:1.0: unable to enumerate USB device on port 4
[  488.948587] hub 1-0:1.0: unable to enumerate USB device on port 1
[  490.872603] hub 8-0:1.0: connect-debounce failed, port 2 disabled
[  492.796561] hub 8-0:1.0: connect-debounce failed, port 3 disabled
[  493.792202] hub 8-0:1.0: unable to enumerate USB device on port 4
[  495.732101] hub 8-0:1.0: connect-debounce failed, port 2 disabled
[  497.660189] hub 8-0:1.0: connect-debounce failed, port 3 disabled
[  498.284668] hub 8-0:1.0: unable to enumerate USB device on port 4
[  498.480639] hub 1-0:1.0: unable to enumerate USB device on port 1
[  500.404603] hub 8-0:1.0: connect-debounce failed, port 2 disabled
[  502.324182] hub 8-0:1.0: connect-debounce failed, port 3 disabled
[  502.820307] hub 8-0:1.0: unable to enumerate USB device on port 4
[  504.788153] hub 8-0:1.0: connect-debounce failed, port 2 disabled
[  506.708184] hub 8-0:1.0: connect-debounce failed, port 3 disabled
[  507.144100] hub 8-0:1.0: unable to enumerate USB device on port 4
[  507.340144] hub 1-0:1.0: unable to enumerate USB device on port 1
[  509.264181] hub 8-0:1.0: connect-debounce failed, port 2 disabled
[  511.192684] hub 8-0:1.0: connect-debounce failed, port 3 disabled
[  511.528131] hub 8-0:1.0: unable to enumerate USB device on port 4
[  513.464556] hub 8-0:1.0: connect-debounce failed, port 2 disabled
[  515.384688] hub 8-0:1.0: connect-debounce failed, port 3 disabled
[  516.240211] hub 8-0:1.0: unable to enumerate USB device on port 4
[  516.436227] hub 1-0:1.0: unable to enumerate USB device on port 1
[  518.360324] hub 8-0:1.0: connect-debounce failed, port 2 disabled
[  520.280191] hub 8-0:1.0: connect-debounce failed, port 3 disabled
[  521.552129] hub 8-0:1.0: unable to enumerate USB device on port 4
[  523.512552] hub 8-0:1.0: connect-debounce failed, port 2 disabled
[  525.444183] hub 8-0:1.0: connect-debounce failed, port 3 disabled
[  525.780698] hub 8-0:1.0: unable to enumerate USB device on port 4
[  525.976615] hub 1-0:1.0: unable to enumerate USB device on port 1

and lsusb


Bus 008 Device 004: ID 046d:09b8 Logitech, Inc. 
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub



any ideas?    thanks in advanced

---

### Post by jasonmichel on 2009-03-27
i should add, that i can plug other usb devices in such as a usb memory stick and it works fine..so this seems to be isolated  to mouse

---

