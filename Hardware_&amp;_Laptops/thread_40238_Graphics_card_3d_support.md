---
title: "Graphics card 3d support"
date: 2005-06-08
forum: Hardware &amp; Laptops
---

### Post by Coffeegeek on 2005-06-08
I have a fairly new onboard graphics card [with 3d acceleration]
its being identified on the device manager as unknown 0x0016 vendor:SIS
and my FPS isn't that great [like 125fps]

how do i get the hardware identified and 3d acceleration working?

  -Thanks =)

---

### Post by jrhodes on 2005-06-08
open up a terminal, run this command:
```
lspci |grep -i vga
```
and paste the output in your reply, so we can know what graphics chip it is.

---

### Post by az on 2005-06-08
See this and good luck!
[http://www.winischhofer.net/linuxsisvga.shtml](http://www.winischhofer.net/linuxsisvga.shtml)

---

### Post by Coffeegeek on 2005-09-07
sorry for the long delay and thanks for your responses.

CoffeeGeek@ubuntu:~$ lspci |grep -i vga
0000:01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter

i went to [http://www.winischhofer.net/linuxsisvga.shtml](http://www.winischhofer.net/linuxsisvga.shtml), but i'm afraid its out of my depth, even though it seems to match my hardware.

---

