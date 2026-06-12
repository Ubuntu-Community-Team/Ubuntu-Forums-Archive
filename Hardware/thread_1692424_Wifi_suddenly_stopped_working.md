---
title: "Wifi suddenly stopped working"
date: 2011-02-21
forum: Hardware
---

### Post by Danicek on 2011-02-21
Hello,

So being first time Linux user, I've installed Ubuntu one my laptop (Compaq Presario CQ60). Everything worked great right out of the box for few weeks. Then suddenly wifi stopped working. I'm not aware of any changes or anything I would do that could cause this.

I'm running release 10.10.

iwconfig says:

lo          no wireless extensions.
eth0      no wireless extensions.
wlan0    IEEE 802.11bg ESSID:off/any
            Mode: Managed Access point: Not-Associated Tx-Power=off
            Retry long limit: 7 RTS thr: off  Fragment thr: off
            Encryption key:off
            Power Management: off

The laptop has dedicated wifi on/off button. This button indicates wifi is on. However pressing it has no impact (as it used to under Windows) and no effect on iwconfig output.

Other laptops are able to use the wifi router, so it is not problem with the router.

I've tried few things I could find on this forums but with no luck.

Any help would be appreciated.

---

### Post by Danicek on 2011-02-21
Ok, so 

rfkill unblock all 

fixed the issue.

Why? What does this command do?

---

### Post by bapoumba on 2011-02-21
[http://www1.ubuntuforums.org/showthread.php?p=10409652](http://www1.ubuntuforums.org/showthread.php?p=10409652)
Maybe ?

---

