---
title: "10 USB 3G Modem Attached, Then Ubuntu Get Confused"
date: 2011-11-12
forum: Hardware
---

### Post by robson9776 on 2011-11-12
[IMG]http://i34.photobucket.com/albums/d132/robson9776/modems.jpg[/IMG]

Hi guys,

I did some 'crazy' experiment with my PC this evening. I was attach 10 (ten) Huawei E173 modems - all are identical - one by one then reboot each time a modem attached.

Ubuntu Desktop 11.10 works detect those modems perfectly fine.. I see there are so many ttyUSB0... ttyUSB29 when I run this command :

> $ dmesg | grep tty

but when I shut down my PC and turn it on again, I only get ONE modem recognized. I don't get it, why Ubuntu can't detect my modems? it was perfectly fine before I it shut down.

I didn't unplug or change the ports or whatsoever... just shut down then everything seems not detected by Ubuntu after it turns on.

PLEASE NOTE : I'm not planning this to connect to the internet. just trying to make my Ubuntu detect my modems as ttyUSBx...

any clue how to make this things works, even after reboot / poweroff? thanks

---

