---
title: "CDMA USB Device not working"
date: 2009-03-13
forum: Hardware
---

### Post by _khAttAm_ on 2009-03-13
I have recently purchased a CDMA USB modem, but found that it doesn't work with Linux.

When I did "lsusb", I got:
```

Bus 002 Device 004: ID 10c4:ea60 Cygnal Integrated Products, Inc. CP210x Composite Device

```

When I did "dmesg", I got:
```

[ 7315.232028] usb 2-2: reset full speed USB device using uhci_hcd and address 4
[ 7315.390334] cp2101 2-2:1.0: cp2101 converter detected
[ 7315.500057] usb 2-2: reset full speed USB device using uhci_hcd and address 4
[ 7315.650358] usb 2-2: cp2101 converter now attached to ttyUSB0

```

I tried wvdialconf and the result was
```

Scanning your serial ports for a modem.

ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Modem Port Scan<*1>: S1   S2   S3
ttyACM0<Info>: Device or resource busy
Modem Port Scan<*1>: ACM0
WvModem<*1>: Cannot get information for serial port.
ttyUSB0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyUSB0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyUSB0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.


Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?


```

It works well with xp inside virualbox, but couldn't share internet with Ubuntu.

Any comment will be highly appreciated.

---

