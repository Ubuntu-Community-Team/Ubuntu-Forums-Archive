---
title: "ipod 3rd generation issue"
date: 2009-12-04
forum: Hardware
---

### Post by dolhotel on 2009-12-04
hi

i am using 64bit karmic and trying to use my 3rd generation ipod with firewire

1) the ipod is not detected when plugged in the ipod, and then i type "lsmod | grep sbp2", but it show sbp2 is not loaded

2) unplug ipod, and then type "modprobe sbp2" and then plug in ipod. and the type "dmesg", and no message is found related to ipod from dmesg

3) tried looking at /proc/bus/ , but could not find the ieee1394 diectory

anyone can help?

cheers

---

### Post by JoePits on 2009-12-05
edit: nevermind i thought u were talking about ipod touch.

---

### Post by IcarusR on 2009-12-05
Is this the firewire ipod ??

First make sure ieee1394 and ohci1394 modules are loaded
```
lsmod | grep 1394
```
plug ipod in & make sure sbp2 has loaded
```
lsmod | grep sbp2
```
If not.
```
sudo modprobe sbp2
```
Ipod shold now mount. 
If not remove all modules.
```
sudo modprobe -r ohci1394
```
The reload the three modules in this order
```
sudo modprobe ohci1394
sudo modprobe ieee1394
sudo modprobe sbp2
```
Ipod should now mount at /media/ipod (or something similar)
If it does not then unplug it, remove sbp2 & try again. Took me some time to get it to work. Works better on a PCMCIA card than the built in firewire on mt Tosh.


I believe you need to have libgpod3 & libgpod-common installed in order to use ipod.

Hope this all makes sense.

Good luck

---

### Post by dolhotel on 2009-12-09
IcarusR, thanks for the share, but it still does not work

my 3rd generation ipod used to work with the ubuntu 7, but after upgrade to ubuntu 9, then it fail to be reconized anymore. and after so many failure with karmic, almost want to give up this guy now

---

