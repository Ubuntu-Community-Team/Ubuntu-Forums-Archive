---
title: "Amilo a1655g wlan problem"
date: 2006-07-19
forum: Hardware &amp; Laptops
---

### Post by Raucom on 2006-07-19
Hi,

I am trying to enable wifi on this laptop because it is off by default. It is controlled by a key above keyboard. My problem is that i have a software that will enable/disable wlan, but i cant compile it..

I downloaded software from [http://www.marvec.org/amilo](http://www.marvec.org/amilo), unpacked it and when i do make, following error appears:
make -C /lib/modules/2.6.15-26-386/build SUBDIRS=/home/manko/wlansoft/fsaa1655g modules
make[1]: Entering directory `/lib/modules/2.6.15-26-386/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.15-26-386/build'
make: *** [default] Error 2

I have installed gcc, kernel header and a lot of stuff with apt-get. I have managed to compile ndiswrapper, although i had to make command : make KSRC=kernel_path ..

I hope that someone can help me.

Thanks in advance.

---

### Post by Cerb on 2007-04-25
same here and  sudo modprobe fsaa1655g says

FATAL: Error inserting fsaa1655g (/lib/modules/2.6.20-15-generic/kernel/net/wireless/fsaa1655g.ko): Invalid module format

---

### Post by freak101 on 2007-05-02
Try with acer_acpi 
[http://code.google.com/p/aceracpi/](http://code.google.com/p/aceracpi/)

---

