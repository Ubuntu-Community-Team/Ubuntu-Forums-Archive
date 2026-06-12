---
title: "no tty display after nvidia driver installed"
date: 2012-05-06
forum: Hardware
---

### Post by Chace Young on 2012-05-06
after the nvidia driver installed my laptop cannot open tty1~tty6. after hit ctrl alt fn. nothing but a blank black screen.
my platform is ubuntu 12.04 desktop and nvidia gtx 230m, any solution please? thx

---

### Post by sudodus on 2012-05-06
> **Chace Young said:**
> after the nvidia driver installed my laptop cannot open tty1~tty6. after hit ctrl alt fn. nothing but a blank black screen.
my platform is ubuntu 12.04 desktop and nvidia gtx 230m, any solution please? thx
Can you answer the following questions to clarify your problem:

1. Do you mean pressing the following three keys at the same time?
ctrl + alt + F1
...
ctrl + alt + F6

2. Did it work before installing the nvidia driver?

3. Does the graphic desktop interface work as it should (on tty7)?

4. Is it the built-in nvidia driver suggested by the system (jockey-gtk), or is it a driver downloaded directly from nvidia's web site and installed manually?

These things work for me in a system that I have updated from the beta stage. (It should be the current Ubuntu 12.04 because it is completely updated, and I have two nvidia chips an older one in one computer and GeForce GT 430 in another one)

---

### Post by Chace Young on 2012-05-09
> **sudodus said:**
> Can you answer the following questions to clarify your problem:

1. Do you mean pressing the following three keys at the same time?
ctrl + alt + F1
...
ctrl + alt + F6

2. Did it work before installing the nvidia driver?

3. Does the graphic desktop interface work as it should (on tty7)?

4. Is it the built-in nvidia driver suggested by the system (jockey-gtk), or is it a driver downloaded directly from nvidia's web site and installed manually?

These things work for me in a system that I have updated from the beta stage. (It should be the current Ubuntu 12.04 because it is completely updated, and I have two nvidia chips an older one in one computer and GeForce GT 430 in another one)

1. yep
2. it worked well before the drive installed.
3. it works well on tty7.
4. i just use the apt-get nvidia-current
ps: is that a resolution issue?

---

### Post by sudodus on 2012-05-09
> **Chace Young said:**
> 1. yep
2. it worked well before the drive installed.
3. it works well on tty7.
4. i just use the apt-get nvidia-current
ps: is that a resolution issue?
Try if there is another alternative suggested by 
```
jockey-gtk
``` that would keep the text mode options

---

### Post by markbl on 2012-05-09
Ubuntu 12.04 includes the buggy version 295.40 nvidia graphics driver. One of the problems I have seen is that virtual terminals don't work (actually they are there - it is just that the screen is completely blank so you can not see the text). Note, for my card, the nvidia driver also crashes (segmentation fault) after a few hours. In the last few days, nvidia have also published 295.49 and 302.07 (beta) versions but I find the same two problems in those also.

I have removed the proprietary nvidia driver and am using the standard open nouveau driver which works very well, has full 3D effects, etc. Maybe you want to try this also.

---

### Post by Chace Young on 2012-05-12
> **markbl said:**
> Ubuntu 12.04 includes the buggy version 295.40 nvidia graphics driver. One of the problems I have seen is that virtual terminals don't work (actually they are there - it is just that the screen is completely blank so you can not see the text). Note, for my card, the nvidia driver also crashes (segmentation fault) after a few hours. In the last few days, nvidia have also published 295.49 and 302.07 (beta) versions but I find the same two problems in those also.

I have removed the proprietary nvidia driver and am using the standard open nouveau driver which works very well, has full 3D effects, etc. Maybe you want to try this also.

thx, i'm using the standard driver nouveau, but i want to use CUDA for my study, so nvidia driver is necessary!

---

### Post by Chace Young on 2012-05-12
> **sudodus said:**
> Try if there is another alternative suggested by 
```
jockey-gtk
``` that would keep the text mode options

thx a lot. i'll try it.

---

### Post by sudodus on 2012-05-12
Another alternative is to download and install various drivers directly from nvidia's web site. You need to run in text mode, either booting in recovery mode or some other text mode, because it is necessary to stop the graphic desktop environment before running the install script. See for example the following link

[[COLOR="Red"]_http://ubuntuforums.org/showthread.php?t=1948324_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1948324")

and remember that another version of the driver might be better for you. You may have to install and uninstall several of them. (It is important to uninstall the old one before installing another one.)

---

