---
title: "USB bug?"
date: 2013-08-23
forum: Hardware
---

### Post by Andrew_Lucas on 2013-08-23
Hi all,

I issued "lsusb" the other day, trying to get information about my laptop's internal wireless internet adapter. I noticed this particular peculiarity in the feedback and thought it would be worth asking about:

```
andy@ZoostormLinuxLaptop:~$ lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 004: ID 0bb4:0fb4 HTC (High Tech Computer Corp.) 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 003: ID 0bda:8723 Realtek Semiconductor Corp.
```

For some reason, there seems to be three 2.0 root hubs - the odd thing, however, is that this does not in anyway match up to my USB ports (which it should, right?). I've only *three* USB ports, 2xUSB3.0 and 1xUSB2.0. Can anyone explain this feedback based on that - I suspect it's something about the kernel or lsusb I don't understand.

Finally, a quick shout out to my wireless thread, which needs solving ASAP :(. Further info can be found [here]("http://ubuntuforums.org/showthread.php?t=2169602")

---

### Post by varunendra on 2013-08-24
> **Andrew_Lucas said:**
> For some reason, there seems to be three 2.0 root hubs - the odd thing, however, is that this does not in anyway match up to my USB ports (which it should, right?). I've only *three* USB ports, 2xUSB3.0 and 1xUSB2.0.

My laptop has four internal USB hubs (3xUSB2, 1xUSB3), and only two external USB ports (1xUSB2, 1xUSB3). ;)

Some of the internal hubs are used for internal devices like webcam, bluetooth, fingerprint reader, (sometimes) wifi adapters, card readers etc. So don't get confused with that. The command lsusb doesn't lie, although you may get the details of 'what' the other hubs are used for only when the devices attached to them are in use.

To get these details, the most common commands are "usb-devices" and "lsusb -v"

Hope it helps explaining the lsusb outputs. :)

**PS:**
Posted on your other thread.

---

### Post by Andrew_Lucas on 2013-08-25
> **varunendra said:**
> My laptop has four internal USB hubs (3xUSB2, 1xUSB3), and only two external USB ports (1xUSB2, 1xUSB3). ;)

Some of the internal hubs are used for internal devices like webcam, bluetooth, fingerprint reader, (sometimes) wifi adapters, card readers etc. So don't get confused with that. The command lsusb doesn't lie, although you may get the details of 'what' the other hubs are used for only when the devices attached to them are in use.

To get these details, the most common commands are "usb-devices" and "lsusb -v"

Hope it helps explaining the lsusb outputs. :)

**PS:**
Posted on your other thread.

Cheers man. :D That's really cleared things up!

Your ongoing support is appreciated in the wirless thread, too.

---

