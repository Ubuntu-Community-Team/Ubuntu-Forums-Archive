---
title: "Post-hibernate module loading"
date: 2005-11-24
forum: Hardware &amp; Laptops
---

### Post by quietglow on 2005-11-24
On my Compaq n610c with w200 wireless "pod" for some reason, the orinoco driver does not load after a hibernation. I have to:

```
sudo modprobe orinoco_usb
```

Is there anywhere I can stick that command  to have it given automatically when coming out of hibernation? My wife's laptop uses ndiswrapper and its windows driver which also must be loaded manually--I'd like to use the same trick for that one as well.

Thanks!

---

### Post by xristos on 2005-11-24
Check this file /etc/default/acpi-support
I think there are some options there to unload a module before suspend .

---

### Post by quietglow on 2005-11-24
Excellent, that seems to work perfectly! I still get an error saying the module couldnt be loaded, but when I check, its there. That works for me.

---

