---
title: "Ubuntu 10.10 and kernel-2.6.35 driver for webcams like Ricoh Webcam 1000,etc (r5u870)"
date: 2010-10-10
forum: Hardware
---

### Post by 3pei on 2010-10-10
it is updated: [http://r5u870.googlecode.com/](http://r5u870.googlecode.com/), plz download the latest one (0.2).

hope it useful for you.

---

### Post by belio on 2010-10-10
Working perfectly ! Thanks.

---

### Post by lisdavid89 on 2010-10-10
Great job! It works!

---

### Post by rakeshcherian on 2010-10-13
It worked. thanks
:)

---

### Post by radarlog on 2010-10-15
good job!

---

### Post by AjitDingankar on 2010-10-16
Thanks! It worked for my Logitech webcam.

---

### Post by kshome on 2010-11-09
Thanks a lot, I have been trying to get my webcam working. This worked with 05ca:1870 Ricoh Co., Ltd Webcam 1000.

---

### Post by d0ugparker on 2010-12-03
Don't put any spaces in the directory or subdirectory names.

--drd0ug

---

### Post by camunit on 2010-12-12
Hello. I'm running ubuntu 10.10 in an external hard drive of a HP Pavillion dv6000. It seems the driver was successfully installed (no error message during installation) but still my camera is not working with neither Cheese nor Skype. I think this information may be useful for anyone that could help me:

:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04fc:05d8 Sunplus Technology Co., Ltd Wireless keyboard/mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 001 Device 004: ID 05ca:1870 Ricoh Co., Ltd Webcam 1000**
Bus 001 Device 003: ID 0c0b:2832 Dura Micro, Inc. (Acomdata) 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

:~$ webcam
reading config file: /home/camunit/.webcamrc
v4l2: open /dev/video0: No such file or directory
v4l2: open /dev/video0: No such file or directory
v4l: open /dev/video0: No such file or directory
no grabber device available

Thanks for you help.

---

### Post by KemKev on 2011-02-05
> **3pei said:**
> since I couldn't find one, and the project from palmix.com has been closed, I made a mod for Maverick (and kernel-2.6.35) myself.

here it is: [http://r5u870.googlecode.com/](http://r5u870.googlecode.com/)

hope it useful for you.
Thanks much!  This works fine in Cheese but just a black screen in Skype so I guess I am half-way there!

---

### Post by MODYSAMA on 2011-02-06
Hello,
I need the owner reply,
I face the same problem of **camunit** with genius face cam 312.

---

### Post by nikunjbadjatya on 2011-03-12
It worked wonders.. !! :) Thanks mate.!

---

### Post by pabloikba on 2011-03-16
Great! Thank you!

---

### Post by tomapio on 2011-04-01
dude, you have saved my life twice... i thought you should know that...
BTW, you forgot to mention that after installing the driver you haveto load it by typing

modprobe r5u870

in the console

Thanks!

---

### Post by Shbeeb on 2011-04-13
WORKED WORKED WORKED :D :D
Laptop: Sony Vaio VGN-TZ37GN
Ubuntu 10.10
Kernel: 2.6.35

THaaaaaaaaaaaaaaaaaaaaaaaAAAAAAAAAAAAAAAnnnnnnnnnnnnnnnnnxxxxxxxXXXX :popcorn::popcorn::popcorn::popcorn:

---

### Post by dogturd on 2011-04-14
Hello. I am running Ubuntu 10.10 Kernel 2.6.35
I followed the driver instructions. Web Cam works with Cheese but black screen when test button on Skype. Any ideas please?

---

### Post by farzadbashtani on 2011-04-17
It works .... thanks man :)

---

### Post by carega on 2011-04-17
Not working! Using a Compaq Presario CQ40, the webcam is not even being detected through lsusb

---

### Post by 3pei on 2011-04-18
> **tomapio said:**
> 

** modprobe r5u870**



thank you , I will update the instructions.

and to others:

if you got "open /dev/video0: No such file or directory" or errors in a similar way, just type the command which tomapio write here. and maybe you want to google "how to load driver automatically".

I can confirm that skype is not working. but if there are other apps working, it may have some compatibility bugs in skype. if softwares used same interfaces and they used them in a same way (which are provided by kernel and protocols), they shouldn't get different results.

I didn't use the webcam much,  and I had never tried to find what happened with apps like skype. so I am not really familiar with these problems. if anybody have thoughts about situation which might result these problems and if you think that we could correct them in the webcam driver, plz tell me, I will go into it.

---

### Post by novatillasku on 2011-04-24
There's Ricoh r5u870 for 2.6.38 kernel? (Natty narwhal)

---

### Post by makiyu on 2011-07-23
i'm just new to ubuntu n m getting this error, using ubuntu 11.04....  facecam 312

makiyu@makiyu:~/Downloads/r5u870$ webcam
reading config file: /home/makiyu/.webcamrc
video4linux webcam v1.5 - (c) 1998-2002 Gerd Knorr
grabber config:
  size 320x240 [none]
  input (null), norm (null), jpeg quality 75
  rotate=0, top=0, left=0, bottom=240, right=320
libv4l2: error turning on stream: No space left on device
libv4l2: error reading: Invalid argument
v4l2: read: Invalid argument
capturing image failed

---

### Post by 3pei on 2011-10-13
updated.

---

