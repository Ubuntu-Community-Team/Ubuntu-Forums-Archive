---
title: "Insmod -1 Invalid module format"
date: 2009-10-19
forum: Hardware
---

### Post by Unkuiri on 2009-10-19
Hi, I'm having a problem loading some modules in ubuntu jaunty...I've update the kernel and now I can't load the modules that let my dvb-t usb device...I've done:
> manuel@manuel-laptop:~$ cd ~/ec168/v4l/
manuel@manuel-laptop:~/ec168/v4l$ sudo insmod dvb-core.ko
insmod: error inserting 'dvb-core.ko': -1 Invalid module format
manuel@manuel-laptop:~/ec168/v4l$
I've tryed also:
> manuel@manuel-laptop:~/ec168/v4l$ sudo modprobe dvb-core.ko
WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.
FATAL: Module dvb_core.ko not found.
manuel@manuel-laptop:~/ec168/v4l$ 
without any result...:(...can someone help me?

thanks in advance

---

