---
title: "Connecting an mx master mouse to 20.04 fails, was working with 18.04 previously"
date: 2020-04-23
forum: Hardware
---

### Post by egandt on 2020-04-23
I'm trying to connect my mx master mouse via bluetooth.  I have verified using a headset that bluetooth works, but for some reason the mouse fails to work, it connects for about a second then disconnects.
```

[bluetooth]# devices
Device E3:E0:29:F3:B0:E3 MX Master
[bluetooth]# connect E3:E0:29:F3:B0:E3
Attempting to connect to E3:E0:29:F3:B0:E3
[CHG] Device E3:E0:29:F3:B0:E3 Connected: yes
[CHG] Device E3:E0:29:F3:B0:E3 Connected: no
Failed to connect: org.bluez.Error.Failed
[bluetooth]# trust E3:E0:29:F3:B0:E3
Changing E3:E0:29:F3:B0:E3 trust succeeded
[bluetooth]# pair E3:E0:29:F3:B0:E3
Attempting to pair with E3:E0:29:F3:B0:E3
[CHG] Device E3:E0:29:F3:B0:E3 Connected: yes
[CHG] Device E3:E0:29:F3:B0:E3 Connected: no
Failed to pair: org.bluez.Error.AuthenticationCanceled
[bluetooth]# info E3:E0:29:F3:B0:E3
Device E3:E0:29:F3:B0:E3 (random)
        Name: MX Master
        Alias: MX Master
        Appearance: 0x03c2
        Icon: input-mouse
        Paired: no
        Trusted: yes
        Blocked: no
        Connected: no
        LegacyPairing: no
        UUID: Human Interface Device    (00001812-0000-1000-8000-00805f9b34fb)
[bluetooth]#


```
It has to be the mouse that is canceling the connection, but I have no clue where to go from here?  I might mention that it works fine in Windows.

ERIC

---

### Post by apoullet-dev on 2020-05-30
I have the exact same issue with my MX Master 3 mouse after upgrading from 18.04 to 20.04. Updating Bluez to 5.54 did not help.

---

