---
title: "Back panel USB ports not working"
date: 2014-03-16
forum: Hardware
---

### Post by p-chris-x on 2014-03-16
I have a Razer BlackWidow keyboard and Razer DeathAdder mouse, and performed a clean install of Ubuntu 13.10 yesterday. Everything was working fine in terms of keyboard and mouse input even after reboots, however when I booted up today neither my keyboard nor mouse is working if they're connected to any USB port on the back of the motherboard. If I connect them to one of the USB ports on my case (meaning they go through the USB header on the motherboard) they work fine.

I've eliminated the possibility of this being a motherboard issue as the keyboard and mouse works fine under the BIOS and when I run Ubuntu from a live CD, so it must be something wrong with my Ubuntu install. Unfortunately as I'm pretty new to Ubuntu I need all the help I can get!

From Googleing, here's a command you might find useful:

```
chris@sasha:~$ lsusbBus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 8087:07da Intel Corp. 
Bus 001 Device 010: ID 1532:0037 Razer USA, Ltd 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 005: ID 046d:c245 Logitech, Inc. G400 Optical Mouse
Bus 003 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

A Razer device is in the list so I'm not sure why it isn't working... anyway any help is greatly appreciated. :)

Edit: Literally 2 minutes after I posted this I fixed the issue. I got the idea of reverting all BIOS settings back to default while I was writing the post and after I did that it works again. Strange considering the only difference I made under the BIOS was to enable virtualization technology for my VMs. Anyway, fix now :)

---

