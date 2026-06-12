---
title: "suspend wifi"
date: 2012-08-08
forum: Hardware
---

### Post by icegood on 2012-08-08
In my laptop asus k52dr seems finally suspend works but from time to time i've got:
cat /var/log/pm-suspend.log  | grep wpa:
```

Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
root@ubuntu:/boot/grub# vi /usr/lib/pm-utils/sleep.d/60_wpa_supplicant 
root@ubuntu:/boot/grub# vi /usr/lib/pm-utils/sleep.d/60_wpa_supplicant 

```

So, sometimes script 60_wpa_supplicant works well, sometimes fails.
Cat /usr/lib/pm-utils/sleep.d/60_wpa_supplicant:
```

#!/bin/sh

# /etc/pm/sleep.d/60_wpa_supplicant
# Action script to notify wpa_supplicant of pm-action events.

PATH=/sbin:/usr/sbin:/bin:/usr/bin

WPACLI=wpa_cli

case "$1" in
    suspend|hibernate)
        $WPACLI suspend
        ;;
    resume|thaw)
        $WPACLI resume
        ;;
esac

exit 0

```

What it could be?

---

