---
title: "usb 3g modem in ubuntu 12.04"
date: 2012-04-23
forum: Hardware
---

### Post by werkman2 on 2012-04-23
i have a huawei usb 3g modem that worked perfectly in ubuntu 11.10, but after doing a clean install of ubuntu 12.04 the modem is not detected at all. but my phone and a icon cdma modem is working perfectly. what config file or other serrimg should i edit to use my 3g modem in ubuntu 12.04? thx

---

### Post by sanderj on 2012-04-23
With the USB modem plugged in, you could use "lsusb" to see the USB-ID of the device, and then google it. Maybe there's already a solution, or a bug report.

Or you could live-boot your Ubuntu 11.10 CD, check again that the USB-modem works, and then do a lsmod to see which driver is installed.

---

### Post by Zingam on 2012-04-23
I have Huawei device and I have upgraded from 11.10 to 12.04. And changed from Ubuntu to Xubuntu. The device works relatively stable.

BUT I need to unplug it and then plug it again each time I want to reconnect or it won't connect. Do not keep the device plugged in, when you boot. Connect it after the OS is up and running.

Also under Xfce the network manager applet does not display the proper icon when a mobile broadband connection has been established but it works.

---

### Post by codemaniac on 2012-04-23
Sakis 3g is an awesome little piece of script that can make your life a hell lot easier while connecting Usb modems .Few days back i was just trying all tricks of the book to connect my mincromax 3g modem but in vain , Ubuntu could not detect my 3g modem at all.
Sakis 3G came into rescue .
[http://www.sakis3g.org/#downloading](http://www.sakis3g.org/#downloading)

---

### Post by Malsasa on 2013-03-17
Is it happens only for me? Sakis3g web is not browseable. It seems like removed from server. Already 2 days I tried to open it.

---

