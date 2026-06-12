---
title: "Can't connect Nokia 6021 with irda and gnokii"
date: 2006-12-04
forum: Hardware &amp; Laptops
---

### Post by batty_whol on 2006-12-04
I'm trying to connect my nokia 6021 via a USB infrared dongle.
PC AMD 2200+
Distro Ubuntu Dapper Drake 606
Kernel 2.6.15-27-k7
Gnokii 0.6.12-0ubuntu3
USB irda Dongle Belkin FSU230(FIR3.2)

Having read numerous posts from all over the web, I haven't found anyone who has reported getting a Nokia 6021 to connect over irda (except one who unhelpfully just quoted 
> It works with ircomm over irda too.
My port is dev/ircomm0

But I don't even know what distro this person was using.

One of the posts I have read (forget which now) suggested that the nokia 6021 only worked at 9600 baud (hence having tried it at this speed. I have also tried it at 19200 (default).

From what I can tell, the irda dongle is working fine. It tries to connect to anything out there, but it does not get any response from the nokia.

Has anyone got any advise. I would greatly appreciate it as I need to backup (400+ phone numbers etc...) my old phone (screen smashed in car accident) to restore to my new phone.

Thanks in advance.

Batty:}

Here's what I have done (condensed, I have skipped numerour oops!).

On connecting the irda I get the following on the usb hub
```
#lsusb | grep -i irda
Bus 003 Device 041: ID 050f:0180 KC Technology, Inc. KC-180 IrDA Dongle
```

Modules loaded
```
#lsmod | grep irda
irda_usb               18820  0
irda                  217980  3 irtty_sir,sir_dev,irda_usb
crc_ccitt               2496  1 irda
usbcore               139012  9 irda_usb,ir_usb,usbserial,usb_storage,usbhid,usblp,ehci_hcd,ohci_hcd
#lsmod | grep irtty
irtty_sir               9536  2
sir_dev                21772  1 irtty_sir
irda                  217980  3 irtty_sir,sir_dev,irda_usb
```

```
#gnokii --identify
GNOKII Version 0.6.12
LOG: debug mask is 0x1
Lockfile /var/lock/LCK..ttyUSB0 is stale. Overriding it..
phone instance config:
model: 6021
port_device: /dev/ttyUSB0
connection_type: 4
init_length: 0
serial_baudrate: 9600
serial_write_usleep: -1
hardware_handshake: 0
require_dcd: 0
smsc_timeout: 100
connect_script:
disconnect_script:
rfcomm_cn: 1
sm_retry: off
Connecting
Serial device: opening device /dev/ttyUSB0
Expecting:
Timeout: aborting command ``/usr/lib/gnokii/gnokii'' with signal 9
```

While gnokii tries to identify, irdadump outputs:
```
#irdadump
01:44:47.170123 xid:cmd 165ed00c > ffffffff S=6 s=0 (14)
01:44:47.261140 xid:cmd 165ed00c > ffffffff S=6 s=1 (14)
01:44:47.349164 xid:cmd 165ed00c > ffffffff S=6 s=2 (14)
01:44:47.437177 xid:cmd 165ed00c > ffffffff S=6 s=3 (14)
01:44:47.525195 xid:cmd 165ed00c > ffffffff S=6 s=4 (14)
01:44:47.613214 xid:cmd 165ed00c > ffffffff S=6 s=5 (14)
01:44:47.701231 xid:cmd 165ed00c > ffffffff S=6 s=* piglet hint=0400 [ Computer ] (22)
```

---

