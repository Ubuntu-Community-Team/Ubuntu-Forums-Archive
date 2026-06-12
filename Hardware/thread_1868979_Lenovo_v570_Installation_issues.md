---
title: "Lenovo v570 Installation issues"
date: 2011-10-25
forum: Hardware
---

### Post by vduke on 2011-10-25
I just bought a Lenovo V570 today, and have been banging my head on as to why I cannot get ubuntu to boot.

Installation goes fine then I get it cannot find the media. 

Has anyone out there gotten Ubuntu to fresh install on a lenovo v570 ?

not to sound scattered but it's 3:16am at this point and my brain is fried.

I tried making the 100mb EFI partition, setting grub boot 1 on SDA nothing.

I'm at a loss here.. I will probably take it back to bestbuy and exchange it since Lenovo Tech support was no help either.

---

### Post by JiangHongTiao on 2011-11-02
Hi, did you solve it? Because I have the same problem and cannot handle it :-/

---

### Post by JCoop on 2011-11-02
I may have answered this question already. Here is a link. Let me know if you have any questions:


[http://phoronix.com/forums/showthread.php?50038-Updated-and-Optimized-Ubuntu-Free-Graphics-Drivers](http://phoronix.com/forums/showthread.php?50038-Updated-and-Optimized-Ubuntu-Free-Graphics-Drivers)

---

### Post by Drnoob on 2011-11-08
I did wubi because I like to run windows too and it downloaded fine except the fact that it would not connect to wireless which was an easy fix. only other issue is adobe flash can't get it to work....got flash to work by going to  browser downloads and downloading flash aid from firefox. :o
-to fix wireless
```
  rfkill list all
```if there is an acer-wmi its trying to read you need to get rid of it.
**this will get rid of the acer-wmi.**
 ```
  **sudo rmmod -f acer-wmi **
```you can run (rfkill list all) again to see if you got rid of the acer-wmi if you like.


this makes the changes permanent.
```
 sudo su
``````
  *echo "blacklist acer_wmi" >> /etc/modprobe.d/blacklist.conf*
``````
 exit
```p.s. if you dont have rfkill which you should its
 ```
 yum install rfkill
```

---

