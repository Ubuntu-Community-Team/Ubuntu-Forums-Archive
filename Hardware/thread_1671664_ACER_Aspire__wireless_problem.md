---
title: "ACER Aspire  wireless problem"
date: 2011-01-20
forum: Hardware
---

### Post by surfingonmusic on 2011-01-20
i have an acer aspire 5741 with a broadcom BCM43225 802.11b/g/n network card running ubuntu 10.10 and i can't connect to wireless=/

i got the bcmwl-kernel-source driver from synaptic which didn't work
then did this tutorial        [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide/Devices](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide/Devices)               and STILL can't get it working

any help please? thanks a mill!

---

### Post by TBABill on 2011-01-20
Have you already gone to System>>>Administration>>>Hardware (or Additional Drivers if Ubuntu 10.10)? The system should recognize the device and offer 2 drivers. The STA should be the one you need. Just click activate, restart and see if it works.
 
If you have done all that the system should show the driver (it's called the wl module) listed in /etc/modules and you can check by doing ```
cat /etc/modules
```
 
If you see the driver there, but still unable to connect, first make sure it is "on", meaning to either turn on the switch if it has one or make sure the soft switch (function key combo) is enabled. If it is, try to ```
sudo rfkill list
``` and if either soft or hard blocked say YES, then ```
sudo rfkill unblock all
```

---

### Post by TBABill on 2011-01-20
Have you already gone to System>>>Administration>>>Hardware (or Additional Drivers if Ubuntu 10.10)? The system should recognize the device and offer 2 drivers. The STA should be the one you need. Just click activate, restart and see if it works.
 
If you have done all that the system should show the driver (it's called the wl module) listed in /etc/modules and you can check by doing ```
cat /etc/modules
```
 
If you see the driver there, but still unable to connect, first make sure it is "on", meaning to either turn on the switch if it has one or make sure the soft switch (function key combo) is enabled. If it is, try to ```
sudo rfkill list
``` and if either soft or hard blocked say YES, then ```
sudo rfkill unblock all
```

---

