---
title: "[SOLVED] Asus Laptop with Atheros Wifi not working??"
date: 2008-09-26
forum: Hardware
---

### Post by Mgiacchetti on 2008-09-26
On a default install do this in terminal

```
[FONT=monospace]
[/FONT]sudo su[FONT=monospace]
[/FONT]enter your password[FONT=monospace]
[/FONT]echo 0 > /sys/devices/platform/asus-laptop/bluetooth[FONT=monospace]
[/FONT]echo 1 > /sys/devices/platform/asus-laptop/wlan 

```

you can also shut off that pesky ambient light sensor by going
```

sudo su
enter your password
echo 0 > /sys/devices/platform/asus_laptop/ls_switch

```

---

