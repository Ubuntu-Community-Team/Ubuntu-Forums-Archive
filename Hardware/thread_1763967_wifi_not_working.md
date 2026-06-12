---
title: "wifi not working"
date: 2011-05-21
forum: Hardware
---

### Post by @rc on 2011-05-21
hi,
I have recently installed ubuntu 10.04 inside windows 7, in my hp pavilion dv6 laptop. My wifi works fine in windows. However ,in ubuntu, no network is detected at all. I have to use a lan wire to get net access.I dont know how to check wifi drivers.Please help

---

### Post by joshuachoo on 2011-05-21
Try the following command:

```
rfkill list all
```

Does it say 'Soft blocked: Yes' under Wireless LAN?

If so, try the command:

```
rfkill unblock all
```[FONT=Courier New][/FONT]

If your wireless is now working and you can detect networks, then you have to ensure that the *rfkill* command is run at system startup by editing the /etc/rc.local file:

```
sudo gedit /etc/rc.local
```

Add the following line above "*exit 0"*:

```
rfkill unblock all
```

Reboot Ubuntu to see if it works. Good luck!

---

### Post by @rc on 2011-05-22
thnx for replying....i tried the command, but nothing happened(i.e.no visible output).What does that mean?

---

### Post by joshuachoo on 2011-05-23
Perhaps it is not installed? If that is so, try installing *rfkill* by Synaptics or do:
```
sudo apt-get install rfkill
```

If *rfkill *is installed but still fails to work you should try going to *Additional Drivers* and removing the "STA driver", and later install *b43-fwcutter* and *firmware-b43-installer.* Reboot.

Tell me how it works out!

---

