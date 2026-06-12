---
title: "Aspire 9300 webcam"
date: 2007-06-24
forum: Hardware &amp; Laptops
---

### Post by Seti on 2007-06-24
Hello, I've just set up Feisty on a friend's Acer Aspire 9300 and have everything working, except for the built in webcam. Now Feisty does detect the USB 2.0 camera, but I have not been able to get it working. I tried Amsn and Camorama. When I launch Camorama, I get "Could not connect to video device (/dev/video0) Please check connection".
This will be my friend's first time having linux, and I would really like to get this working for him.

Any ideas?

thnx in advance

---

### Post by Seti on 2007-06-24
Anyone else even have an Aspire 9300??

Anyone?

---

### Post by retro_killa on 2007-07-05
i have a aspire as well & i was seeing if there is any webcam drivers for my laptop

---

### Post by retro_killa on 2007-07-07
bump

---

### Post by AJB2K3 on 2007-07-07
Will dis work?
[Orbicam possible install]("http://www.southernvaleslug.org/modules/newbb/viewtopic.php?topic_id=25&forum=2&post_id=27")
[Ubuntu 7.04 driver?]("http://southernvaleslug.org/modules/mydownloads/viewcat.php?cid=4")
No this doesn't work because the files are in bz2 format and the tar command wont touch it.

---

### Post by tgellen on 2007-08-01
I too have an Acer Aspire 9300 ( 9303WSMi ) and I've managed to get the webcam working with one caveat. The webcam in my Acer is also a USB2.0 WebCam. To confirm that you have the same webcam as I do type
```
lsusb
```
and look for one of the following
```

ID 5986:0100
ID 5986:0102
ID 5986:0200

```
Currently this webcam is supported by the [Linux UVC driver]("http://linux-uvc.berlios.de/") however, and here is the caveat, it only supports V4L2 interface and most software which supports webcams only support V4L interface. Those which support V4L2 don't seem to support MJPEG decoding which is required by this webcam.

To test if the webcam is working. Open a Terminal and type in the following ...

```

sudo apt-get install build-essential libsdl1.2-dev libpt-plugins-v4l2 subversion
svn checkout svn://svn.berlios.de/linux-uvc/linux-uvc/trunk
cd trunk
make
sudo modprobe -r uvcvideo
sudo make install
sudo modprobe uvcvideo
cd ..
wget http://mxhaard.free.fr/spca50x/Investigation/uvc/luvcview-20070512.tar.gz
tar -zxvf luvcview-20070512.tar.gz
cd luvcview-20070512/
make
./luvcview

```

All things going to plan the green light on the webcam will come on and a small window should open with a live preview :)

Enjoy

---

### Post by lubaby on 2007-09-01
This works also for me (same webcam on Acer 5104, tested in updated Gutsy Tribe 5). Unfortunetaly luvcview is the only one application which works for me with this webcam :-(

---

### Post by ramadhian on 2007-10-20
rama@mylappy:~/luvcview-20070512$ ./luvcview 
luvcview version 0.2.1 
Video driver: x11
A window manager is available
video /dev/video0 
ERROR opening V4L interface 
: No such file or directory

Did I missed somethin here ?

---

### Post by geirergoy on 2007-10-31
I got that guide working fine on my Aspire 5610Z.
But why is luvcview the only program that works  with this cam?
I'd like to use aMSN and similar. Luvcview sucks...

---

### Post by bryston on 2007-11-15
i have aspire 9304, lucview works but i agree, its rubbish.
i installed skype and the camera works fine.  no probs at all.

---

### Post by SoulSmasher on 2007-12-01
works like a charm, but still useless on other programs :(

---

### Post by verdomde on 2007-12-29
hey, ive no help, but  a question of my own, did you ever get the nvidia new glx drivers to run on your aspire 9300, mine freezes and im looking for help?

---

### Post by egglestn on 2008-02-28
You sir are a genius.. I have been sweating bullets trying to make the webcam work, and here was the info here from the start.

Shame that only skype uses it but thanks for the help
:KS

---

### Post by tgellen on 2008-04-30
Fantastically all the hardware on my Acer 9303 works fantastically under Hardy :) The webcam works a treat with Ekiga, my SD cards are read/write perfectly, video resolution with nv driver is perfect and Flash on FF3 (AMD64 Install) works like a dream. No need to follow my compilation notes for this webcam anymore :) "Out of the box" goodness. Yum.

---

### Post by JesCed on 2008-05-03
Hello. I am running hady on an Acer Aspire 3690, and haven't been able to get the orbicam working. Ekiga and Skype both detect a USB 2.0 camera, but I get only the black screen. I downloaded, compiled and ran luvcview, and I get the same issue... the green light on the cam doesn't light up, and I only see the black screen on the preview window. I know the cam itself is OK, because it works fine in the bundled Vista.

Any ideas?

---

### Post by tgellen on 2008-05-03
What is the output of the lsusb command ?

---

### Post by JesCed on 2008-05-03
All right, here is my output:

jesus@jesus-laptop:~$ lsusb
Bus 005 Device 003: ID 5986:0100 Bison Acer OrbiCam
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 0d8c:0001 C-Media Electronics, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

---

### Post by JesCed on 2008-05-03
All right, here is my output:

[INDENT]```
jesus@jesus-laptop:~$ lsusb
Bus 005 Device 003: ID 5986:0100 Bison Acer OrbiCam
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 0d8c:0001 C-Media Electronics, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000
```[/INDENT]

---

### Post by JesCed on 2008-05-05
Hello, all.

I just thought I'd post a follow-up. I have no idea what happend with my computer now, but today, just for the heck of it, I tried luvcview again, and this time it actually worked! The viewer window came up, and this time there was video in it! I also found the video working in Ekiga and Skype. So, it seems as though the problem fixed itself. I don't know what happened, but I am very glad it did.

---

### Post by j0rg3n on 2008-05-25
> **JesCed said:**
> Hello. I am running hady on an Acer Aspire 3690, and haven't been able to get the orbicam working. Ekiga and Skype both detect a USB 2.0 camera, but I get only the black screen. I downloaded, compiled and ran luvcview, and I get the same issue... the green light on the cam doesn't light up, and I only see the black screen on the preview window. I know the cam itself is OK, because it works fine in the bundled Vista.

Any ideas?

Just writing to confirm the problem. lsusb output is the same as yours, but I have an ACER Aspire 5100, AMD64 Dual Core, ATI 8.4 drivers, running Hardy 64:
```
Bus 003 Device 003: ID 5986:0100 Bison Acer OrbiCam
```

Clicking "X" on the black luvcview video window prints "Stop asked" in the terminal, but does nothing else.

---

