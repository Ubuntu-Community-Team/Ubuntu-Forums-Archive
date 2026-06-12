---
title: "Invalid keys for Apple Magic Keyboard (A1644) in wireless mode"
date: 2019-06-09
forum: Hardware
---

### Post by kinetic-cookie on 2019-06-09
Hi. I encountered a strange behavior trying to use the keyboard wirelessly.
In wired mode I have working Fn keys, but in wireless mode they send other keys.

I tried to investigate it myself and found following:

The same keyboard in different modes has different vendor and product id.
I checked it with lsusb in wired mode (Apple Inc. Magic Keyboard Input device ID: bus 0x3 vendor 0x5ac product 0x267 version 0x110) 
and bluetoothctl in wireless mode (Magic Keyboard bus 0x5 vendor 0x4c product 0x267 version 0x67)

Is this intended? How do I fix it?

upd

> 
lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.2 LTS
Release:    18.04
Codename:    bionic


> 
uname -a
Linux MS-7A72 4.15.0-51-generic #55-Ubuntu SMP Wed May 15 14:27:21 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux


---

