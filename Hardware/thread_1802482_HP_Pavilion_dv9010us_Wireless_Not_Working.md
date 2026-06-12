---
title: "HP Pavilion dv9010us Wireless Not Working"
date: 2011-07-12
forum: Hardware
---

### Post by dodle on 2011-07-12
I have an HP Pavilion dv9010us with the Broadcom bcm4311 wireless card.

```
:~$ lspci | grep Broadcom
03:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
```

I have installed the Broadcom STA Wireless Driver along with b43-fwcutter and firmware-b43-installer, but I still cannot get it to work. 

I have looked over these threads about the dv9000 series:
[http://ubuntuforums.org/showthread.php?t=431815](http://ubuntuforums.org/showthread.php?t=431815)
[http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)
[http://www.linuxquestions.org/questions/linux-wireless-networking-41/howto-bcm43xx-broadcom-drivers-462995/page4.html](http://www.linuxquestions.org/questions/linux-wireless-networking-41/howto-bcm43xx-broadcom-drivers-462995/page4.html)
But these deal with older versions of Ubuntu.

The laptop has a hardware switch for wireless. The light is amber but should be blue.

```
:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


```

---

### Post by dodle on 2011-07-12
Thanks to wildmanne39 for helping me find the answer. 

The STA driver was causing the problem, so I un-installed it, along with b43-fwcutter and firmware-b43-installer, rebooted, re-installed b43-fwcutter and firmware-b43-installer and rebooted again. Works fine now.

---

