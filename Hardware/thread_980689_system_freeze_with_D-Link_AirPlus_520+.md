---
title: "system freeze with D-Link AirPlus 520+"
date: 2008-11-13
forum: Hardware
---

### Post by hasanen on 2008-11-13
Hi
I got this problem with all distros that use the ACX driver , system freeze after no more than few minutes from starting up.....
At first the solution was to rmmod acx immediately after logging in....then I blacklisted the acx driver in /etc/modprobe.d/blacklist
And now I finally got the card working with ndiswrapper , I just inserted the windows driver CD and used the ndiawrapper gui to install the driver...so easy....now the card is working just fine. :)

---

