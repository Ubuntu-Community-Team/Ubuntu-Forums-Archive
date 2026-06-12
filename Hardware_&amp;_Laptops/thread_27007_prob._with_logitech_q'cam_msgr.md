---
title: "prob. with logitech q'cam msgr"
date: 2005-04-14
forum: Hardware &amp; Laptops
---

### Post by andyk on 2005-04-14
i'm installing ubuntu on my parents dell desktop.  installation went with out a hitch.  no problems with logitech cordless mouse, linksys wireless router etc. when i got to the webcam, i hit a snare.  using previous posts i found:
[http://home.mag.cx/messenger/source/](http://home.mag.cx/messenger/source/)

installation was easy and at the end i had a video source from camera.  i followed the prompts to install driver permenantly.  reboot and now i can't use camera.  output of dmesg:

quickcam [45.221912]: ---------------loading quickcam module---------------------------
quickcam [45.221923]: struct quickcam size 3900

further down:

USB Core: registered new driver quickcam

and yet farther down;

quickcam [53.671943]: INT URB error status=-84 tb_length=1 act_length=0 interval=16 frame=-1 data=00

still farther:

kernel 2.6.10-5-386 bus:1 class:FF subclass:FF vendor:046D product: 08F0
poisoning qc in qc_usb.init
E00A 08F0
registered /dev/video0
quick shutdown INIT_HANDLER

then asks to reload quickcam module using "rmmod quickcam ; modprobe quickcam"
at the end of dmesg output i run:

lynn@recroom$ sudo rmmod quickcam ; modprobe quickcam
password:
FATAL: error inserting quickcam (lib/modules/2.6.10-5-386/misc/quickcam.ko): operation not permitted

any help or input ?

andy

---

