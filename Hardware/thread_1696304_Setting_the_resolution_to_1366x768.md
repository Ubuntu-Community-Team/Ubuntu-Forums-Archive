---
title: "Setting the resolution to 1366x768"
date: 2011-02-27
forum: Hardware
---

### Post by usagiakumu on 2011-02-27
In Ubuntu 10.04 and earlier I was simply able to add this to xorg.conf and reboot and things would be peachy.

Nvidia 6100 soon to be 8400GS but like I said it was able to support it just fine

The drivers only see 1360X768 which looks butt ugly and 1368x768 which is "out of range" I would like to in 10.10 set it to 1366x768.

Is there some new file I just go and edit? What do I need to do to accomplish this. It is an Acer computer with Acer monitor that came with Windows on it which supports it as well, so it is a well supported but very odd resolution. Thanks in advance :)

---

### Post by realzippy on 2011-02-27
...you have an old (from 10.04) xorg.conf with this modeline?

---

### Post by usagiakumu on 2011-02-27
Yes and all it does is wants to default to 1368

Before I would simply deactivate KMS and unload Neauvu from the driver, upon doing so rendered X useless. 

```

#!/bin/bash

echo 0 > /sys/class/vtconsole/vtcon1/bind
rmmod nouveau
/etc/init.d/consolefont restart
rmmod ttm
rmmod drm_kms_helper
rmmod drm


```

To do this all I would need to do is put that code in 
/sys/class/vtconsole/vtcon*/name then point to it with xorg.conf then
put under display depth 'default resolution "1366x768"' and it would load.

---

