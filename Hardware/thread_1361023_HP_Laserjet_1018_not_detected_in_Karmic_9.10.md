---
title: "HP Laserjet 1018 not detected in Karmic 9.10"
date: 2009-12-21
forum: Hardware
---

### Post by TKoorn on 2009-12-21
I have a laserjet 1018 which used to work under jaunty. It was temperamental, but it worked. Under Karmic I can't even get it to be detected by hplip or cups. I can see it listed as a usb device.

lsusb says:
Bus 001 Device 008: ID 03f0:4117 Hewlett-Packard Printing Support

but no printing setup util sees it.

Does anybody have any ideas of how to fix this?

---

### Post by drs305 on 2009-12-21
My LJ1000 was very tempermental too. Even though it was detected by "lsusb" I eventually got recognized by CUPS when I disconnected it and then recycled the power as well.   You should be so lucky. ;-)

---

### Post by LinuxDeal on 2009-12-21
[http://ubuntuforums.org/showthread.php?t=1265875](http://ubuntuforums.org/showthread.php?t=1265875)

---

