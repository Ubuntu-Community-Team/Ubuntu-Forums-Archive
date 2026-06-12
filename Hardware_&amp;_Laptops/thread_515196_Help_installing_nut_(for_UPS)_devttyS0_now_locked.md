---
title: "Help installing nut (for UPS) /dev/ttyS0 now locked"
date: 2007-08-01
forum: Hardware &amp; Laptops
---

### Post by Fraoch on 2007-08-01
It looks like the Bulldog software that came with my new Belkin F6C1200-UNV UPS won't install (see [http://ubuntuforums.org/showthread.php?t=514891](http://ubuntuforums.org/showthread.php?t=514891) ) so I've been trying to get nut going all day.

I got *so* close.  I abandoned trying to do it by USB and tried serial, and when I used the belkinunv driver, upsdrvctl start waited and said "No response from UPS" several times, then "Invalid data from UPS" then "Garbage data from UPS" and finally "Can't connect to UPS".

I took this to mean that I was using the right port but I figured I was using the wrong driver so I consulted this: [http://www.networkupstools.org/compat/stable.html](http://www.networkupstools.org/compat/stable.html) which said to use the megatec_usb driver but that does not come with nut 2.0.5 (the latest from the Ubuntu repos), it looks like it comes with nut 2.2.

I tried the megatec driver, which does come with nut 2.0.5, but now I get:

```
mark@Sauron:~$ upsdrvctl start
Network UPS Tools - UPS driver controller 2.0.5
Network UPS Tools - Megatec protocol driver 1.5 (2.0.5)
Carlos Rodrigues (c) 2003-2006

/dev/ttyS0 is locked by another process
Driver failed to start (exit status=1)
```

Aaargh!  It looks like my previous attempt has locked the port!  This behaviour persists after a reboot.

How do I unlock the port or is there anything else I should be doing?

Next step: uninstall nut 2.0.5, compile and install nut 2.2, but if I have to use the USB drivers I don't have much hope.  I have lots of USB problems on this machine, and lsusb suspiciously doesn't list a Belkin UPS when I connect the USB port, it lists a device with vendor ID 0665:5161.  0665 is on the right track though, note in the nut compatibility list: "Belkin Universal UPS F6C1100-UNV USB (2007 models, vendor id: 0665)"

---

