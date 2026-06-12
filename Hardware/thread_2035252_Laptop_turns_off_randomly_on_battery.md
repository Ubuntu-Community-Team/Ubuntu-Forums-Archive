---
title: "Laptop turns off randomly on battery"
date: 2012-07-30
forum: Hardware
---

### Post by soin on 2012-07-30
Hi all, I have enabled the laptop-mode once before and since then I experience this annoying bug, that my laptop turns off randomly when run on battery. On Win 7 this doesn't happen. 
In the syslog, the last lines before turn off are:
```

Jul 30 11:03:16 igor-Lenovo kernel: [ 2151.723378] wlan0: no IPv6 routers present
Jul 30 11:03:17 igor-Lenovo ntpdate[6950]: no server suitable for synchronization found
Jul 30 11:03:27 igor-Lenovo NetworkManager[1262]: <info> (wlan0): IP6 addrconf timed out or failed.
Jul 30 11:03:27 igor-Lenovo NetworkManager[1262]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Jul 30 11:03:27 igor-Lenovo NetworkManager[1262]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Jul 30 11:03:27 igor-Lenovo NetworkManager[1262]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.

```
I run a Lenovo y570 laptop. If you have any ideas - I would be very grateful. This didn't happen before I enabled laptop-mode

---

### Post by davidbilla on 2012-09-06
Hi,

I've got a Lenovo Y570 too. I don't have the laptop-mode on, but sometimes, Ubuntu shuts down as soon as I disconnect AC power, even if the battery is charged to some extent.

---

