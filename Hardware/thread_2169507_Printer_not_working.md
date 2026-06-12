---
title: "Printer not working"
date: 2013-08-22
forum: Hardware
---

### Post by Bachey on 2013-08-22
Hello ubuntu users!

I'm relatively new to ubuntu. It works seamlessly, but one thing I can't get to work is the printer. It's a Konica Minolta PagePro 1300W model. It's connected to the PC via USB. I'm using Ubuntu 13.04 64 bit. Thank you for reading.

Bachey

---

### Post by ibjsb4 on 2013-08-22
Have you installed the driver?

[https://apps.ubuntu.com/cat/applications/raring/printer-driver-min12xxw/](https://apps.ubuntu.com/cat/applications/raring/printer-driver-min12xxw/)

---

### Post by Bachey on 2013-08-22
Yes, I have this installed. But it still does not work.

---

### Post by Bachey on 2013-08-22
Any ideas?

---

### Post by ibjsb4 on 2013-08-22
Go to System Settings>Printers and check your settings.

Also check to see that the printer is being dectected in terminal:

```
lsusb
```

---

### Post by Bachey on 2013-08-23
Yes, it is detected. > Bus 004 Device 002: ID 0686:300c Minolta Co., Ltd PagePro 1300W

I tried to use cups according to a tutorial, but it still does not work. 

[IMG]http://ubuntuone.com/0U2OwgrSUYPaE9wKFQNSD6[/IMG]

---

### Post by kurt18947 on 2013-08-23
This is my default on Brother networked printers, no experience with Konica/Minolta or other brands.  I determine the I.P. address of the printer, make it static (or assign something like xxx.xxx.xxx.13:9100)  then in the 3rd line down -URI - I enter socket://xxx.xxx.xxx.xxx:9100 where x=i.p address.  This method might be somewhat archaic, I don't know but it has been pretty much bulletproof for me.

---

### Post by ibjsb4 on 2013-08-23
I found this (old) fix, could be worth a try.

[https://bugs.launchpad.net/ubuntu/+source/cupsys/+bug/30282/comments/18](https://bugs.launchpad.net/ubuntu/+source/cupsys/+bug/30282/comments/18)

Got a few more hits here

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Konica+Minolta+PagePro+1300W&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Konica+Minolta+PagePro+1300W&sa=Search&cof=FORID:9)

---

### Post by Bachey on 2013-08-31
Sorry about the late reply, I tried those tips, did not work. I also tried the printer on windows and it works fine, so it must be a driver problem. Please help me in this matter, I really need to set up this printer properly.

---

