---
title: "Run script when phone is connected through usb"
date: 2012-04-12
forum: Hardware
---

### Post by choel on 2012-04-12
Trying to run a script when my phone is plugged in via USB, a made a udev rule looks like this in /etc/udev/rules.d/85-lazydroid.rule

```

ATTRS{idVendor}=="22b8", ATTRS{idProduct}=="428c", RUN+="/home/joel/.lazydroid"
```

And the script .lazydroid looks like this:

```
#!/bin/bash
exec adb forward tcp:8080 tcp:8080 &
exec chromium-browser 127.0.0.1:8080 --new-window &

```

The script itself runs fine. The trick is I can't get the script to run up on insertion of the phone.

And it's the right ID according to: lsusb | grep Motorola
```

Bus 002 Device 042: ID 22b8:428c Motorola PCS

```

Any ideas?

---

