---
title: "Webcam A4Tech PK 130MJ - incorrect work in kubuntu 14.04 LTS"
date: 2016-02-09
forum: Hardware
---

### Post by Melano Chole on 2016-02-09
Hi!

I've got an old web camera A4 Tech PK 130MJ which works pretty fine in Windows, however gives a broken image in kubuntu 14.04 (3.13.0-77-generic):

[IMG]http://storage8.static.itmages.ru/i/16/0209/h_1455018610_7954639_a4404c5648.jpg[/IMG]
As soon as the image is present, I infer that the camera is detected. The outputs of dmesg and lsusb seem to confirm that:

dmesg 
```
[ 2653.224012] usb 2-1.3: new high-speed USB device number 4 using ehci-pci
[ 2653.418082] usb 2-1.3: New USB device found, idVendor=0ac8, idProduct=0328
[ 2653.418088] usb 2-1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 2653.418093] usb 2-1.3: Product: USB2.0 Web Camera
[ 2653.418096] usb 2-1.3: Manufacturer: Vimicro Corp.
[ 2653.419084] gspca_main: vc032x-2.14.0 probing 0ac8:0328
```
lsusb:
```
Bus 002 Device 004: ID 0ac8:0328 Z-Star Microelectronics Corp. A4Tech PK-130MG
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 001 Device 003: ID 04d9:1400 Holtek Semiconductor, Inc. PS/2 keyboard + mouse controller
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```
I have been searching for the way to solve the problem for two  weeks, but the newest solutions I've found are from 2011, and all are  related to gspca or gspcav1 modules compilation. I have tried some, but  the compilation failed due to various errors. 

Does anybody knows a  method to make the camera work properly using the native kernel support that is definitely present in the kernel and without compilation that  requires tones of additional packages and build dependencies? Shall I give any additional information?

---

### Post by coldraven on 2016-02-09
The only thing I can suggest is to install guvcview and try adjusting some settings. I see in this link (click for bigger image)  that there is a powerline frequency adjustment, I don't know what it does but give it a try :)
Also try disabling any "Auto" settings in the check boxes.
[http://www.ghacks.net/2011/02/05/record-from-your-web-cam-in-linux-with-guvcview/](http://www.ghacks.net/2011/02/05/record-from-your-web-cam-in-linux-with-guvcview/)

---

### Post by Melano Chole on 2016-02-09
coldraven, that's just amazing! It finally turned out that the camera is able to work properly in kubuntu!
[IMG]http://storage8.static.itmages.ru/i/16/0209/h_1455051777_8588905_4367002cc9.png[/IMG]
No additional settings in guvcvuew were necessary to change. Wonder why VLC could'nt transmit the correct picture while being OK with a UVC Logitwch C270 camera. Thanks for the advice!

But VLC is not the issue. Skype still shows a black rectangle. I tried launching it in console like this:
```
bash -c 'LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so skype'
bash -c "LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l2convert.so skype"

```
but its video won't work :-(
Should I create another thread in "Multimedia software" section, or can proceed right here? Please advice.

---

### Post by coldraven on 2016-02-10
> Skype still shows a black rectangle
When in Skype shine a flashlight at your web-cam, do you see anything?
If so quit Skype, run guvcview and (if there is one) uncheck the  "Auto level" box then adjust the brightness. No need to save, just quit uvcview and start Skype.

---

### Post by Melano Chole on 2016-02-11
> **coldraven said:**
> When in Skype shine a flashlight at your web-cam, do you see anything?
Nope. Just a blank screen. I treid this with the both of the aforenentioned preload options, but nothing appears on the screen even when I bring a flashlight directly to the camera.
I even tried to downgrade my skype as people advise here [https://code.google.com/archive/p/r5u870/issues/8](https://code.google.com/archive/p/r5u870/issues/8) and here [https://github.com/3pei/r5u870](https://github.com/3pei/r5u870) but the older version just does not start.

---

### Post by Melano Chole on 2016-02-11
BTW, the camera is not recognized here as well: [http://www.testmycam.net/](http://www.testmycam.net/)

---

### Post by Melano Chole on 2016-02-14
Today I tried the camera in kubuntu 15.10 with guvcview installed, and it worked even worse there. I didn't take a picture, but it was mostly black and white with some color spots. It seems I should give up making the camera work in linux as in windows :(

---

### Post by mörgæs on 2016-02-15
Do you get a better picture using Cheese?

---

### Post by Melano Chole on 2016-02-16
> **mörgæs said:**
> Do you get a better picture using Cheese?

No. The picture in cheese is slightly different, but completely unusable.

---

