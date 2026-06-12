---
title: "Bug in Ndiswrapper Broadcom &quot;bcmn43xx64.inf&quot; Driver at wiki.ubuntuusers.de"
date: 2016-06-01
forum: Hardware
---

### Post by steffomix on 2016-06-01
I have found a Bug in the Broadcom bcm43xx.inf in [https://wiki.ubuntuusers.de/WLAN/Karten/Netgear/](https://wiki.ubuntuusers.de/WLAN/Karten/Netgear/)

The Package is here:
[https://wiki.ubuntuusers.de/WLAN/Chips%C3%A4tze/#bcm43xx](https://wiki.ubuntuusers.de/WLAN/Chips%C3%A4tze/#bcm43xx)

The Bug is in File bcmn43xx64.inf at Line 19:

```
%BCM4xx03_DeviceDesc% = BCM43XXN[COLOR=#ff0000]32[/COLOR], USB\VID_0846&PID_9011
```

should be:

```
%BCM4xx03_DeviceDesc% = BCM43XXN[COLOR=#ff0000]64[/COLOR], USB\VID_0846&PID_9011
```

The Bug cause a Message on "ndiswrapper -i bcmn43xx64.inf" the Driver is incomplete and will in effect not recognise WLan Sticks that should be supported.

If there is anyone who can fix and replace the File in wiki.ubuntuusers.de would be nice.

---

