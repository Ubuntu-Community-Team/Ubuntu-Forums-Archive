---
title: "Lenovo x301 (wifi problem!!!)"
date: 2012-05-16
forum: Hardware
---

### Post by brutser on 2012-05-16
Hi all ! Just decided to install Ubuntu 12.04 on my Lenovo X301 as dual boot with Windows 7.
I first 'tested' from the usb installation, then from test mode installed Ubuntu.
Wifi was working normal, connection smoothly, speed like expected.
Decided to do few updates after installation and during this process wifi failed suddenly.
With wire connection completed the updates, but wifi still not working.

After a day, decided to install 64 bits Ubuntu, same thing happened.

Got IP from router's dhcp, but cannot even reach the gateway (router).

Found several posts on wifi problems with 12.04 but I have no idea how to solve it or what commands to run to find more information about it.

product: Ultimate N Wifi Link 5300
vendor: Intel Corporation

How can I fix this without trying solutions for other wifi products (like they suggest in other posts I found on the similar problem) ?

Thank you for advices and tips what to do, or where to look ! ;)

PS. After rebooting the wifi works initially, just to die after random number of minutes (usually ~10mins)

---

### Post by ts3 on 2012-05-16
> **brutser said:**
> With wire connection completed the updates, but wifi still not working

Hi, I know very little about wireless cards other than the one I have but I'd suggest running in terminal

```
lspci -nn
```

The output shows more info about the wireless card and you can look for a solution using more specific search terms.  

You can also take a look at [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

It's a good intro guide to getting acquainted with the wireless on a particular computer.

In the meantime one of the wireless gurus might chance by this thread and give you more help :)

---

