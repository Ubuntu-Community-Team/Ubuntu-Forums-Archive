---
title: "Ubuntu custom refresh rate"
date: 2013-01-11
forum: Hardware
---

### Post by mostwanted4 on 2013-01-11
Hello! After upgrading from 12.04 to 12.10 I can't use my monitor at max resolution(1680x1050) because it does not support the refresh rate. I'm not sure what was it before the upgrade but  in windows I use it at 59 Hz.

I tried making a custom mode using xrandr newmode and addmode, but at addmode I get:

```
xrandr --addmode DVI-I-0 "1680x1050_59.00"
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  31
  Current serial number in output stream:  32
```

Do you know any way to make it work at 59 Hz?

Note: Everything is updated to the day.
 
P.S. I'm trying to avoid the "edit xorg.conf" way.

---

