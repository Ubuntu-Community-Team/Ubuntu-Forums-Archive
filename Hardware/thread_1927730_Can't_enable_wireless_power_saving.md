---
title: "Can't enable wireless power saving ?"
date: 2012-02-18
forum: Hardware
---

### Post by fictivetoast on 2012-02-18
This should be a simple fix, but I can't seem to find a straight-forward answer anywhere.  Powertop indicates that one of the biggest power drains on my laptop (Lenovo x220) is the iwlan0.  Under the Powertop turntable though, I can't activate wireless power saving for interface iwlan0, and sure enough iwconfig shows "Power Management : off".

How the heck do I turn Power Management on?  And why the heck wouldn't it be on by default?

---

### Post by fictivetoast on 2012-02-18
"sudo iwconfig wlan0 power on" returns :


Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlan0 ; Operation not supported.

---

### Post by fictivetoast on 2012-09-10
Bump - I still seem unable to invoke wireless power saving on wlan0 for my Lenovo X220 (running 12.04 with all updates installed).  Indeed, disabling the network interface doesn't seem to actually conserve any power at all!

---

