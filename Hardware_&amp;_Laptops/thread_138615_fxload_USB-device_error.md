---
title: "fxload USB-device error"
date: 2006-03-02
forum: Hardware &amp; Laptops
---

### Post by gosh on 2006-03-02
I try to set up my MidiSport1x1 USB device following this HowTo [http://www.ubuntuforums.org/showthread.php?t=96506](http://www.ubuntuforums.org/showthread.php?t=96506), but get this message when i try to load:

```
jos@ubuntu:~/usbmidi$ sudo fxload -I /etc/firmware/ezusbmidi1x1 -D /proc/bus/usb/001/003
/etc/firmware/ezusbmidi1x1: unable to open for input.

``` 
It looks like I don't have the rights to write of read that device.
How can I change this?

---

### Post by gosh on 2006-03-05
I've found it:

The command should read:
```
~/usbmidi$ sudo fxload -I /etc/firmware/ezusbmidi1x1.ihx -D /proc/bus/usb/001/003
```

---

