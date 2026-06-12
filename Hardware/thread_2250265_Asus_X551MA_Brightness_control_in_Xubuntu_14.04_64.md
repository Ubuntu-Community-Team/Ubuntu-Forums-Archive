---
title: "Asus X551MA: Brightness control in Xubuntu 14.04 64-bit"
date: 2014-10-27
forum: Hardware
---

### Post by nikita-e on 2014-10-27
Hello!

I can't finally tune the brightness control on my Asus X551MA in Xubuntu 14.04 64-bit. I've already done the following:

1. Change a line in **/etc/default/grub** to **GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi="**

2. Create a file **/usr/share/X11/xorg.conf.d/20-intel.conf**

```
Section "Device"
        Identifier "card0"
        Driver "intel"
        Option "Backlight" "intel_backlight"
        BusID "PCI:0:2:0"
EndSection
```

Now f5 and f6 activate the notification window only but the brightness doesn't change.

Could you please help me to find a solution?

---

### Post by nikita-e on 2014-10-27
In addition. xbacklight works, but I would like to tune the system correctly without extra apps.

---

### Post by nikita-e on 2014-10-28
Already not actual. I've installed Xubuntu 14.10 and after abovementioned actions the brightness control works via f5 and f6.

---

