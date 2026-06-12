---
title: "Arduino serial port greyed out"
date: 2016-01-05
forum: Hardware
---

### Post by telmovaz on 2016-01-05
Hey guys,


I'm trying to upload some code to my Arduino Uno trough Arduino IDE I installed from synaptic.

It  happens that I cannot upload since it says "serial port COM1 not  found". Whenever I go to "Tools > Serial Ports" it is greyed out. i  googled the problem and found out that if I started arduino from sudo it  would work but it didn't.

I'm using Xubuntu 13.

lsusb:
```

Bus 003 Device 002: ID 8087:8001 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0cf3:e300 Atheros Communications, Inc. 
Bus 001 Device 003: ID 174f:14ee Syntek 
Bus 001 Device 002: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

java -version:
```

java version "1.7.0_91"
OpenJDK Runtime Environment (IcedTea 2.6.3) (7u91-2.6.3-0ubuntu0.14.04.1)
OpenJDK 64-Bit Server VM (build 24.91-b01, mixed mode)

```

uname -a:
```
Linux vaz 4.3.0-040300-generic #201511020949 SMP Mon Nov 2 14:50:44 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
```

---

