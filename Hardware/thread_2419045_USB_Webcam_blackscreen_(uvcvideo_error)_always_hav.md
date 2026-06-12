---
title: "USB Webcam blackscreen (uvcvideo error) always have to unplug"
date: 2019-05-15
forum: Hardware
---

### Post by jkstar1337 on 2019-05-15
Hello,

I am using Ubuntu 16.04 LTS with V4L2, OpenCV 3.4 Python with Intel NUC i3 7100U and ELP USB 2.0 Camera ELP-USB500W04AF-L60 OV5640 (Datasheet required: / Linux with UVC(above linux-2.6.26))

After a while some days some of my USB cameras only return a black screen, it also happend that it returned a white screen when using cheese or any other program to capture my webcam's image.
I have to re-plug the device physically to get a normal picture. Un-/binding usb ports using shellscript or C script does not have any effect. Even rebooting/shutdown doesn't change anything.


[LIST]
[*]Cam returns blackscreen 
[*]V4L2 v4l2-ctl settings are all default values 
[*]dmesg shows following error: 
[/LIST]
     
      [ATTACH=CONFIG]283272[/ATTACH]


Can it be a uvcvideo module/kernel bug? I have seen this bug happen to me multiple times on the same devices with the same camera. It also happend once that the picture is only white.
Thanks for help!

---

