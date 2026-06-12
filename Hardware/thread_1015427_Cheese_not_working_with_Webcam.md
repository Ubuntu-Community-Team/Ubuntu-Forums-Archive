---
title: "Cheese not working with Webcam"
date: 2008-12-18
forum: Hardware
---

### Post by Prominence on 2008-12-18
Recently my Cheese Photobooth has stopped working, how do I fix it? Or when will it be fixed? This is a big thing to be seeing that the family loves it, and would suck to go without it.

---

### Post by chris.h on 2008-12-18
what kind of computer do you have, what kind of webcam do you have? have you tried another program like luvcview or skype?

---

### Post by bushd on 2008-12-18
I've heard of Cheese having an issue with webcams -- it is because you need to set the Cheese resolution from its config file, which I can't remember where it's located or how to do it.  Try Ekiga, Camorama or Xawtv.  If that isn't it then an update may have killed it somehow, the webcam died or something odd.  I know I had to chmod my /dev/video0 to get it to work.

---

### Post by cheapest on 2008-12-18
yes, you need to set the Cheese resolution from its config file.

---

### Post by Prominence on 2008-12-19
How do I do that?

---

### Post by Prominence on 2008-12-19
bump

---

### Post by Prominence on 2008-12-20
help?

---

### Post by Prominence on 2008-12-21
please someone tell me how to...anyone

---

### Post by Prominence on 2008-12-26
will anyone help?

---

### Post by littletinman on 2008-12-29
I need help with this too. HElooooooo?

---

### Post by xer09aradox on 2008-12-29
I think the settings are in gconf-editor under apps. Don't know if that'll solve your webcam problems, though.

---

### Post by digitizemd on 2009-01-04
xer09aradox is correct.  press alt+f2 and type in gconf-editor.  cheese is listed under the apps tab.  i am, however, experiencing buggy behavior with cheese, but only on ubuntu 8.10.

---

### Post by greenpeace on 2009-01-04
> **bushd said:**
> I've heard of Cheese having an issue with webcams -- it is because you need to set the Cheese resolution from its config file, which I can't remember where it's located or how to do it.  Try Ekiga, Camorama or Xawtv.  If that isn't it then an update may have killed it somehow, the webcam died or something odd.  I know I had to chmod my /dev/video0 to get it to work.

hey, I'm having the same problem here with camorama... did you just give read access to all users like: 

chmod +r /dev/video0 

? 

my cheese problems were resolved by changing the capture resolution down to a size that my webcam actually supports... then it stopped crashing all the time.  :)

---

### Post by eldersoares on 2009-01-06
hi!
i had the same problem and i did the same: set the lowest resolution and it started working fine. although, the video quality is too bad!! i'd like to be able to record/take photos in a better resolution. i know my webcam supports it 'cause in win vista, i can.

executin cheese in terminal, when i increase the resolution, appears the following:

libv4l2: error allocating conversion buffer

does anybody know what it could mean???

thanks a lot!

---

### Post by octopuskevin on 2009-01-15
I've been having the same problems but it looks like a fix for libv4l was posted on the launchpad thread... [https://bugs.launchpad.net/ubuntu/+source/camstream/+bug/260918](https://bugs.launchpad.net/ubuntu/+source/camstream/+bug/260918)

check the bottom post or
> 
 Stéphane Marguet wrote on 2009-01-11: (permalink)

libv4l 0.5.8 is out.
Fixed problem with camorama for me.
Grab it in my PPA (or elsewhere):
i386 : [https://edge.launchpad.net/%7Estemp/+archive/+files/libv4l-0_0.5.8-1~intrepidppa1_i386.deb](https://edge.launchpad.net/%7Estemp/+archive/+files/libv4l-0_0.5.8-1~intrepidppa1_i386.deb)
amd64 : [https://edge.launchpad.net/%7Estemp/+archive/+files/libv4l-0_0.5.8-1~intrepidppa1_amd64.deb](https://edge.launchpad.net/%7Estemp/+archive/+files/libv4l-0_0.5.8-1~intrepidppa1_amd64.deb)
amd64 compatibility : [https://edge.launchpad.net/%7Estemp/+archive/+files/lib32v4l-0_0.5.8-1~intrepidppa1_amd64.deb](https://edge.launchpad.net/%7Estemp/+archive/+files/lib32v4l-0_0.5.8-1~intrepidppa1_amd64.deb)


---

