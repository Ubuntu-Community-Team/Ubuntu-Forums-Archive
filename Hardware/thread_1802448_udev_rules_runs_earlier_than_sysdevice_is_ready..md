---
title: "udev rules runs earlier than /sys/device is ready."
date: 2011-07-11
forum: Hardware
---

### Post by legendbb on 2011-07-11
I was trying to speed up thinkpad trackpoint.

Set /etc/udev/rules.d/10-trackpoint.rules as:
[COLOR="DarkGreen"]SUBSYSTEM=="serio", DRIVER=="psmouse",  ATTR{speed}="220", ATTR{sensitivity}="190"[/COLOR]

Verified by calling # udevadm trigger
it works fine, but does't work on system boots.

/var/log/syslog:
```
[COLOR="DarkGreen"]Jul 11 22:31:19 t60p udevd-work[356]: error opening ATTR{/sys/devices/platform/i8042/serio1/serio2/speed} for writing: No such file or directory
Jul 11 22:31:19 t60p udevd-work[356]: error opening ATTR{/sys/devices/platform/i8042/serio1/serio2/sensitivity} for writing: No such file or directory[/COLOR]
```

It seems when rules are called, the /sys/devices/platform/i8042/serio1/serio2 is not ready yet.

Also, try directly assigning {speed} & {sensitivity} values in /etc/rc.local, same situation "No such file or directory"

But after user login, just call # udevadm test /sys/... or # udevadm trigger, it works.

Check /sys/devices/platform/i8042/serio1/serio2/speed | sensitivity files they are actually newer than those timestamps in syslog.

Could not find documentation explaining how /sys/devices system is generated upon system boot, nor when and how udev rules are called on system boot.

Anyone, please share your knowledge, or simply point me to some useful documentation. I need to figure out these.

Great thanks,
:popcorn:

---

