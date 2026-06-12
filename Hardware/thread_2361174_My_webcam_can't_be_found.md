---
title: "My webcam can't be found"
date: 2017-05-13
forum: Hardware
---

### Post by mollie4168 on 2017-05-13
I tried to use both facebook messenger and skype yesterday and realized that my webcam does not work--Skype couldn't find it.  Cheese says it cannot find a device.  I'm not sure where to start to try and fix this.

I did a fresh install of 16.04 in February.  I have a built in camera on a System76 laptop.  In the past (before February), the camera has worked fine, so I'm unsure if it's the hardware or ubuntu.

I did dmseg, and the end of the output was the following:

```
 22.848860] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   22.848863] Bluetooth: BNEP filters: protocol multicast
[   22.848867] Bluetooth: BNEP socket layer initialized
[   28.434582] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[   28.434680] iwlwifi 0000:03:00.0: L1 Enabled - LTR Enabled
[   28.434938] iwlwifi 0000:03:00.0: L1 Enabled - LTR Enabled
[   28.651131] iwlwifi 0000:03:00.0: L1 Enabled - LTR Enabled
[   28.651394] iwlwifi 0000:03:00.0: L1 Enabled - LTR Enabled
[   28.665234] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[   28.668499] IPv6: ADDRCONF(NETDEV_UP): enp4s0f2: link is not ready
[   28.866065] r8169 0000:04:00.2 enp4s0f2: link down
[   28.866125] IPv6: ADDRCONF(NETDEV_UP): enp4s0f2: link is not ready
[   29.544967] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[   36.032716] wlp3s0: authenticate with 60:e3:27:88:08:4e
[   36.035671] wlp3s0: send auth to 60:e3:27:88:08:4e (try 1/3)
[   36.036320] wlp3s0: authenticated
[   36.040285] wlp3s0: associate with 60:e3:27:88:08:4e (try 1/3)
[   36.041236] wlp3s0: RX AssocResp from 60:e3:27:88:08:4e (capab=0x1011 status=0 aid=2)
[   36.043280] wlp3s0: associated
[   36.043336] IPv6: ADDRCONF(NETDEV_CHANGE): wlp3s0: link becomes ready
[   39.706274] Bluetooth: RFCOMM TTY layer initialized
[   39.706282] Bluetooth: RFCOMM socket layer initialized
[   39.706286] Bluetooth: RFCOMM ver 1.11
[  376.603365] psmouse serio2: Touchpad at isa0060/serio2/input0 lost sync at byte 6
[  376.619458] psmouse serio2: Touchpad at isa0060/serio2/input0 - driver resynced.


```

Reading the terminal is not my strong suit, but I did not see anything that seemed to indicate my camera.

Thanks for any assistance.

---

### Post by #&amp;thj^% on 2017-05-13
By any chance have you tried reactivating the camera with "Fn+<Camera Key>"
If that don't work run this from the terminal:
```
lsmod
```
Post back the return (copy and Paste) here so we can have a look. (Code tags)

---

### Post by mollie4168 on 2017-05-15
FN + camera key worked!  Thanks!

---

