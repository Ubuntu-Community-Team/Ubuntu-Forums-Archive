---
title: "Trouble in using USB serial"
date: 2013-01-06
forum: Hardware
---

### Post by boyiliao on 2013-01-06
I used  prolific PL2303 serial port 
My Ubuntu version is 12.04 LTS

>lsusb
Prolific Technology, inc. PL2303 Serial Port 

>lsmod | grep 2303
pl2303          17599 1
usbserial       37024 3 pl2303

It looks ubuntu get the HW, but i used "putty", "minicom", "cutecom". it looks like someone press the "enter" key continually, and i can't input any key, and then putty will crash.

I also used open to signle mode, and exec the "minicom" and  it woks fine .
Is there any special setting should i set under xwindows ?  thanks .

---

