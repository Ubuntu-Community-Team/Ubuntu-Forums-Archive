---
title: "Bluetooth mouse reconnect problem in 18.04"
date: 2018-09-09
forum: Hardware
---

### Post by Gijsbert_Wiesenekk on 2018-09-09
Hi,

Ever since I upgraded to 18.04 (from 16.04) my Logitech M557 bluetooth mouse fails to reconnect automatically after a suspend/resume or a reboot of my laptop. As a workaround I created a simple shell script:

```
bluetoothctl <<EOF
connect MAC-ADDRESS-MOUSE
trust MAC-ADDRESS-MOUSE
EOF
```

I switch the mouse to pairing mode, run the script and the mouse works again but I am looking for a permanent solution. When I run bluetoothctl as root in a terminal, suspend/resume and move the mouse bluetoothctl shows that it connects but it immediately disconnects:

[CHG] Device MAC-ADDRESS-MOUSE Connected: yes
[CHG] Device MAC-ADDRESS-MOUSE Connected: no

Any ideas how to resolve this issue?

Regards,
Gijsbert

---

### Post by Gijsbert_Wiesenekk on 2019-04-23
I finally found the workaround for this annoying issue. Add/set UserspaceHID to true in /etc/bluetooth/input.conf:

UserspaceHID=true

and restart the bluetooth service.

Regards,
Gijsbert

---

