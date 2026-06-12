---
title: "How can I capture ascii stream onn USB/serial port"
date: 2014-10-25
forum: Hardware
---

### Post by parcdulas on 2014-10-25
Hello,

I have a Prolific USB to Serial converter.

lsusb shows:

bus 004 device 002 ID 067b:2303 prolific technology PL2303 Serial port

There should be an ascii stream at 57k 8bit 1 stop bit no handshake comming in (as an XML message apparently according to the device mfr.) Ho can I view and ultimately capture to a file this stream?

Thanks,

Martin

---

### Post by parcdulas on 2014-10-25
I tried dmeg | grep tty
and found that the port was ttyusb0

tried a few different serial reader applications including moserial which recognised ttyusb0.

when I try to connect I get the message "cannot open ttyusb0"

any suggestions?

Martin

---

