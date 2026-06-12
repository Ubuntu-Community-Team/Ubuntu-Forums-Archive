---
title: "HP Pavillion dv6130us built-in Webcam"
date: 2008-02-08
forum: Hardware &amp; Laptops
---

### Post by rachel10123@msn.com on 2008-02-08
I have a HP Pavilion dv6130,and I am running Ubuntu 7.10,is there a driver that I could download to use my webcam?:(

---

### Post by linuxwizard on 2008-02-08
You may not need to install a driver. Try using Ekiga see if webcam is detected/works. Also you might have to change settings > Open Ekiga > Edit > Preferences > Video > Video Devices > try changing some of the settings there.

---

### Post by rachel10123@msn.com on 2008-02-08
No it doesn't detect ANY devices.

---

### Post by linuxwizard on 2008-02-08
type lsusb in a terminal window post results

---

### Post by rachel10123@msn.com on 2008-02-08
rae@Rae:~$ lsusb
Bus 005 Device 002: ID 05ca:1870 Ricoh Co., Ltd 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
rae@Rae:~$

---

### Post by linuxwizard on 2008-02-08
Look at the 6th post down > [http://ubuntuforums.org/showthread.php?t=421880](http://ubuntuforums.org/showthread.php?t=421880) > that is your webcam. Hopefully that will work for you.

---

### Post by rachel10123@msn.com on 2008-02-08
Thanks,but this didn't work either:confused:

---

### Post by EXCiD3 on 2008-02-08
technically your webcam SHOULD work out of the box. make sure you are using the v4l2 drivers.

Are you using gutsy?

You might check out the ricoh webcam driver here: [http://download.tuxfamily.org/arakhne/pool/ricoh-webcam-r5u870/](http://download.tuxfamily.org/arakhne/pool/ricoh-webcam-r5u870/)

---

### Post by rachel10123@msn.com on 2008-02-08
> **EXCiD3 said:**
> technically your webcam SHOULD work out of the box. make sure you are using the v4l2 drivers.

Are you using gutsy?

You might check out the ricoh webcam driver here: [http://download.tuxfamily.org/arakhne/pool/ricoh-webcam-r5u870/](http://download.tuxfamily.org/arakhne/pool/ricoh-webcam-r5u870/)



What are the v412 drivers??

Yes I am using gusty.

How do you install a BIN file?

---

### Post by linuxwizard on 2008-02-08
What are you using to see if webcam works ? Did you try Ekiga after installing the driver from that link I gave you ? Do you try changing the setting like I posted in my first post ?  Alot of webcams don't support the v4l2 drivers the webcam has to support it. Not even sure if yours support it. I would try V4l first.

You can look over this, also you can search more on it.
[http://en.wikipedia.org/wiki/V4L2](http://en.wikipedia.org/wiki/V4L2)

---

### Post by AmericanYellow on 2008-02-08
Open a Terminal.

Type:

gstreamer-properties

In the window that opens (Multimedia Systems Selector), click the 'Video' tab and at the bottom in the 'Default INPUT' section you'll see 'Plugin'. Change the Plugin to 'v4l2' - "Video for Linux 2".
Then go to 'Device' and you should see your webcam there. (something like USB 2.0 Camera).

If you test your webcam it still may not work. You'll have to restart you computer and to test your webcam using the program "CHEESE".
e
This should allow your webcam to function in few apps but not in all.

---

### Post by linuxwizard on 2008-02-09
AmericanYellow

Voice and Video (Microphone and Webcam) Support Not Implemented Yet with Pidgin > Bottom of this page > [http://developer.pidgin.im/wiki/Using%20Pidgin#VoiceandVideoMicrophoneandWebcamSupportNotImplementedYet](http://developer.pidgin.im/wiki/Using%20Pidgin#VoiceandVideoMicrophoneandWebcamSupportNotImplementedYet)

---

### Post by rachel10123@msn.com on 2008-02-09
> **AmericanYellow said:**
> Open a Terminal.

Type:

gstreamer-properties

In the window that opens (Multimedia Systems Selector), click the 'Video' tab and at the bottom in the 'Default INPUT' section you'll see 'Plugin'. Change the Plugin to 'v4l2' - "Video for Linux 2".
Then go to 'Device' and you should see your webcam there. (something like USB 2.0 Camera).

If you test your webcam it still may not work. You'll have to restart you computer and to test your webcam using the program "Pidgin".
e
This should allow your webcam to function in few apps but not in all.

It still does not detect my webcam.

---

### Post by blerinab on 2008-02-09
that worked for me, thanks. I had no idea it would be so easy.

I have a HP pavillion 6631a

---

### Post by AmericanYellow on 2008-02-09
> **linuxwizard said:**
> AmericanYellow

Voice and Video (Microphone and Webcam) Support Not Implemented Yet with Pidgin > Bottom of this page > [http://developer.pidgin.im/wiki/Using%20Pidgin#VoiceandVideoMicrophoneandWebcamSupportNotImplementedYet](http://developer.pidgin.im/wiki/Using%20Pidgin#VoiceandVideoMicrophoneandWebcamSupportNotImplementedYet)

:lolflag: HUGE mistake! I meant 'Cheese' not Pidgin. Sorry for the confusion!

---

### Post by rachel10123@msn.com on 2008-02-09
> **AmericanYellow said:**
> Open a Terminal.

Type:

gstreamer-properties

In the window that opens (Multimedia Systems Selector), click the 'Video' tab and at the bottom in the 'Default INPUT' section you'll see 'Plugin'. Change the Plugin to 'v4l2' - "Video for Linux 2".
Then go to 'Device' and you should see your webcam there. (something like USB 2.0 Camera).

If you test your webcam it still may not work. You'll have to restart you computer and to test your webcam using the program "CHEESE".
e
This should allow your webcam to function in few apps but not in all.

rae@Rae:~$ gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'pulsesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Skipping unavailable plugin 'pulsesrc'
rae@Rae:~$ cheese
creating thumbnail for /home/rae/.gnome2/cheese/videos/Video01.ogg
appending /home/rae/.gnome2/cheese/videos/Video01.ogg to thumbnail row
** Message: Probing the webcam, please ignore the following, not applicabable tries
** Message: Error running pipeline 'v4l2src ! fakesink': Cannot identify device '/dev/video0'. [v4l2_calls.c(424): gst_v4l2_open (): /pipeline0/v4l2src0:
system error: No such file or directory]
** Message: test pipeline for v4l2src failed:
[v4l2src ! fakesink]: Cannot identify device '/dev/video0'.
** Message: Error running pipeline 'v4lsrc ! video/x-raw-rgb,width=640,height=480 ! fakesink': Device "/dev/video0" does not exist. [v4l_calls.c(168): gst_v4l_open (): /pipeline1/v4lsrc0]
** Message: test pipeline for v4lsrc failed:
[v4lsrc ! video/x-raw-rgb,width=640,height=480 ! fakesink]: Device "/dev/video0" does not exist.
** Message: Error running pipeline 'v4lsrc ! video/x-raw-yuv,width=640,height=480 ! fakesink': Device "/dev/video0" does not exist. [v4l_calls.c(168): gst_v4l_open (): /pipeline2/v4lsrc1]
** Message: test pipeline for v4lsrc failed:
[v4lsrc ! video/x-raw-yuv,width=640,height=480 ! fakesink]: Device "/dev/video0" does not exist.
** Message: Error running pipeline 'v4lsrc ! video/x-raw-rgb,width=320,height=240 ! fakesink': Device "/dev/video0" does not exist. [v4l_calls.c(168): gst_v4l_open (): /pipeline3/v4lsrc2]
** Message: test pipeline for v4lsrc failed:
[v4lsrc ! video/x-raw-rgb,width=320,height=240 ! fakesink]: Device "/dev/video0" does not exist.
** Message: Error running pipeline 'v4lsrc ! video/x-raw-rgb,width=1280,height=960 ! fakesink': Device "/dev/video0" does not exist. [v4l_calls.c(168): gst_v4l_open (): /pipeline4/v4lsrc3]
** Message: test pipeline for v4lsrc failed:
[v4lsrc ! video/x-raw-rgb,width=1280,height=960 ! fakesink]: Device "/dev/video0" does not exist.
** Message: Error running pipeline 'v4lsrc ! video/x-raw-rgb,width=174,height=144 ! fakesink': Device "/dev/video0" does not exist. [v4l_calls.c(168): gst_v4l_open (): /pipeline5/v4lsrc4]
** Message: test pipeline for v4lsrc failed:
[v4lsrc ! video/x-raw-rgb,width=174,height=144 ! fakesink]: Device "/dev/video0" does not exist.
** Message: Error running pipeline 'v4lsrc ! video/x-raw-rgb,width=160,height=120 ! fakesink': Device "/dev/video0" does not exist. [v4l_calls.c(168): gst_v4l_open (): /pipeline6/v4lsrc5]
** Message: test pipeline for v4lsrc failed:
[v4lsrc ! video/x-raw-rgb,width=160,height=120 ! fakesink]: Device "/dev/video0" does not exist.
** Message: Error running pipeline 'v4lsrc ! fakesink': Device "/dev/video0" does not exist. [v4l_calls.c(168): gst_v4l_open (): /pipeline7/v4lsrc6]
** Message: test pipeline for v4lsrc failed:
[v4lsrc ! fakesink]: Device "/dev/video0" does not exist.
using source: videotestsrc

This is what happens.

---

### Post by AmericanYellow on 2008-02-14
Does the webcam light turn on when you try to use Cheese??

---

