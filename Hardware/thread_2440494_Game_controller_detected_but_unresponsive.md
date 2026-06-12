---
title: "Game controller detected but unresponsive"
date: 2020-04-11
forum: Hardware
---

### Post by Gridwalker on 2020-04-11
I have recently obtained a generic PS3 compatible USB controller, but my 19.10 box cannot detect any input from it.

When I run "lsusb" my system reports :
```
Bus 004 Device 008: ID 045e:028e Microsoft Corp. Xbox360 Controller

```

I have tried installing both xboxdrv and ubuntu-xboxdrv

With xboxdrv installed, jstest-gtk will report a controller is attached, but will not calibrate.
I get a similar result with ubuntu-xboxdrv installed, however jstest-gtk then reports 4 unresponsive controllers.

When I run "sudo xboxdrv --detach-kernel-driver" with the controller attached, I get the following output :
```
Controller:        Microsoft X-Box 360 pad
Vendor/Product:    045e:028e
USB Path:          004:008
Controller Type:   Xbox360

Your Xbox/Xbox360 controller should now be available as:
  /dev/input/js0
  /dev/input/event22
```

So it is definitely detected, as running the same command with the controller detached generates the following error :
```
-- [ ERROR ] ------------------------------------------------------
No Xbox or Xbox360 controller found
```


Can anybody advise on how to get this working?

---

### Post by Claus7 on 2020-04-14
Hello,

which is the application that you are trying to detect input from your controller? Are you sure, for example, that wine is configured accordingly in order to be able to use the controller? Have you enabled controller from gaming platforms?

Regards!

---

