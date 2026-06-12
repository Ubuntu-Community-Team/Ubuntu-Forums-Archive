---
title: "How to get remote control working"
date: 2008-08-10
forum: General Help
---

### Post by BiscuitTin on 2008-08-10
Hi all,

Please how do I get my remote control workig under Linux?

I have installed lirc, and I have a /dev/lircd device, however irw does not work and when you try to cat  the device /dev/lircd you get a message telling you that it is not a valid device.

Any help would be appreciated.

---

### Post by txcrackers on 2008-08-10
```
sudo /etc/init.d/lircd start
```

And the device will actually probably be /dev/lirc0

---

