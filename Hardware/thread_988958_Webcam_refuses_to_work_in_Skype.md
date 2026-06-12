---
title: "Webcam refuses to work in Skype"
date: 2008-11-21
forum: Hardware
---

### Post by Trab on 2008-11-21
Webcam: Logitech Communicate Deluxe
driver: uvcvideo
Ubuntu 8.10 (fairly clean install)

Last night I was using my webcam and Skype to talk with my brother who lives in Oregon.

It crashed part-way through (my own fault, had it full-screen while on dual monitors, went to a conference call which kills the video...the screen stayed black so I nuked skype).


once I started it again, the video refused to work.

Normally, a restart will fix this (before installing 8.10, this would happen very infrequently, and restarting fixed it).

Well, not wanting to restart whenever that happened, I decided to look around. I played with modprobe -r, v4l-conf (i had to kill this cause it blacked my screen) and gstreamer-properties, but it still didn't work.

well, after a reboot, i went to try skype, and it didnt work in the video.

going to gstreamer-properties and clicking video and test gave me a live video.
the settings for default input were 

Plugin: v4l2
Device: (usb name of device here)


going back into it now, it says unknown for device, and refuses to show me the video again.


here is the skype output

Skype Xv: Xv ports available: 4
Skype XShm: XShm support enabled
Skype Xv: Using Xv port 131
libv4l2: error dequeuing buf: Invalid argument


I'm going to try a restart again.

I have 2 main questions:

1) if after a restart it doesn't work, what else can I try?
2) when it fails like that, is there a way to reload whatever is broken without a restart? it seems like there should be.

---

### Post by Trab on 2008-11-21
a second restart fixed skype. but i would still like to know if its possible to fix this without restarting?

---

### Post by Yezinki on 2008-11-21
Get a quick cam pro 9000.

---

### Post by Yezinki on 2008-11-21
[http://ubuntuforums.org/showthread.php?t=966398&page=17](http://ubuntuforums.org/showthread.php?t=966398&page=17)

---

