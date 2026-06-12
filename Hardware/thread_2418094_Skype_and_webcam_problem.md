---
title: "Skype and webcam problem"
date: 2019-05-01
forum: Hardware
---

### Post by trenien2 on 2019-05-01
Hi all.
So here is the problem : whereas my webcam works properly with a number of applications (jitsi, vlc etc...) it doesn't with skype (and cheese). I've looked around and tried a couple of solutions, but no luck so far. Any idea what I could do ?

I'm under xubuntu 18.10, the webcam is a logitech quickcam IM/connect
here is the result of an lsusb :

```
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 058f:6364 Alcor Micro Corp. AU6477 Card Reader Controller
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 005: ID 046d:08d9 Logitech, Inc. QuickCam IM/Connect
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 046d:c31c Logitech, Inc. Keyboard K120
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 002: ID 046d:c077 Logitech, Inc. M105 Optical Mouse
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

the commands I've tried with no success are the following :
```
LD_PRELOAD=/usr/lib/x86_64-linux-gnu/libv4l/v4l2convert.so /usr/bin/skypeforlinux

LD_PRELOAD=/usr/lib/x86_64-linux-gnu/libv4l/v4l1compat.so /usr/bin/skypeforlinux
```

Any idea ?

---

### Post by $yl9pAR%t on 2019-05-07
Not my thread, but BUMP. I am interested because I have the same problem.

---

### Post by wildmanne39 on 2019-05-07
Hello rumburak888, please instead of bumping someone else's thread always start your own for support.

Thanks!

---

### Post by mastablasta on 2019-05-08
> **trenien2 said:**
> 
the commands I've tried with no success are the following :
```
LD_PRELOAD=/usr/lib/x86_64-linux-gnu/libv4l/v4l2convert.so /usr/bin/skypeforlinux

LD_PRELOAD=/usr/lib/x86_64-linux-gnu/libv4l/v4l1compat.so /usr/bin/skypeforlinux
```

Any idea ?


interesting... it looks like it is not initialised by skype in the same way as it is in other apps.

you could try in skype4linux forums. i found them a helpful bunch of people back in the day. however, before you go there, run skype from terminal and check for any error messages being thrown out in the terminal window. perhaps they will give a clue why the camera is not initialised.
does this camera come with a mic? is the mic working?

are the libraries you are preloading installed? are they at the place you indicated in the command?

i have an old cam that needed these and worked well until 12.04. haven't used it in a while and last time (in 14.04) i got the picture but it was upside down. :) so yeah sometimes linux drivers are a bit strange or wrong ones get loaded.

---

### Post by trenien2 on 2019-05-12
Well, unfortunately the libraries are installed and at the spot written in the command. If only...
So far, no luck finding anything in skype4linux forum (but that is a mess, so no luck so far).

To note, as wrote before, the webcam doesn't work with cheese either, and that particular software doesn't even detect it. However, skype does see the camera, it just gets no image from it (black video screen).

---

