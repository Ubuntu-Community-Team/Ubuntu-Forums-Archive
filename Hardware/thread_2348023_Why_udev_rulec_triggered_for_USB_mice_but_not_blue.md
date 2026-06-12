---
title: "Why udev rulec triggered for USB mice but not bluetooth mice"
date: 2016-12-30
forum: Hardware
---

### Post by zhangweiwu on 2016-12-30
The bluetooth mouse's information:

```

$ udevadm info -a -p `udevadm info -q path /dev/input/mouse3`

  looking at device '/devices/virtual/misc/uhid/0005:17EF:6060.0005/input/input26/mouse3':
    KERNEL=="mouse3"
    SUBSYSTEM=="input"
    DRIVER==""

  looking at parent device '/devices/virtual/misc/uhid/0005:17EF:6060.0005/input/input26':
    KERNELS=="input26"
    SUBSYSTEMS=="input"
    DRIVERS==""
    ATTRS{name}=="Lenovo Mice N700"
    ATTRS{phys}=="B8:8A:60:56:E4:3C"
    ATTRS{properties}=="0"
    ATTRS{uniq}=="D5:94:54:38:3D:5D"

  looking at parent device '/devices/virtual/misc/uhid/0005:17EF:6060.0005':
    KERNELS=="0005:17EF:6060.0005"
    SUBSYSTEMS=="hid"
    DRIVERS=="hid-generic"
    ATTRS{country}=="00"

  looking at parent device '/devices/virtual/misc/uhid':
    KERNELS=="uhid"
    SUBSYSTEMS=="misc"
    DRIVERS==""

```

The udev rules I tried:
```

$ cat /etc/udev/rules.d/lenovo.rules
KERNEL=="hidraw*", SUBSYSTEM=="hidraw", ATTRS{uniq}=="D5:94:54:38:3D:5D", SYMLINK+="N700"
KERNEL=="hidraw*", SUBSYSTEM=="hidraw", ATTRS{address}=="d5:94:54:38:3d:5d", SYMLINK+="N700"
SUBSYSTEM=="input", SUBSYSTEMS=="input", SUBSYSTEMS=="hid", ATTRS{name}=="Lenovo Mice N700", SYMLINK+="N700"

```
None of the three rules are tirggered, since evidently they are not mentioned in syslog (when udev log-priority is set to 'debug') and no /dev/N700 show up.

I repeated the test with a USB mouse, and everything worked - the rule is mentioned in syslog, reported as returning successfully, and new /dev symlink showed up. The rule that worked for USB mouse is:

SUBSYSTEM=="input", SUBSYSTEMS=="usb", ATTRS{idVendor}=="046d", ATTRS{idProduct}=="c063", SYMLINK+="usbmouse"

I wish I can adapt the USB mouse's rule directly for the bluetooth, but of course I can't because bluetooth device doesn't ahve idVendor/idProduct, at least not in the output of `udevadmin info`

Using Ubuntu 16.10, Thanks!

---

### Post by zhangweiwu on 2017-01-02
It turns out that the rule which works is this:

```

SUBSYSTEM=="input", SUBSYSTEMS=="input", ATTRS{name}=="Lenovo Mice N700", SYMLINK+="N700"

```

Reason: the rule should only match one parent, not its parent's parent (SUBSYSTEMS="hid").

---

### Post by mörgæs on 2017-01-02
Thanks for posting the solution. Please use Thread Tools for marking the thread 'solved'.

---

### Post by zhangweiwu on 2017-01-02
Done. Thought that they are the same.

---

### Post by mörgæs on 2017-01-02
No, the real solved flag can be used for filtering if you go to the Advanced Search page.

---

