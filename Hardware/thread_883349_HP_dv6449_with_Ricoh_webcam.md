---
title: "HP dv6449 with Ricoh webcam?"
date: 2008-08-07
forum: Hardware
---

### Post by zakman411 on 2008-08-07
Hi all,
Im fairly new to Ubuntu 8.04, and I've almost completed the switch over from vista. I have everything working at this point, other than my webcam, which i would certainly like to use (with 'Cheese') however, when i run any application using the webcam, nothing happens (the blue light next to it will turn on in windows). I have downloaded gstreamer and a few other useless drivers (most of which I have no idea what they're for) which I found in forums that I've been searching through, all with no cigar. I emailed one of the developers of cheese, and he recommended opening 'gstreamer-properties', clicking on the video tab, then testing the set up.. I did that, (with plugin: v4l2  and device: none [which is unselectable]) and the test said:

Video for Linux 2 (v4l2): Cannot identify device '/dev/video0'

I've tried the other two plugins, both return the same error. According to my google searches, this isnt a rare problem, it seems that my Ricoh webcam doesnt have a good time with linux. However, i cant seem to find a thread that has worked for me.. any help? Im dying to use cheese

-I am new at this so try to keep it simple if possible, thanks in advance!

---

### Post by phidia on 2008-08-07
I don't have the same model webcam but this [ubuntu wiki]("https://help.ubuntu.com/community/Webcam") may help you.

---

### Post by sergiom99 on 2008-08-08
please post the output of lsusb
I might have the same camera, lets see.

---

### Post by zakman411 on 2008-08-10
> **sergiom99 said:**
> please post the output of lsusb
I might have the same camera, lets see.

Thanks for the replies. I will check out that wiki, although I don't know if that will get cheese to work, thats my main concern here haha. In the meantime, here is my output for lsusb:

Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 05ca:1810 Ricoh Co., Ltd 
Bus 001 Device 001: ID 0000:0000  

Let me know.

---

### Post by sergiom99 on 2008-08-10
sorry, this is mine:
> Bus 002 Device 002: ID 064e:a110 Suyin Corp.

worked out-of-the-box in Kubuntu Hardy (and gutsy), both in cheese and Kopete.

---

### Post by sergiom99 on 2008-08-10
searching for that keywords, a few thread appeared. maybe some of them might help:
05ca:1810 Ricoh

[http://ubuntuforums.org/search.php?searchid=46062706](http://ubuntuforums.org/search.php?searchid=46062706)

---

