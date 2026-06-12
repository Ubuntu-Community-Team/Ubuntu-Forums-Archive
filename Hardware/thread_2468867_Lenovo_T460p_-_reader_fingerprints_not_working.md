---
title: "Lenovo T460p - reader fingerprints not working"
date: 2021-11-12
forum: Hardware
---

### Post by 09martin09 on 2021-11-12
Hi, 

I am new to Ubuntu. I have switched from Win10 to Ubuntu 20.10. I have a problem with fingerprint reader. In terminal (lsusb) I can see it: 

Bus 001 Device 002: ID 138a:0090 Validity Sensors, Inc. VFS7500 Touch Fingerprint Sensor

I have found several instructions on the internet how to get it work, but nothing helped. I can not enroll the reader. If I try so, there is no device. Do you have any idea? Thanks.

---

### Post by TheFu on 2021-11-12
First, it should be noted that fingerprint readers aren't really very secure.  In testing there are about 50 "master" fingerprints that seem to unlock many common fingerprint computers.  This is a mix of hardware and software faults. Never use a fingerprint as the only method to unlock anything, ever, anywhere, unless you just want to impress people who don't know better.  Yes, we've all worked at places where fingerprints were used for "highly secure" access controls, but those were only after both a keycard AND PIN were entered.  At one data center, they kept it so cold inside that the warm-hand part of the fingerprint scanning process to leave never worked, since nobody inside could keep their fingers warm enough to pass.  Their solution?  Prop open 2 doors - on right next to the exit door next to the elevators and the other one behind a counter 20 ft away.

With all that said, it is very common for niche USB devices to never get Linux drivers.  I have a fingerprint reader on an Asus laptop and there aren't any Linux drivers.  You can search for drivers using the USBid - 138a:0090.

If you don't share the instructions, hard for anyone else to know what "several instructions on the internet" you found.  If it were me on a 20.10 box (which I'd never use for production), I'd start with these: [https://snapcraft.io/validity-sensors-tools](https://snapcraft.io/validity-sensors-tools)   Following instructions for older releases will likely fail, since drivers can be tightly coupled to the kernel used.
If you don't share what you did, exactly, with exact commands and exact outputs, hard for anyone else to know which step may have failed.

I get the disappointment in not having all the hardware working perfect, but at least it isn't something that cannot be replaced by a $20 FIDO2 device which will provide better security without the risk of losing a finger.

Good luck.

---

