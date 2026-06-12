---
title: "Problem with Samsung external DVD burner"
date: 2014-10-07
forum: Hardware
---

### Post by spinitch2 on 2014-10-07
Hi,
I can't get a SAMSUNG SE-208 external DVD burner to work. It won't open and I can't get my laptop to see it. Works fine with my desktop running Windoze 7. I’m running Xubuntu 12.04 on a really old Dell laptop. I’ve tried some of the commands suggested in [**this thread**]("http://ubuntuforums.org/showthread.php?t=1448072"): 

```
lsusb
dmesg | tail
ls /dev/sr*
```


Any ideas?
Thanks

```

mrm@mrm-Latitude-D500:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
mrm@mrm-Latitude-D500:~$ dmesg | tail
[   27.768071] type=1400 audit(1412678029.121:18): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=841 comm="apparmor_parser"
[   27.783379] type=1400 audit(1412678029.137:19): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer//sanitized_helper" pid=841 comm="apparmor_parser"
[   27.819341] type=1400 audit(1412678029.173:20): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=849 comm="apparmor_parser"
[   27.826414] type=1400 audit(1412678029.181:21): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=849 comm="apparmor_parser"
[   27.852169] type=1400 audit(1412678029.209:22): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=851 comm="apparmor_parser"
[   29.680675] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   29.688173] [drm] GMBUS timed out, falling back to bit banging on pin 5 [i915 gmbus dpb]
[   30.597375] lib80211_crypt: registered algorithm 'CCMP'
[   30.605150] lib80211_crypt: registered algorithm 'TKIP'
[   41.128144] eth1: no IPv6 routers present
mrm@mrm-Latitude-D500:~$ ls /dev/sr*
/dev/sr0
mrm@mrm-Latitude-D500:~$ udisks --mount /dev/sr0
Mount failed: Error mounting: mount: no medium found on /dev/sr0



```

---

### Post by MartyBuntu on 2014-10-07
Both USB plugs are plugged into known working USB ports? Not using a USB hub?

---

### Post by spinitch2 on 2014-10-07
Yup, the ports on the laptops work with usb sticks and DVDs mount from the samsung to the desktop. Could it be that the drive needs usb 2.0 and the laptop ports are 1.0?

---

### Post by Vladlenin5000 on 2014-10-07
> **spinitch2 said:**
> Could it be that the drive needs usb 2.0 and the laptop ports are 1.0?

Yes.
You can't use any USB optical drive with anything less than USB2.0 and expect it to work. At best, it works for reading only and the speed won't be reliable if it works at all...

(EDIT)
However, a Latitude D500 has USB2.0 ports and its hub is shown in your *lsusb.*

---

