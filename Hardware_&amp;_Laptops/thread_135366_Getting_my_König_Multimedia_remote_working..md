---
title: "Getting my König Multimedia remote working."
date: 2006-02-23
forum: Hardware &amp; Laptops
---

### Post by daller on 2006-02-23
Hi There,

Just got a König Remote delivered! - But it doesn't work :(

Model: IR-PC1

```
daniel@ubuntu:~$ lsusb
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 0ad1:17f2 Remotec Technology, Ltd
Bus 001 Device 001: ID 0000:0000

```

According to xev and dmesg, none of the keys send signals.

Any ideas on what to do?

---

### Post by kintoandar on 2008-04-02
Did you have any luck with the konig ir-pc1?
I just bought one and I've no idea how to configure it. 


I'm using gutsy and on /var/log/messages I get this:

```
Apr  2 21:27:35 localhost kernel: [   14.628000] usbcore: registered new interface driver xpad
Apr  2 21:27:35 localhost kernel: [   14.628000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/in
put/joystick/xpad.c: driver for Xbox controllers v0.1.6
```

With lsusb:
> 
Bus 004 Device 002: ID 0ad1:6130 Remotec Technology, Ltd

Any help would be appreciated. 
Thanks!

---

