---
title: "Rocketfish RF-NBWEB Webcam driver appears to be installed but not working perfectly."
date: 2009-12-29
forum: Hardware
---

### Post by nch0930 on 2009-12-29
Hello, I'm using Ubuntu 9.10.

On the Video settings on Skype, I get no image on the test window, however on AMSN, I do get a very very dark image, so I guess the driver is installed.

A blue led on this webcam turn on when you use it on Windows, which doesn't happen when I test it under AMSN, I think that's why maybe I get such a dark image.

Can anybody help me fix this?

this is what lsusb returns:
Bus 002 Device 007: ID 0c45:6288 Microdia PC Camera with Microphone (SN9C202 + OV9655)

This is where you can get the drivers for Windows/Mac:
[http://www.rocketfishproducts.com/pc-35-3-rocketfish-notebook-web-camera.aspx](http://www.rocketfishproducts.com/pc-35-3-rocketfish-notebook-web-camera.aspx)

Thanks in advance.

---

### Post by nch0930 on 2009-12-29
I posted at the microdia google groups, but it wasn't letting me write everything I wanted to write, and also I'm not sure that group is still active, I don't understand well how does google groups work.

So I'm gonna write my complete message on this thread, I hope somebody knows how to make this webcam work.

---

### Post by nch0930 on 2010-03-06
Hello, I'm trying to get a Microdia webcam to run on my Linux system.

Brand RocketFish Model: RF-NBWEB S/N:7J08A000381
ID 0c45:6288 Microdia PC Camera with Microphone (SN9C202 + OV9655)

Linux: Ubuntu 9.10 2.6.31-19-generic

I installed the driver following the instructions on this site:
[http://groups.google.com/group/microdia/web/testing-microdia-driver-draft?hl=en](http://groups.google.com/group/microdia/web/testing-microdia-driver-draft?hl=en)

However, I wasn't able to get the "sn9c20x sub-driver" mentioned at the top, so I just followed the regular instructions.

Everything went OK with the installation, but the webcam isn't working properly. Skype recognizes it but I get no image, and AMSN displays a very dark image.

When I use it under Windows, a blue led turns on, I'm attaching a photo that shows this.
[http://img121.imageshack.us/img121/7107/onoffh.jpg](http://img121.imageshack.us/img121/7107/onoffh.jpg)

I think this Led is what gives the camera a clear image.

The windows drivers can be found here:
[http://www.rocketfishproducts.com/pc-35-3-rocketfish-notebook-web-camera.aspx](http://www.rocketfishproducts.com/pc-35-3-rocketfish-notebook-web-camera.aspx)

I'm also attaching 2 snp2std.inf files I found on my Windows system, and I wonder if the next line could be in particular helpful:
%USBPCamMicDesc% = SN.PCamMic,USB\VID_0c45&PID_6288&MI_00    ; SN9C202 + OV9655
[http://rapidshare.de/files/49186426/snp2std.inf.html](http://rapidshare.de/files/49186426/snp2std.inf.html)
[http://rapidshare.de/files/49186427/snp2std_2_.inf.html](http://rapidshare.de/files/49186427/snp2std_2_.inf.html)

This is the output of: lsusb -d 0c45:6288x -v
[http://rapidshare.de/files/49186431/lsusb.html](http://rapidshare.de/files/49186431/lsusb.html)

Can anybody help me solve this?

Thanks in advance.

---

### Post by ambdeep on 2010-04-23
*bump*
im facing similar problems....can soe one please help?

---

