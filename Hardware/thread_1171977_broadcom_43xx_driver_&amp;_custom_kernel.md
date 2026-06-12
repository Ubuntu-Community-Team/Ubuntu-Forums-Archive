---
title: "broadcom 43xx driver &amp; custom kernel"
date: 2009-05-27
forum: Hardware
---

### Post by demios on 2009-05-27
So I installed a custom kernel for low-latency firewire audio work, and it works well, except that there is no wireless driver installed into it (there is on in the generic kernel). There is also no wired network driver in it, so no direct internet. so what I need to do is download the driver while booted into generic, reboot into the custom kernel and install it, *without* overwriting the one that is beautifully integrated into my generic kernel.

my question is, can I simply follow the instructions on the broadcom driver's page ([http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)) without messing up my old driver?

hardware is a dell inspiron with the BCM4328 a/b/g/n adapter.

please tell me if my assumptions about drivers and kernel modules and whatever are flawed :)

---

