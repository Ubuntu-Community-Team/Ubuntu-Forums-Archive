---
title: "Hauppauge pvr 150 at /dev/video1 not working in tvtime"
date: 2005-08-16
forum: Hardware &amp; Laptops
---

### Post by RDo on 2005-08-16
can somebody please help me, the last thing for me is to get my tv-card to work and then maybe I can switch over to linux completely.
I've installed de ivtv drivers and everything is well, the device is working when I capture the card with "cp /dev/video1 test.mpg" I get static.
Now my problem is that the programs "zapping" "tvtime" xawtv" all don't work. I've tried to change the .xml file for tvtime to /dev/video1 and similar actions for the other programs. Still they don't work. Anybody an idea.
This is the output from xawtv -c /dev/video1;

[SIZE=1]This is xawtv-3.94, running on Linux/i686 (2.6.10-5-k7)
WARNING: v4l-conf is compiled without DGA support.
/dev/video1 [v4l2]: no overlay support
v4l-conf had some trouble, trying to continue anyway
ioctl: VIDIOC_QUERYMENU(id=134217728;index=1;name="44.1 kHz";reserved=3081902560): Invalid argument
ioctl: VIDIOC_QUERYMENU(id=134217729;index=1;name="Layer 1";reserved=3081902560): Invalid argument
ioctl: VIDIOC_QUERYMENU(id=134217730;index=1;name="[L1/L2] Free fmt";reserved=3081902560): Invalid argument
ioctl: VIDIOC_QUERYMENU(id=134217731;index=1;name="Stereo";reserved=3081902560): Invalid argument
ioctl: VIDIOC_QUERYMENU(id=134217732;index=1;name="Subbands 4-31/bound=4";reserved=3081902560): Invalid argument
ioctl: VIDIOC_QUERYMENU(id=134217733;index=1;name="None";reserved=3081902560): Invalid argument
ioctl: VIDIOC_QUERYMENU(id=134217734;index=1;name="CRC off";reserved=3081902560): Invalid argument
ioctl: VIDIOC_QUERYMENU(id=134217735;index=1;name="Copyright off";reserved=3081902560): Invalid argument
ioctl: VIDIOC_QUERYMENU(id=134217736;index=1;name="Copy";reserved=3081902560): Invalid argument
Segmentation fault
[/SIZE]

I don't know what else to post here, so if there is certain information needed please let me know... I want this to work .. :P

---

### Post by SickTwist on 2005-09-19
The PVR 150 uses a hardware encoder to supply video in MPEG2 format. TVtime does not have MPEG2 decoder functionality so it cannot play video directly from this card. There is information about this on the TVtime website under the ivtv section on the "supported cards" page. I'm not sure if there is a way around this.

As for the other programs that you mentioned, I don't know if they are capable of supporting the PVR 150 or not.

---

### Post by dlai on 2006-05-01
If you still have the problem the only way around it i have found is to use xawtv... to change channels and mplayer /dev/video0 to display the image

---

