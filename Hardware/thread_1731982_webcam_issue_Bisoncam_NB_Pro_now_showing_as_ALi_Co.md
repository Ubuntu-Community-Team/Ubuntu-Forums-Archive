---
title: "webcam issue: Bisoncam NB Pro now showing as ALi Corp M5606"
date: 2011-04-17
forum: Hardware
---

### Post by casaschi on 2011-04-17
hello,

I have an MSI WIND U100 and I got recently a very strange issue with the webcam; I suspect some kind of hardware failure, but I though asking here before giving up looking for a software fix.

Until few days ago, the webcam was working fine, I was using it with skype without any problem.
In the linux syslog this was shown: 
```
uvcvideo: Found UVC 1.00 device BisonCam, NB Pro (5986:0203)
```
Few days ago, the webcam stopped working; still linux recognixes there is a webcam device but the video is always blank and the small light next to the webcam never lights up. Moreover, the linux syslog shows this entry:
```
uvcvideo: Found UVC 1.00 device USB2.0 Camera (0402:5606)
```
Strange enough, the webcam is reported as a different kind (0402:5606 correspond to "ALi Corp. M5606 Video Camera Controller [UVC]"), apparently based on same/similar hardware.

Tested this again with a live CD, so to exclude software corruption on my system and the behaviour is confirmed.

Bottom line... something happened to my webcam that now presents itself to the OS as a different HW:
- anyone with an idea what might have happened and how to fix it?
- anyone with the latest firmware for the BisonCam, NB Pro (5986:0203) and with a suggestion how to flash the firmware to the webcam from linux?
- any other advise (other than replacing the hw... looked at some notes how to disassemble the MSI WIND and looks scary, I dont think to be able to put it back together)?

Thanks in advance!

Paolo

---

