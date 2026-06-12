---
title: "Novatel MC760 stop automount"
date: 2010-05-05
forum: Hardware
---

### Post by DeathFire on 2010-05-05
I have a Novatel MC760 which automounts a fake ISO image each time it is plugged in.  I cannot use the modem until I eject the ISO.  I know that I can use the noauto command to stop the automatic mounting if I have a UUID.  However I cannot find the UUID for this device.  I have tried blkid and it only shows my other devices which I have connected.

Do you have any suggestions on how I can stop an automount without a UUID or have other suggestions to find the UUID?

I am using 10.04. This was also a problem on 9.10.

---

### Post by dino99 on 2010-05-05
try to tweak it with MountManager

maybe modemmanager can help too

something to see:
[http://forums.opensuse.org/get-help-here/network-internet/431467-novatel-mc760.html](http://forums.opensuse.org/get-help-here/network-internet/431467-novatel-mc760.html)

---

### Post by DeathFire on 2010-05-05
Thanks for the info, by reading that I found my way through to the solution.

```
sudo apt-get install usb-modeswitch
```Now when I plug the modem in it detects properly and automatically connects to the Internet. Super slick!

---

