---
title: "Bluez sspmode Input/Output Error"
date: 2016-02-10
forum: Hardware
---

### Post by ted20 on 2016-02-10
Hi,

I have multiple identical Bluetooth USB dongles that I've been using on the same machine. 

The following command *works* on the first device: **hciconfig hci0 sspmode 1/0**

However, when I plug a different (identical dongle) into the same machine and run the same command I get: [B]Can't read Simple Pairing mode on hick: Input/output error (5)

[/B]I've tried resetting the configs etc, even reinstalling Bluez but the only thing that seems to work is running a dpkg --purge on bluez - which isn't ideal!

Can anyone give me some pointers as to where bluez may be getting confused between dongles?

Cheers,

Ted

---

