---
title: "bluetooth.service active only after restart"
date: 2016-12-29
forum: Hardware
---

### Post by ndoob on 2016-12-29
Hello Community..

So, I have a lenovo G510 laptop with xubuntu 16.04.1. When I power on my laptop, I couldn't start the blueman-manager. It works only when I restart my laptop. After further trace:

```
systemctl status bluetooth.service
``` returns 
```

&#9679; bluetooth.service - Bluetooth service
   Loaded: loaded (/lib/systemd/system/bluetooth.service; enabled; vendor preset: enabled)
   Active: inactive (dead)
     Docs: man:bluetoothd(8)

```
every fresh startup, but returns
```

&#9679; bluetooth.service - Bluetooth service
   Loaded: loaded (/lib/systemd/system/bluetooth.service; enabled; vendor preset: enabled)
   Active: active (running) since Do 2016-12-29 21:51:09 CET; 15s ago
     Docs: man:bluetoothd(8)
 Main PID: 1593 (bluetoothd)
   Status: "Running"
   CGroup: /system.slice/bluetooth.service
           &#9492;&#9472;1593 /usr/lib/bluetooth/bluetoothd


Dez 29 21:51:09 debby systemd[1]: Starting Bluetooth service...
Dez 29 21:51:09 debby bluetoothd[1593]: Bluetooth daemon 5.37
Dez 29 21:51:09 debby systemd[1]: Started Bluetooth service.
Dez 29 21:51:09 debby bluetoothd[1593]: Starting SDP server
Dez 29 21:51:09 debby bluetoothd[1593]: Bluetooth management interface 1.10 initialized

```
every restart.

Is this a session issue? Or do I have to force bluetooth service to start on boot? Many thanks!

---

