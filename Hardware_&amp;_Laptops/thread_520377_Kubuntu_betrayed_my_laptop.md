---
title: "Kubuntu betrayed my laptop"
date: 2007-08-08
forum: Hardware &amp; Laptops
---

### Post by arkhit on 2007-08-08
HI guy's,

            I have installed kubuntu 7.4 in my laptop. After the first but i checked all things are working fine. But after my second boot the Kubuntu get's hanged in login screen both mouse and keybord is not responding. In this situation anyone can help me to solve this issue. 

My Laptop config: 945 motherboard. 2GB RAM, nividia 7500, 120GB. lenovo 3000 y 500 series

Regards
arkhit

---

### Post by dougfractal on 2007-08-08
maybe xorg.conf issue.

boot into rescue mode
> startx

if it breaks rebuild xorg with
> sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by arkhit on 2007-08-09
hi,

As you said i enter in to the rescue mode and tried to type but the keyboard is not working. Any solution to solve this problem. But keyboard and touch pad all worked well before while i am booting as live cd.


help me!:roll:
Regards,
karthi

---

### Post by A-Sylum on 2007-08-09
try a usb keyboard or ps/2 it may be detected better :D

---

### Post by dougfractal on 2007-08-09
> As you said i enter in to the rescue mode and tried to type but the keyboard is not working

The keyboard is not working at boot prompt?
or at startx?

_Fix from liveCD._
mount kubuntu drive
sudo cp /etc/X11/xorg.conf /media/hdXX/etc/X11/xorg.conf

*replace hdXX with the correct value.*




My usb keyboard is not working at grub prompt, but the ps/2 does.

---

### Post by arkhit on 2007-08-09
the keyboard is working while i am selecting boot loader and editing the boot loader. (One important that useless vista home edition came with my laptop pre-installed is there any problem with that.)  Then as above mention i have the copy the file sudo cp /etc/X11/xorg.conf /media/hdXX/etc/X11/xorg.conf ...  the hdxx represents the / or root  partation. 


Thanks regards,
arkhit

---

### Post by dougfractal on 2007-08-09
> One important that useless vista home edition came with my laptop pre-installed is there any problem with that.)

ask around i don't know but if you've install it a bit late,  but should cause no probs to kubuntu.
[B]
from LiveCD[/B]

haxx is the partition you installed kubuntu on.   maybe (only guessing /dev/hda6)
sudo gparted   will tell you , look for ext3

you just need to mount it first.
GUI or
sudo mount /dev/hdaX  /media/hdaX

---

### Post by arkhit on 2007-08-10
Hi guys :(,
               I tried booting through live cd and i found that my mouse pad is not working so i used my usb mouse and found my mouse is working. Then  for the keyboard i could not do anything. Bad luck better in next version. Thank you guys for the help and support you provided


Regards,
arkhit

---

### Post by dougfractal on 2007-08-10
Hi arkhit

I was reading [SOLVED] I am new to Ubanthu please guide me :) [http://ubuntuforums.org/showthread.php?p=3108715](http://ubuntuforums.org/showthread.php?p=3108715)
so at what point did it go wrong?

> My Laptop config: 945 motherboard. 2GB RAM, nividia 7500, 120GB. lenovo 3000 y 500 series
[http://www-604.ibm.com/webapp/wcs/stores/servlet/ProductDisplay?productId=4611686018425277793&storeId=10000356&langId=356&categoryId=4611686018425052502&dualCurrId=1000105&catalogId=-356](http://www-604.ibm.com/webapp/wcs/stores/servlet/ProductDisplay?productId=4611686018425277793&storeId=10000356&langId=356&categoryId=4611686018425052502&dualCurrId=1000105&catalogId=-356)
 > **Processor**
Processor internal clock speed[1] 	1.73  GHz
Processor Type 	Intel Celeron M Processor 430
Internal L2 Cache Size 	1  MB
Front side bus 	533  MHz
 **Graphics Subsystem**
Graphics bus interface 	PCI Express
Connectors 	VGA

If you do this and post I may be able to help (This can be all done with mouse only! )
```

cd ~                     #  goto myhome
touch mylatop.info # create file
lsb_release -d > mylatop.info   # version
uname -r >> mylatop.info   # kernel
uptime >> mylatop.info    # time on
ps --no-headers -A -o "%cpu sz ucomm" | sort +0r | head  >>  mylatop.info  # condensed version **top**
lspci -nn >> mylatop.info   #   list hardware
free -m >>   mylatop.info    # display memory
cat /etc/X11/xorg.conf >>   mylatop.info   #  graphics file
```

please attach  "mylatop.info" to your post as it will be quite long

---

### Post by fredj on 2007-08-10
This is a confusing post so I'm not sure that I have understood it.
If you are using a USB keyboard then make sure that support for usb keyboards is
enabled in the bios. If it isn't then your keyboard may not work until ubuntu is loaded and
this will cause problems when you can't get ubuntu to load.

---

