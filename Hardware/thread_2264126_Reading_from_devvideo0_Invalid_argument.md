---
title: "Reading from /dev/video0 Invalid argument"
date: 2015-02-05
forum: Hardware
---

### Post by javier36 on 2015-02-05
Hello, I am using Lubuntu 14.10. I have a web camera connected to the computer.
The model: Logitech Webcam C270 [http://support.logitech.com/en_us/product/7079](http://support.logitech.com/en_us/product/7079)
 The camera is working: for example using  "mplayer tv:// " I can see the image correctly. 

I want to read the RAW DATA, the idea is to pipe the result through netcat and visualize it in other computer. Something like the suggested here: [http://www.raspberrypi.org/forums/viewtopic.php?f=28&t=98778&p=685576#p685576](http://www.raspberrypi.org/forums/viewtopic.php?f=28&t=98778&p=685576#p685576) 

This is the error:

# cat /dev/video0
cat: /dev/video0: Invalid argument
# dd if=/dev/video0 
dd: error reading ‘/dev/video0’: Invalid argument
0+0 records in
0+0 records out
0 bytes (0 B) copied, 0,00210474 s, 0,0 kB/s
# 
# ls -l /dev/video0 
crw-rw----+ 1 root video 81, 0 feb  5 17:15 /dev/video0

(yes, im running it as root to discard permissions issues)

I have tried the same in archlinux, also in a raspberrypi with raspbian. The result is always the same, "Invalid argument"
Is it something specific about this model of webcam? Do you know any other way to do it?

Thank you in advance
 J.

---

