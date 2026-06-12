---
title: "Wireless Card Possibly Broken?"
date: 2008-09-10
forum: Hardware
---

### Post by rpros1 on 2008-09-10
The past week, I had tried to make a hackintosh off of my Dell Insipiron 1501 and that didn't go according to plan and could not get it to work so...  I returned to Hardy, installed it and everything like I had done a thousand times, used this guide, which has worked for me plenty of times before - [http://www.ubuntu1501.com/2008/04/overview-of-ubuntu-804-hardy-heron-on.html](http://www.ubuntu1501.com/2008/04/overview-of-ubuntu-804-hardy-heron-on.html) - to install my drivers, tried this numerous times, tried reinstalling hardy again, low and behold. Nothing.  I tried using the Wi-Fi toggle key, Fn + F2, the light remains off.  I've tried other guides as well and can not figure what the problem is.  When i enter iwconfig wlan0 or iwconfig in the terminal i get

-laptop:~$ iwconfig wlan0
wlan0     No such device

r-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.
-laptop:~$ 

I really don't know what to do, is there any command that can toggle on my card, which I think I have already tried.  Also, in the Network Manager there is no Wireless subcategory?  Ideas anyone?  Thanks for your time.

---

### Post by sergiom99 on 2008-09-10
try to reseat the wifi card.
post the output of lspci to see if its being detected by your system.

---

### Post by Crafty Kisses on 2008-09-10
I'd also like to see the results of this command:
```
lshw -C network
```

---

### Post by rpros1 on 2008-09-14
I fixed the problem, I just opened up the case and recieted the wireless card.  Thanks for the help though.

---

