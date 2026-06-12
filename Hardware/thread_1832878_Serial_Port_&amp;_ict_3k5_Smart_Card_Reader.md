---
title: "Serial Port &amp; ict 3k5 Smart Card Reader"
date: 2011-08-25
forum: Hardware
---

### Post by cid89 on 2011-08-25
Hi,

i need some help with this card reader (ict 3k5).. 

is plugged in the serial ttyS0... sending commands via shell doesnt work.. what can i do?

dmesg | grep tty
```

[    0.000000] console [tty0] enabled
[    0.453106] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.453391] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   16.785668] usb 3-3: pl2303 converter now attached to ttyUSB0
[   16.822847] usb 3-2: GSM modem (1-port) converter now attached to ttyUSB1
[   16.822975] usb 3-2: GSM modem (1-port) converter now attached to ttyUSB2
[   16.823113] usb 3-2: GSM modem (1-port) converter now attached to ttyUSB3

```

lsusb
```

Bus 004 Device 004: ID 102e:0003  
Bus 004 Device 003: ID 076b:5321 OmniKey AG 
Bus 004 Device 002: ID 0dd4:01a7 Custom Engineering SPA 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port
Bus 003 Device 002: ID 12d1:1001 Huawei Technologies Co., Ltd. E620 USB Modem
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0ac8:3420 Z-Star Microelectronics Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

srry for my bad english..

---

