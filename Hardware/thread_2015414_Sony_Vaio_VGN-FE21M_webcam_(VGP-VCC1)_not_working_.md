---
title: "Sony Vaio VGN-FE21M webcam (VGP-VCC1) not working in 12.04"
date: 2012-07-03
forum: Hardware
---

### Post by sicco1 on 2012-07-03
The Sony 'motion eye' webcam built-in the Vaio VGN-FE21M laptop doesn't work in Ubuntu 12.04 32bit. I also tried live discs of 11.10 and 11.04, but *cheese* didn't recognize the webcam there either.

According to the *lsusb* info I have a 0ac8:c002 Z-Star Microelectronics Corp. Visual Communication Camera VGP-VCC1 webcam:
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 054c:0281 Sony Corp. 
Bus 001 Device 005: ID 0ac8:c002 Z-Star Microelectronics Corp. Visual Communication Camera VGP-VCC1
Bus 002 Device 002: ID 046d:c030 Logitech, Inc. iFeel Mouse
Bus 004 Device 002: ID 044e:300c Alps Electric Co., Ltd Bluetooth Controller (ALPS/UGPZ6)
```When I run Cheese the following lines are added when checking *dmesg*:
```
[ 1071.486601] gspca_main: ISOC data error: [14] len=0, status=-71
[ 1071.686580] gspca_main: ISOC data error: [13] len=0, status=-71
[ 1071.786597] gspca_main: ISOC data error: [13] len=0, status=-71
[ 1071.818572] gspca_main: ISOC data error: [23] len=0, status=-71
[ 1071.887557] video_source:sr[2613]: segfault at 4 ip 0038bc4c sp af2cedf0 error 4 in libgstreamer-0.10.so.0.30.0[33d000+e3000]
[ 1072.018576] gspca_main: ISOC data error: [23] len=0, status=-71
[ 1072.118578] gspca_main: ISOC data error: [22] len=0, status=-71
```I know about the R5U87x Userspace Tools, which seems to support similar webcams, but it [doesn't support my version]("https://bitbucket.org/ahixon/r5u87x/src/a9b2171d762b/docs/model_matrix.txt") (VGP-VCC1) and installing it thus failed.

Does anyone know how to fix this/proceed in any way or should I file a bug? My problem seems to be [similar to this bug]("https://bugs.launchpad.net/ubuntu/+source/gspca/+bug/990749"), but unlike it I didn't have any installation problems when upgrading from 11.10 to 12.04.

---

### Post by forkandles on 2012-07-03
This link is for Mint but it should work with Ubuntu and it may help you:

[http://community.linuxmint.com/tutorial/view/219](http://community.linuxmint.com/tutorial/view/219)

---

### Post by sicco1 on 2012-07-03
Thank you for the advice, but sadly it doesn't fix my problem.

---

### Post by forkandles on 2012-07-03
This will fix it.

Save yourself a lot of time and heartache, go on ebay and buy a cheap webcam such as the Logitech E3500 which works perfectly on most Linux systems, including Ubuntu 12.04.

I have just tested my old E3500 in 12.04 and everything works fine.

I once spent **5 days** trying to get a MS Windows webcam (something like a MS LifeCam VX-1000) to work in Linux before the pain became too much and I bought a nice cheap Logitech E3500.
 It solved the problem at a stroke. Don't waste any more time trying to get the built-in webcam to work.

---

### Post by sicco1 on 2012-07-03
This is an option yes, but I still would like to fix the built-in webcam. I won't be bringing such an external webcam with me when travelling with the laptop, so I still need the built-in webcam to work.

---

### Post by forkandles on 2012-07-03
This person managed to get his identical webcam (Z star 0ac8:c002) working in Kubuntu 10.04 so there is hope for you.

[http://www.kubuntuforums.net/showthread.php?48551-SOLVED-How-to-load-modules-on-startup](http://www.kubuntuforums.net/showthread.php?48551-SOLVED-How-to-load-modules-on-startup)

---

### Post by sicco1 on 2012-07-03
Thanks for the continuing advice! I already found that thread and tried the suggested fix, but it didn't work.

---

### Post by AlanR8 on 2012-07-03
I had/have a Sony Vaio VGN, can't remember the model but the webcam was the bane of my life. I did get it working and have kept the thread addresses I used to use so give them a go but be warned they are quite old now.

Let us know how you get on.

[http://ubuntuforums.org/showthread.php?t=1544564](http://ubuntuforums.org/showthread.php?t=1544564)

[http://ubuntuforums.org/showthread.php?t=968381](http://ubuntuforums.org/showthread.php?t=968381)

---

### Post by sicco1 on 2012-07-03
Thank you AlenR8. I also found those threads already and they fix their webcams using R5U87x Userspace Tools. This works for webcam models VGP-VCC2 till VGP-VCC9, but not for my VGP-VCC1. Your laptop is a VGN-FZ21S which has a VCC8.

---

### Post by sicco1 on 2012-07-03
I might be on to something. I think the GSPCA driver should support my webcam as it is [shown in this list]("http://mxhaard.free.fr/spca5xx.html") and [this one]("http://lxr.linux.no/#linux+v3.2/Documentation/video4linux/gspca.txt#L292"). Sadly enough, the GSPCA information for 12.04 in launchpad [doesn't list my model]("https://bazaar.launchpad.net/%7Eubuntu-branches/ubuntu/precise/gspca/precise/view/head:/READ_AND_INSTALL"). I got to go now, but I'll be diving into this later tonight.

---

### Post by utt73 on 2013-03-24
I have the same camera,  Z-Star Microelectronics Corp. Visual Communication Camera VGP-VCC1 (built into a Sony Vaio PCG-7N2L laptop). Did you ever get [COLOR=#000000]the camera working?[/COLOR]

---

### Post by sicco1 on 2013-03-25
I didn't get it to work yet. I did create a [bug report]("https://bugs.launchpad.net/ubuntu/+source/v4l-utils/+bug/1134565") though on Launchpad. Do you have the same problem? If so, then it would be really nice if you could click the following green button/link at the top of the bug report: "[COLOR=#008000]This bug affects 1 person. Does this bug affect you?[/COLOR]", and post a comment describing your problem and details. There are some people helping me out and you might want to help further by answering their questions with me.

---

