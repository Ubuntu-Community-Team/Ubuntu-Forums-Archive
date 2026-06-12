---
title: "Webcam trouble"
date: 2008-08-18
forum: General Help
---

### Post by wildman4god on 2008-08-18
I got a webcam from staples, it is branded with the staples logo and pakaged as staples own brand, i got it because it was 20 bucks, but i found linux didn't recognize it, i tried to get linux drivers but i didn't know who really made it but after some searching and eyeballing i found it was made by a company called sakar its modle number is 49652N. is there a driver for this camera for linux or can i use khexedit to hack the windows drivers so it works. please help and thanks in advanced.

---

### Post by linuxwizard on 2008-08-18
Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Devices > Video Devices > try changing some of the settings. (try both V4L and V4L2)

To test your webcam you can do this:
There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

If Ekiga doesn't work post results of the command > lsusb

---

### Post by wildman4god on 2008-08-19
I can't post the output now as i am in class and don't have the laptop with me now but i will later today. but anywho i used the command and it recognizes it and i can find where it mounts in the file system but ekiga or any webcam program can't use it, the file it produces when it mounts is an unknown file type.

---

### Post by wildman4god on 2008-08-19
here is the output of lsusb
Bus 004 Device 002: ID 0ad2:9314 Service & Quality Technology Co., Ltd 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

---

### Post by wildman4god on 2008-08-24
hello,

anybody there...

echo....

---

### Post by linuxwizard on 2008-08-24
Sorry I didn't reply to you. I don't come to the forum like I have in the past. Searching >  ID 0ad2:9314 Service & Quality Technology Co., Ltd > does not look like it is a webcam so your webcam is not being detected by your system. Do you have your cam connected to a hub ? You need to have cam connected to a port on your computer. If you are not using a hub try using another port on your computer than run > lsusb > again and see if your results change. If not than your cam is not going to work.

---

### Post by wildman4god on 2008-08-25
it is connected directly to the laptop, when i remove the webcam and run lsusb it goes away and when i connect to another port it the same thing shows up on the corresponding port.

---

### Post by linuxwizard on 2008-08-25
If you are saying this is your webcam > Bus 004 Device 002: ID 0ad2:9314 Service & Quality Technology Co., Ltd > not sure which driver you need to get it working i can't find anything on that cam. It is always better to check to see if it will work in Linux before you buy anything.

---

### Post by Crafty Kisses on 2008-08-25
For your next purchase, look at this link > [https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams)

---

### Post by wildman4god on 2008-08-26
it seems that logitech is the linux users choice for webcams, i bought that webcam a year ago when i didn't know that much about linux or webcams and i got it because it was only $20.00. i am still wondering if i could reverse engineer the windows drivers it cam with or somehow convert them to linux format, it this possible?

---

### Post by MacLeod_1980 on 2010-08-23
Did you ever get this worked out?  The cam is branded several different ways.

Installing it via WINE did not seem to help either.

---

### Post by no2498 on 2010-08-24
best chance you have is try this

gstreamer-properties


open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1

cheese has a nice help file look in the faq's

if you get any thing at all get back to us

---

