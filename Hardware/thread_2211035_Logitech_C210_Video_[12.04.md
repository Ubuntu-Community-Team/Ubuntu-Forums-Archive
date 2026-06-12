---
title: "Logitech C210 Video [12.04"
date: 2014-03-13
forum: Hardware
---

### Post by Wobzter on 2014-03-13
Hello,

I have installed Ubuntu 12.04 on my HP Elitebook 8540w.
Skype has not always been a fun thing, but after lots of effort I was able to make it work a couple of months ago.
The problem I kept on having was that my screen would freeze after 1-30 minutes. Not a problem so much, but sometimes a bit annoying.
Now I'm using another webcam (the C210 one) which has a way better resolution. It worked similar to the previous one. But I was just in a Skype chat when it started to freeze ago.
So naturally I pressed "webcam off" and then "webcam on" again. This time the webcam did not return. In fact, my laptop is unable to find it at all, even though it is plugged it. 

Upon my search for information, I found that this information might be useful:

> robbie@robbie-HP-EliteBook-8540w:~$ lsmod | grep video
uvcvideo               72250  0 
videobuf2_core         39385  1 uvcvideo
videodev               96131  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12920  1 uvcvideo
videobuf2_memops       13042  1 videobuf2_vmalloc
video                  19116  0 


> robbie@robbie-HP-EliteBook-8540w:~$ dmesg | grep -i video
[    1.268197] pci 0000:01:00.0: Boot video device
[   12.526744] video: probe of LNXVIDEO:00 failed with error -2
[   13.831980] Linux video capture interface: v2.00
[   14.268499] uvcvideo: Found UVC 1.00 device <unnamed> (046d:0819)
[   14.370208] usbcore: registered new interface driver uvcvideo
[   14.370210] USB Video Class driver (1.1.1)
robbie@robbie-HP-EliteBook-8540w:~$ 


Unlike most people, it is not a problem of microphone, but of video.

---

