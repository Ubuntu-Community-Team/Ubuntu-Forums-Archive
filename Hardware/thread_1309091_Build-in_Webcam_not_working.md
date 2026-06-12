---
title: "Build-in Webcam not working"
date: 2009-11-01
forum: Hardware
---

### Post by Ampi on 2009-11-01
I have an Acer Aspire One with Ubuntu Netbook Remix and it's impossible for me to get my webcam working even after upgrading to 9.10.
For example Skype and Cheese don't see I have a webcam. So I installed luvcview

apt-get install luvcview

and that seemed to install well.
But after

dmesg |grep -i "uvc"


I just get a new prompt. And when I want to test it:

luvcview -f yuv

I get the following error:

luvcview 0.2.4

SDL information:
Video driver: x11
A window manager is available
Device information:
Device path: /dev/video0
ERROR opening V4L interface: No such file or directory

---

