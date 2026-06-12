---
title: "bluetooth Lenovo Yoga 11s"
date: 2014-10-30
forum: Hardware
---

### Post by mephisto56 on 2014-10-30
Just installed 14.10. Wireless works out of the box now (hooray). Previously I had to use [https://github.com/lwfinger/rtl8723au](https://github.com/lwfinger/rtl8723au). For bluetooth the driver was [https://github.com/lwfinger/rtl8723au_bt](https://github.com/lwfinger/rtl8723au_bt) but that never worked for me. The page also states that kernel version is max 3.13.  I've been browsing through a lot of sites and never got it to work with 14.04. ```
rfkill list all
``` shows it is not soft nor hard blocked. When I go to systems settings -> bluetooth I can switch it to on but it keeps saying bleutooth is disabled (and it is 'off' again when I visit the setting again). ```
lsusb
``` shows:

```
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 005: ID 03eb:8814 Atmel Corp. 
Bus 002 Device 004: ID 2047:0855 Texas Instruments 
Bus 002 Device 003: ID 0bda:1724 Realtek Semiconductor Corp. 
Bus 002 Device 002: ID 5986:053d Acer, Inc 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

Anyone that can guide me through the getting it to work?

---

### Post by paulmiles on 2014-10-30
Is bluetooth the only thing which didn't work when you installed 14.10?

---

### Post by mephisto56 on 2014-10-30
> **paulmiles said:**
> Is bluetooth the only thing which didn't work when you installed 14.10?

There's also automatic screen rotation that doesn't work. It deactivates keyboard in tablet mode but not the trackpad. Anything specifically you want to know whether it works or not?

---

### Post by mephisto56 on 2014-11-09
I have an old usb bluetooth dongle and it also doesn't work. It does work however on my computer (using 12.04, which I installed on my lenovo but doesn't make a difference) so I know ubuntu can work with it. I don't understand why it won't work on my laptop then.

I have tried enabling/disabling bluetooth in windows. No success.

---

### Post by mephisto56 on 2015-04-03
Bluetooth now works. I've used the tips in this thread:

[https://github.com/lwfinger/rtl8723au_bt/issues/18](https://github.com/lwfinger/rtl8723au_bt/issues/18)

---

### Post by mephisto56 on 2015-04-03
Bluetooth now works. I've used the tips in this thread:

[https://github.com/lwfinger/rtl8723au_bt/issues/18](https://github.com/lwfinger/rtl8723au_bt/issues/18)

---

