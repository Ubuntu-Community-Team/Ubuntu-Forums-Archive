---
title: "No S-Video out on 11.04 with Intel 945GM"
date: 2011-05-27
forum: Hardware
---

### Post by KurtPreston on 2011-05-27
I just installed Ubuntu 11.04 on a Pandora 945-D (using an Intel 945GM chipset).  My DVI monitor works just fine, but I can't get Ubuntu to output to the S-Video port.

The port is registered as connected, however, I can't get it to actually output at any resolution.

In my Xorg.0.log file, I have the following lines pertaining to the S-Video out (TV1):
**cat /var/log/Xorg.0.log | grep TV1**
```

[    17.956] (II) intel(0): Output TV1 has no monitor section
[    18.240] (II) intel(0): EDID for output TV1
[    18.240] (II) intel(0): Printing probed modes for output TV1
[    18.240] (II) intel(0): Output TV1 connected
[    18.240] (II) intel(0): Output TV1 using initial mode 1024x768

```

I have tried to generate an Xorg.conf file to change my settings, but **sudo Xorg -configure** returns an error:
```

(++) Using config file: "/home/inventables/xorg.conf.new"
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
Number of created screens does not match number of detected devices.
  Configuration failed.
 ddxSigGiveUp: Closing log

```

Anyone have any insight?

Thanks!

---

