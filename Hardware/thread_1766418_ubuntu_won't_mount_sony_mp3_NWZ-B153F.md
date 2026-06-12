---
title: "ubuntu won't mount sony mp3 NWZ-B153F"
date: 2011-05-24
forum: Hardware
---

### Post by rukiaEnix on 2011-05-24
Hello, I'm having this annoying issue with Ubuntu 11.04, I plug in my sony mp3 player and it doesn't mount it automatically (yes I have automatically mounting enable) I have been trying to mount it with console but I don't know how because when mounting with console I always do this:

```

mount /dev/sdb(number) /media/whatever 

```

and it always work, but now I can't because at /dev there isn't any sdb device, and this problem appears only with the mp3 because when plugging any other usb mass storage device I can see sdb devices at /dev.

What I want to do is mounting my mp3 with the device ID because Ubuntu it's recognizing my device, I can see it with:

```

$ lsusb
Bus 002 Device 011: ID 054c:04be Sony Corp. 
Bus 002 Device 003: ID 0c45:6481 Microdia 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

If someone could tell me how to mount it using the device ID please. Or maybe it's and 11.04 issue, because I have other laptop with 10.04 and I don't have problems plugging my mp3.

---

### Post by rukiaEnix on 2011-05-24
Issue solved, I don't know what happen, but I just plugged in my mp3 to another pc with Ubuntu 9.04 and it was automatically mounted which it made me feel even more annoy.
But then I was wondering if it may be something to do with nautilus or some graphical issue, so I close my session at the laptop with the problem (Ubuntu 11.04) and start it again but in Ubuntu mode ( I was logged in with Ubuntu classic mode) then I plugged in the mp3 and there it was! automatically mounted so then I unplugged it close and start again with classic mode then I plugged in it again and there it was again! I don't know what was the thing that fix it, maybe it was something to do with the graphic interface but now everything is fine. Still it would be useful to know other ways of mounting devices.

---

### Post by Tootler on 2011-06-20
I have had the same problem with a Sony Walkman NWZ-A816 mp3 player. 

This thread [http://ubuntuforums.org/showthread.php?p=10962220#post10962220](http://ubuntuforums.org/showthread.php?p=10962220#post10962220)

Suggested ensuring you have quit rhythmbox. If you have a rhythmbox icon in the panel at the top right, click on it and select "Quit". That did the trick for me.

Geoff

---

