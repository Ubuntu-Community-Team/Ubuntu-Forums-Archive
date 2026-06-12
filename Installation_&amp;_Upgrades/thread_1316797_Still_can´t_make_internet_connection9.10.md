---
title: "Still can´t make internet connection/9.10"
date: 2009-11-06
forum: Installation &amp; Upgrades
---

### Post by HannuMR on 2009-11-06
USB-modem Huawei e169. It works very fine only in 9.04.
Upgrade 9.04 > 9.10 done many times, but no internet connection. Same with live-CD.
Is it better to wait next spring and hope..?

---

### Post by jheaton5 on 2009-11-06
See your previous [thread]("http://ubuntuforums.org/showthread.php?t=1312263").

---

### Post by HannuMR on 2009-11-06
Thanks.
In my case with Huawei e169 there is no working Network Manager in 9.10, so I can not
make new connection.

---

### Post by jheaton5 on 2009-11-06
Can you install network manager by using ethernet connection?  In a terminal type: ```
$ sudo aptitude udate
$ sudo aptitude install network-manager network-manager-gui
```

Network Manager is installed with gnome.  Are you using some other desktop manager?

---

### Post by HannuMR on 2009-11-06
It was my fourth upgrade to 9.10.
Network Manager is there, but no internet connection. I tried ewerything what I can, even those sudo codes.
All time I getting this about Mobile Partner:

Error mounting: Mount exited with exit code 32: mount: block device/ dev/sr1 is write protected, mounting read-only
mount: /dec/sr1 is already mounted or /media/ Mobile Partner is busy

My english is not good, and I can not hanlde this + I am very tired on 9.10.
It is disaster for me after good 9.04.

Gog bless this working Windows.

---

### Post by jouni on 2009-11-06
> **HannuMR said:**
> 
My english is not good, and I can not hanlde this + I am very tired on 9.10.


From your name I guess you are Finnish. This is being discussed on the [Finnish Ubuntu forums]("http://forum.ubuntu-fi.org/index.php?topic=29831.msg230952") as well.

---

### Post by HannuMR on 2009-11-07
Right.
Jouni, I hope you read all threads in finnish forum.

sudo rmmod usb-storage
sudo modprobe -r option
sudo modprobe -r usbserial
sudo modprobe usbserial vendor=0x12d1 product=0x1001
sudo pppd ttyUSB0

This is not real solution, because you must do that and create new connection every time, when you need internet...

Drivers for Huawei are destroyed in kernel of Ubuntu 9.10:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146?comments=all)

Situation is the same with Nokia mobile phone - no connection to 9.10,
and no updates for kernel to create 3G-connection..

---

### Post by tempus on 2009-11-07
> **HannuMR said:**
> USB-modem Huawei e169. It works very fine only in 9.04.
Upgrade 9.04 > 9.10 done many times, but no internet connection. Same with live-CD.
Is it better to wait next spring and hope..?

Same problem here. my USR USB modem worked perfectly in version 9.04 but not with 9.10. I was using GnomePPP in 9.04 but it does not work now. Is there something being done to get back functionality for dial-up modems?

---

### Post by Menestrello on 2009-11-07
If your hardware/connection was working with 9.04, try this: [http://ubuntuforums.org/showthread.php?t=1310892](http://ubuntuforums.org/showthread.php?t=1310892)

I hope it can help you!

---

