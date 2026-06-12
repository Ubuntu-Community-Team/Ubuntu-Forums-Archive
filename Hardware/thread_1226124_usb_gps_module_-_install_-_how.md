---
title: "usb gps module - install - how"
date: 2009-07-29
forum: Hardware
---

### Post by bonfire89 on 2009-07-29
Hey all,

I'm setting up an ubuntu jaunty laptop for a coworker and he has a usb gps module he would like to use.

here is the lsusb output
```
Bus 003 Device 006: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port
```

I have install **gpsdrive** which I have had no success with, but I have also installed **tangogps** which has worked twice but it is hit or miss. Most of the time after reboot or when I plug it in it will not work.



How do I properly install it? how do I properly setup up? How do I * ?

Thanks!

---

### Post by rannable on 2009-07-29
i would check on the manufacturers website as some have linux support but tangogps is my fave but will not work on all gps units. failing everything bite the bullet and stick a windows virtual machine on your laptop for this purpose...

---

### Post by bonfire89 on 2009-08-04
hmmm we shall see. It is some no name unknown whatever. But I will see what I can do.

Thanks

---

### Post by River7471 on 2011-03-25
Anyone have any idea why my BU353 GPS puck works with TangoGPS and not with any other linux based program?

I can't get it to work in OpenCPN, Roadnav, and other linux nav programs.

---

### Post by River7471 on 2011-03-26
Never mind 

Found it.

[http://opencpn.org/setting_up_gps](http://opencpn.org/setting_up_gps)

If gpsd isn't running  use $ gpsctl -f -n  /dev/ttyUSB0

---

