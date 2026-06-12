---
title: "Server won't boot without keyboard plugged in."
date: 2013-03-07
forum: Hardware
---

### Post by Maheriano on 2013-03-07
I installed Ubuntu Server on an Acer AC100S purchased from [here]("http://www.memoryexpress.com/Products/MX38131"). I installed Server multiple times and Desktop once, every time I do it, the machine fails to boot with the keyboard unplugged. The boot order is as follows:
- UEFI
- removable
- RAID disk
- network
When the keyboard is plugged in, it finds Ubuntu on the RAID disk and boots it. When it's not plugged in, it skips the RAID disk and tries to boot from the network, looking for a DHCP connection......then failing. I've never heard of this before, any idea what can fix this? This is a server going to a client site 5 hours away.

---

### Post by Maheriano on 2013-03-08
I've confirmed this multiple times. It has no problem booting with the LiveUSB but on the base install it won't boot without a keyboard plugged into it. It keeps skipping the RAID disk and trying to boot from DHCP, I don't get it. Why would it do that? I've been through the BIOS 5 times and also confirmed it is the newest version, there is absolutely nothing in there to halt the system without a keyboard.

---

