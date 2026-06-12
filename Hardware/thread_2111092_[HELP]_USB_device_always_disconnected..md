---
title: "[HELP] USB device always disconnected."
date: 2013-02-01
forum: Hardware
---

### Post by techfanatic on 2013-02-01
Hi Experts,

I had a touchpad named B16 from HANWANG company.

Recently I tried to write a driver for the input device( pen touch usb device). Luckily, I had made it for the Ubuntu 10.04.4(kernel 2.6.32), and it works well

I tried to migrate to the Ubuntu 12.10(kernel 3.5.0-17), but the usb device fail to connect. I also tried in the kernel 3.0.36, it output the same message

There is no error message in the log, it just show the device connected and disconnected....


I had viewed by "lsusb", it shows the 0b57:8408 device when it connected, and disappeared within 1s.

Could you give some help or comments?
What i can do to debug this issue?


Thanks,
Joshua

---

### Post by techfanatic on 2013-02-01
I debugged using a usb debug kernel, it shows the hub port status was changed frequently.
I was still in the investigation

---

