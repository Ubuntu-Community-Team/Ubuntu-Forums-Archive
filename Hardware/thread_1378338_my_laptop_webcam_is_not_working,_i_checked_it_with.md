---
title: "my laptop webcam is not working, i checked it with cheese."
date: 2010-01-11
forum: Hardware
---

### Post by bulbmaker on 2010-01-11
Mine is hp pavilion dv6226tx. i first tried to video chat using empathy(gmail account), it didn't work then i checked installing cheese. it say no camera found! what should i do?

help plz...

---

### Post by mocoloco on 2010-01-12
Open a terminal (Applications > Accessories > Terminal) and type in ```
gstreamer-properties
```

Select the Video tab and under Default Input hit Test.  Try with plugin set to both "v4l" and "v4l2" and see which works better or if either of them work and post back.

After that close the window and still in the terminal type ```
lsusb
``` to get a list of your USB devices (internal webcams also work through USB).  Use the mouse to copy and paste the output here.

---

### Post by ratdog on 2010-01-16
I'm having the same problem here.
When I first installed ubuntu on my new laptop (Lenovo Y550), the built-in camera would work with cheese.  I didn't really use it after just checking that it worked.  I have since upgraded to 9.10 and have started wanting to use skype.  Now, when I try to use skype the camera is not detected.  Not detected in Cheese either.  No video device is found in gstreamer-properties.  
Here is the output of lsusb:

Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Thanks for any help!

---

### Post by bulbmaker on 2010-01-25
> **mocoloco said:**
> Open a terminal (Applications > Accessories > Terminal) and type in ```
gstreamer-properties
```

Select the Video tab and under Default Input hit Test.  Try with plugin set to both "v4l" and "v4l2" and see which works better or if either of them work and post back.

After that close the window and still in the terminal type ```
lsusb
``` to get a list of your USB devices (internal webcams also work through USB).  Use the mouse to copy and paste the output here.

nither "v41" nor v412" working its saying 
"Video for Linux (v4l): Device "/dev/video0" does not exist."

root@gowtham-laptop:/home/gowtham# lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[COLOR="Lime"]Bus 001 Device 003: ID 05ca:1810 Ricoh Co., Ltd Pavilion Webcam [R5U870][/COLOR]
Bus 003 Device 002: ID 04f3:0214 Elan Microelectronics Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

i can c my web cam name..
plz help me to setup it with cheese:grin:
thanq:o

---

### Post by ratdog on 2010-01-27
Anyone else have any ideas?
I would love to get my camera working.

---

### Post by mrgoldy on 2010-01-27
I'm having the same issue. I signed up for this forum today because of this problem, so hopefully someone can help me out.

I'm not real computer savy, I was using windows but experienced 3 virus attacks in the last year. A coworker suggested I get off the bandwagon and try Ubuntu. I like it so far, but we have relatives all over that we chat with using MSN messenger(now aMSN) and would really like to get the video chat working before giving up and going to Windows 7.

I have a Compaq CQ70-120US Notebook PC with a webcam built in.

I succesfully ran the gstreamer-properties test above and it recognizes my internal webcam.

typed lsusb and get this
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 001 Device 003: ID 064e:a102 Suyin Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 002: ID 046d:c00e Logitech, Inc. M-BJ58/M-BJ69 Optical Wheel Mouse
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by bulbmaker on 2010-01-28
any one help plz... our webcams want life...

---

### Post by niffcreature on 2010-02-02
yeah i think i have the same issue. my webcam is supported out of box supposedly. 
v4l also tells me it has no DGA direct video mode for my display. i have discovered this has to do with the newest xawtv with intrepid which is what im running but i uninstalled it and v4l gives says the same thing. what does that have to do with webcams?
my problem might be more screwed up than yours.

try something i tried, just make a /dev/video0 with this command

mknod /dev/video0 c 81 0

---

### Post by don1ogan on 2010-02-16
Same problem here.
The camera appears on the lsusb list.
It worked fine previously with Jaunty.
No problem with Windows 7 running in Virtual box I can use the web-cam with Yahoo Messenger.

---

### Post by todlangweilig on 2010-03-21
I was able to get the camera on my Lenovo Y550 to work by running these commands. I ran the first command, but when I tried to use the camera, it said that it could not be read or written to. So I tried the second command and it worked.

mknod /dev/video0 c 81 0 
chmod a+rw /dev/video0

---

### Post by mythsnlegends on 2010-04-14
Hi I am having the same issue with my camera laptop. I did not have problems while video conferencing with my in built camera when i first installed Ubuntu but now when my bf and I sent video in empathy, he can't see me but I can see him....the funny thing is, my camera light is turned on!

I tried entering the command 
"gstreamer-properties"
tested my camera out and I found that the Output is not working (the input worked)!

Can someone help!

I am using a toshiba satellite

Thanks!

---

### Post by Sreejith s on 2010-10-10
I am having the same problem. Camera works with cheese but when i test settings in gmail chat, it does nt show video option. I tried chatting with friends using the gtalk, they are able to see me, but i cant see them in my laptop. Can anyone help me? I have installed ubuntu 9.01 in DELL inspiron.

---

### Post by Quackers on 2010-10-10
For those of you with the r5u87x camera chipset the method in the following link worked for me :-)
[https://launchpad.net/~r5u87x-loader/+archive/ppa](https://launchpad.net/~r5u87x-loader/+archive/ppa)

---

