---
title: "Issues with an old Synaptics touchpad"
date: 2015-10-09
forum: Hardware
---

### Post by mariosangiorgio on 2015-10-09
Hello, my laptop (Running Ubuntu 15.4) has an old Synaptics touchpad. These are the device details I got from /proc/bus/input/devices:
```
I: Bus=0011 Vendor=0002 Product=0007 Version=01b1
N: Name="SynPS/2 Synaptics TouchPad"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input6
U: Uniq=
H: Handlers=mouse0 event4 
B: PROP=1
B: EV=b
B: KEY=420 30000 0 0 0 0
B: ABS=11000003
```

Sometimes when the computer goes to sleep and I wake it up the TouchPad works weirdly. I can move the pointer but I cannot click. Could it be that there is something preventing it from waking up correctly?

Also, I had a look at the logs and I found messages like:```

Oct  9 19:28:29 Stormy kernel: [  761.029913] psmouse serio1: TouchPad at isa0060/serio1/input0 lost sync at byte 4
Oct  9 19:28:29 Stormy kernel: [  761.034374] psmouse serio1: TouchPad at isa0060/serio1/input0 lost sync at byte 1
Oct  9 19:28:29 Stormy kernel: [  761.039649] psmouse serio1: TouchPad at isa0060/serio1/input0 lost sync at byte 1
Oct  9 19:28:29 Stormy kernel: [  761.041160] psmouse serio1: TouchPad at isa0060/serio1/input0 lost sync at byte 1
Oct  9 19:28:29 Stormy kernel: [  761.044190] psmouse serio1: TouchPad at isa0060/serio1/input0 lost sync at byte 1
Oct  9 19:28:29 Stormy kernel: [  761.044195] psmouse serio1: issuing reconnect request
Oct  9 19:28:30 Stormy kernel: [  761.919983] psmouse serio1: synaptics: queried max coordinates: x [..5182], y [..4518]
```

Has anybody had these issues? How could I solve them?

Please let me know if I can give you some other information useful to diagnose the issue.

---

