---
title: "Wavecom GSM Modem"
date: 2009-09-17
forum: Hardware
---

### Post by chet on 2009-09-17
Hi All, I'm running Ubuntu 8.04 and am hitting problems with Gnokii and my Wavemodem, I'm not sure if its down to my tty permissions so I will post here what I have done so far.

Install Gnokii
```
apt-get install gnokii
```

Created a .gnokiirc with the following
```
[global]
port = /dev/ttyS0
model = AT
initlength = default
connection = serial
use_locking = no
serial_baudrate = 19200
handshake = hardware
connect_script =
disconnect_script =
 
smsc_timeout = 10
 
[xgnokii]
allow_breakage = 0
[gnokiid]
bindir = /usr/sbin/
[connect_script]
TELEPHONE = 123456789
[disconnect_script]
 
[logging]
debug = off
rlpdebug = off
xdebug = off
```

Added the username to the dialout group
```
sudo addgroup $USERNAME dialout
```

added
```
KERNEL=="ttyS[0-9]", GROUP="dialout", MODE="0777"
``` 

to the end of etc/udev/rules.d/40-permissions.rules

I thought that would be it but I get the following.

When I try to identify it

gnokii --identify
GNOKII Version 0.6.22
Telephone interface init failed: Command timed out.
Quitting.
Cannot unlock device.
Command timed out.

Has anybody got any ideas on what I have missed?

Thanks

---

### Post by amolshastry on 2012-05-02
I had the same issue but when i changed my band to 9600 it worked.

---

