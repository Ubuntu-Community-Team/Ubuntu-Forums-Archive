---
title: "Wireless drivers"
date: 2012-05-13
forum: Hardware
---

### Post by Beamer180 on 2012-05-13
I know there is a lot of information out there on how to do this but none of seems to be working. I picked up a used Dell Lattitude D600 after my university upgraded one of its computer labs.

First I tried installing a legacy a b43-fwcutter (or something simiiliar I don't remember the exact name). The first try of this did not work I was missing son dependancies so I downloaded libc6 and tried installing the driver again and it worked.

Now that the driver is installed when I run lshw -C network it shows that I am using driver driver=b43legacy driverversion=3.0.0-17-generic but it says it is disable.

This makes it sound like to me that I have the driver installed but I don't have the the device enabled. I have been scratching my head for days trying to get this wireless card installed. Any help would be greatly appreciated.

I am running Ubuntu 11.10

If I need to give more information please let me know.

---

### Post by Mopar1973Man on 2012-05-13
I don't know if this will work in your case but worth a try... It would for my little USB Netgear wireless... (Netgear WG111v3)

[http://www.itechtalk.com/thread6579.html](http://www.itechtalk.com/thread6579.html)

---

