---
title: "Logitech webcam doesn't work with skype"
date: 2009-04-25
forum: Hardware
---

### Post by julian.b on 2009-04-25
I have a Logitech webcam. In older versions of Kubuntu it was enough to plug the usb in and the webcam worked. Unfortunately the device doesn't work with skype anymore in newer versions of Kubuntu (8.10 and 9.04). I can only see colorful vertical stripes in skype. The webcam, however, works fine with cheese. EasyCam program did not help to solve the problem. I'd be glad if anybody could help me.

lsusb:
```
...
Bus 003 Device 002: ID 046d:0928 Logitech, Inc. Quickcam Express
...
```

lsmod | grep videodev:
```
videodev               45184  2 gspca_main,compat_ioctl32
v4l1_compat            23940  1 videodev
```

---

### Post by yahs on 2009-04-27
My webcam is logitech quickcam communicate stx

lsusb output

Bus 002 Device 002: ID 046d:08ad Logitech, Inc. QuickCam Communicate STX

I'm still running 8.04 as hardy uses v4l1 whereas intrepid and jaunty use v4l2. So if I try and run skype in Intrepid or Jaunty I get a green screen. 

This is a quick fix which works for me if I want to use Skype in Intrepid or Jaunty.

Open a terminal and type

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

You can test your webcam under v4l1 and v4l2 by running gstreamer-properties from a terminal

---

### Post by tonyps on 2009-04-27
I used the command line info you mentioned and the webcam works.. however, I cannot get it to dispay video from within Skype?? Any ideas??

---

### Post by yahs on 2009-04-27
As I use 8.04 I have only tested to see if the command works and it does as long as you leave the terminal open. To make skype work in Intrepid or Jaunty without using a terminal you can check out this post which has a title "Skype green video"

[http://ubuntuforums.org/showthread.php?p=7064653](http://ubuntuforums.org/showthread.php?p=7064653)

---

### Post by julian.b on 2009-04-27
yahs thanks for the link, it worked,

I just want to tell everybody, read the link carefully. If one of the commands gives you an error you should try another command and/or install the missing packages!!!

Thank you

---

### Post by johnaaronrose on 2009-04-28
The problem I have with skype is the microphone not working. Any ideas?

---

### Post by johnaaronrose on 2009-04-29
Problem in jaunty is that not all pulse audio packages are installed and sound needs to be configured for pulse audio. This has at least one other advantage: can directly record sound from computer input e.g. playing radio station. URL for solution is:
[http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html](http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html)

---

### Post by fly-hi on 2009-06-06
I've followed the threads an now have my webcam working in Ekiga (was working) and camorama (only works with LD_PRELOAD...)   However, skype doesn't work:

ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.

I am on amd64 and use the 64 bit version of skype (2.0.0.72).  Would this be related?

I also have a problem with my sound recording.  The problem seems to be that the Input Source defaults to "Front Mic" on my hardware, even though this is not recognized by the settings.  The workaround is to create an executable (chmod +x) called "skype" in /usr/local/bin :

#! /bin/bash
amixer sset "Input Source" "Front Mic"
amixer sset "Input Source" "Mic"
/usr/bin/skype
return 0

---

### Post by fly-hi on 2009-06-06
Well, so much for being clever.  My logitech webcam now works after removing skype and installing from medibuntu.

---

