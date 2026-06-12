---
title: "Can a router with a &quot;hidden&quot; SSID connect to an HP netboook's wireless RT3090?"
date: 2012-02-04
forum: Hardware
---

### Post by nowifi on 2012-02-04
An HP 110 netbook with a wireless RaLink RT3090 will not connect to a "hidden" router.
Is this a known problem or is there a fix?

For the wireless to work in Ubuntu, except as noted,  the following commands are needed:

```
[COLOR=Navy]sudo su
mkdir -p /etc/Wireless/RT2860STA/
touch /etc/Wireless/RT2860STA/RT2860STA.dat
service network-manager restart
exit[/COLOR]
```

There are several posts regarding this problem but apparently no solutions.
There are more details here: [http://ubuntuforums.org/showthread.php?t=1919987](http://ubuntuforums.org/showthread.php?t=1919987) .

---

