---
title: "Imon RM200 remote (device 15c2:ffdc) won't work on Ubuntu 12.04 or 11.10"
date: 2012-06-24
forum: Hardware
---

### Post by Skerit on 2012-06-24
The device is recognized just fine:

```

Bus 001 Device 005: ID 15c2:ffdc SoundGraph Inc. iMON PAD Remote Controller

Found /sys/class/rc/rc0/ (/dev/input/event6) with:
    Driver imon, table rc-imon-mce
    Supported protocols: RC-6 
    Enabled protocols: RC-6 
    Repeat delay = 500 ms, repeat period = 125 ms

```

But any testing results in nothing.

I point the remote, I press a few button and nothing happens. Not in irw, not in ir-keytable, nothing. It's driving me insane.

---

