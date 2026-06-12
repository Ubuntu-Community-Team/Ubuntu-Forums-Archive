---
title: "wireless driver broken after kernel update"
date: 2010-10-01
forum: Hardware
---

### Post by kastied on 2010-10-01
I just upgraded the kernel on my Ubuntu laptop from 2.6.32-24-generic to 2.6.32-25-generic (using the update manager under gnome). After the update, the wireless network controller shows up as UNCLAIMED when I do lshw -C network.

When I try to install the driver with the commands
sudo modprobe lib80211
sudo insmod wl.ko

...i get this error message:
insmod: error inserting 'wl.ko': -1 Invalid module format

I have compiled the driver using the 2.6.32-24 kernel. Do I have to re-compile with the new kernel?

I'm a unix user, but not a kernel hacker, so I'm wondering if I will run into problems every time I get a kernel update? Or is this problem an exception?

Thanks for helping.


Ubuntu 10.4.1
Kernel version 2.6.32-25-generic
previous Kernel version: 2.6.32-24-generic

WLAN network controller: Broadcom BCM4311

---

