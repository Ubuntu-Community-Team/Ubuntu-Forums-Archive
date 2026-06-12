---
title: "usb doesn't work on lenovo u460"
date: 2014-06-04
forum: Hardware
---

### Post by maarten6 on 2014-06-04
Hi,

i just installed ubuntu 14 on a lenovo u460.
i could not do this using usb (the option was't there in the boo menu)
i successfully installed but now i can not use usb, I tried all
3 ports, different devices (that work) and changing the boot options
to legacy and back. i can't find the devices in the dev folder.

does anybody have suggestions?
keyboard and mouse are working

thanks!

---

### Post by varunendra on 2014-06-05
Welcome to the forums maarten6!

Is there a feature called "IOMMU" in the BIOS? If yes, try toggling its state (enabled to disabled, or opposite of it). If no such feature is there, or if it doesn't help, please open a terminal (Ctrl-Alt-T), and show us the output of -
```
lsusb
```

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

