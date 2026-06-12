---
title: "modprobe blacklist not working?"
date: 2010-10-14
forum: Hardware
---

### Post by icanhaszombie on 2010-10-14
allright, so the installed driver for my usb wireless is't working,  and I've added the driver to /etc/modprobe.d/blacklist.conf, but the device is still being recognized and the device manager says it's still using the driver, what am I doing wrong?

```
#realtek driver doesn't work.
blacklist rtl819xU
```

---

### Post by dabl on 2010-10-14
After booting the computer, do you see that particular driver listed when you run ```
sudo lsmod
```

??

---

### Post by icanhaszombie on 2010-10-14
No, but I did find two other drivers for that hardware that were running and blacklisting those solved the problem, thank you!

---

