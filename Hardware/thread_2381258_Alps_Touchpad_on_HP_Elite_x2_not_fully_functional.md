---
title: "Alps Touchpad on HP Elite x2 not fully functional"
date: 2017-12-28
forum: Hardware
---

### Post by gontijo on 2017-12-28
Hi everyone, I've been trying to get my Alps Touchpad fully functional on my HP Elite x2. On Windows, it recognizes as much as 4 fingers, but on Ubuntu 17.10 it won't go over 2; therefore, I can't use the middle click functionality, which is something I do very often. I've searched quite a bit on Google and such, but trouble is most solutions I've found regard X11, and since I'm on Wayland those solutions don't apply. I've also verified that the driver being used is a generic usbhid, so therefore libinput seems to be unable to properly recognize its capabilities, as seen below:
```
$ libinput

Device:           Alps Alps Touchpad
Kernel:           /dev/input/event10
Group:            6
Seat:             seat0, default
Capabilities:     pointer 
Tap-to-click:     n/a
Tap-and-drag:     n/a
Tap drag lock:    n/a
Left-handed:      disabled
Nat.scrolling:    disabled
Middle emulation: n/a
Calibration:      n/a
Scroll methods:   button
Click methods:    none
Disable-w-typing: n/a
Accel profiles:   flat *adaptive
Rotation:         n/a

$ usb-devices

T:  Bus=01 Lev=02 Prnt=05 Port=00 Cnt=01 Dev#=  7 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=044e ProdID=120d Rev=04.05
S:  Manufacturer=Alps
S:  Product=Alps Touchpad
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=30mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid
```

I'm quite happy with the overall functionality of the system, since most of the system worked out of the box, but this is really bugging me. Anyone has any idea what I could do to sort this out?

---

### Post by gontijo on 2018-01-02
Doesn't anybody have any ideas on how to fix this issue?

---

### Post by Jan_Drewes on 2018-04-12
Hello,

I have the exact same problem.

Would you kindly say if you ever made any progress with this?

Cheers,
Jan

---

### Post by wildmanne39 on 2018-04-12
Hello Jan_Drewes, please start your own thread, you will have a much better chance of getting your issue resolved that way then posting in an old thread with no replies and the OP has not been here since January 2nd.

Thanks

---

