---
title: "USB flash memory reader works in 2.6.10, not 2.6.11"
date: 2005-05-18
forum: Hardware &amp; Laptops
---

### Post by pointym5 on 2005-05-18
I've got both the 2.6.10 and 2.6.11 K8 kernel packages installed. Today, running on 2.6.11, I noticed that my CF reader was not detecting a flash device when it was inserted. In other words, inserting the CF card resulted in no messages in /var/log/messages at all.

I rebooted from the generic kernel and from 2.6.10, and it worked as expected. But rebooting again to 2.6.11 and it doesn't work at all.

The USB subsystem works at least partially in 2.6.11, as I've got a USB keyboard and mouse, and those were fine.

---

### Post by ossi on 2005-05-18
Hi!

I got a similar problem with usb mass storages and the 2.6.11 kernel version. I got no problem with mounting them. As long as they are mounted it still works but when unmounting or unplugging them the whole system freezes immediately and crashes.

When I use a protocol like ptp with digital cameras or other options it works. The assistant for importing pictures pops up and guides through the process. Also no problem with unmounting.

---

