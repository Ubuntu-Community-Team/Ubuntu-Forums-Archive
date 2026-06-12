---
title: "Logitech UAS14 not working"
date: 2010-09-21
forum: Hardware
---

### Post by ts230 on 2010-09-21
So, I got this wonderful USB Logitech UAS14, and I want to use it, and when I open v4l2ucp, I see controls for the camera, but when I try to open MPlayer to show video, I only get the following output:
```
tristan@tristan-laptop:~$ mplayer /dev/video0 
MPlayer SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /dev/video0.
Cannot seek backward in linear streams!
Seek failed


MPlayer interrupted by signal 2 in module: demux_open


MPlayer interrupted by signal 2 in module: demux_open
tristan@tristan-laptop:~$ mplayer /dev/video0 
MPlayer SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /dev/video0.
Cannot seek backward in linear streams!
Seek failed


MPlayer interrupted by signal 2 in module: demux_open


MPlayer interrupted by signal 2 in module: demux_open
tristan@tristan-laptop:~$ 

```
All info that might be relevant is that v4l2ucp shows that the driver is STV06xx. Also, since mplayer would not return, I had to press Ctrl+C a few times to get it to quit.

How would I go about getting this to work? Any help is appreciated.

---

### Post by ts230 on 2010-09-22
So I did some research on the web, which brought me here: [http://www.quickcamteam.net/devices/non-uvc-webcams](http://www.quickcamteam.net/devices/non-uvc-webcams)

I see my camera listed, the normal Logitech QuickCam Messenger, but I have no idea which driver to use, and where to get them. I could not find them using apt-get install, or Synaptic.

---

### Post by ts230 on 2010-09-22
Does anyone have any help? Please, I want to get this working soon.

---

