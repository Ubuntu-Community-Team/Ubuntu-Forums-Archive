---
title: "HDMI cable doesn't work"
date: 2024-04-26
forum: Hardware
---

### Post by icegood on 2024-04-26
Hello. In mine HP Victus by HP Laptop 16-e0xxx
i have two distros: ubuntu 24.04 and fedora. Both previous 23.10 and new one have HDMI cable plugged into my external projector and don't generate any udev events. 
New ubuntu is:
```

Linux ice-home 6.8.0-31-generic #31-Ubuntu SMP PREEMPT_DYNAMIC Sat Apr 20 00:40:06 UTC 2024 x86_64 x86_64 x86_64 GNU/Linux

```


While my old fedora
```

[root@fedora ice]# uname -a
Linux fedora 6.0.17-200.fc36.x86_64 #1 SMP PREEMPT_DYNAMIC Wed Jan 4 16:00:03 UTC 2023 x86_64 GNU/Linux

```

generates next events while plugged in:
```

KERNEL[48.311971] change   /devices/pci0000:00/0000:00:01.1/0000:01:00.0/drm/card0 (drm)
UDEV  [48.317955] change   /devices/pci0000:00/0000:00:01.1/0000:01:00.0/drm/card0 (drm)
KERNEL[49.453282] add      /devices/pci0000:00/0000:00:01.1/0000:01:00.0/graphics/fb1 (graphics)
UDEV  [49.455485] add      /devices/pci0000:00/0000:00:01.1/0000:01:00.0/graphics/fb1 (graphics)

```
and everything fine there.

is it kernel issue or some ubuntu overrides?

---

