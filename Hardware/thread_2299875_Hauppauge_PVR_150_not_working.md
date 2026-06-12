---
title: "Hauppauge PVR 150 not working"
date: 2015-10-22
forum: Hardware
---

### Post by Dukenukemx on 2015-10-22
Just got myself a cheap PVR 150 and wanted to use it in MythTV but so far nothing works with it.  TVTime doesn't see jack and VLC only shows snow for Video32.  Video0 and Video24 don't do anything.  TVheadend doesn't even detect it.  TVTime says "ivtv: inappropriate ioctl for device".  BTW Ubuntu 15.04.  

This is what I see with "dmesg | grep ivtv".  What do I need to do to fix this?  
```

[   13.344795] ivtv: Start initialization, version 1.4.3
[   13.344876] ivtv0: Initializing card 0
[   13.344879] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   13.402156] ivtv0: Autodetected Hauppauge WinTV PVR-150
[   13.470480] cx25840 14-0044: cx25843-24 found @ 0x88 (ivtv i2c driver #0)
[   14.146040] wm8775 14-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   14.398984] ivtv0: Registered device video0 for encoder MPG (4096 kB)
[   14.399052] ivtv0: Registered device video32 for encoder YUV (2048 kB)
[   14.399087] ivtv0: Registered device vbi0 for encoder VBI (1024 kB)
[   14.399122] ivtv0: Registered device video24 for encoder PCM (320 kB)
[   14.399159] ivtv0: Registered device radio0 for encoder radio
[   14.399160] ivtv0: Initialized card: Hauppauge WinTV PVR-150
[   14.399204] ivtv: End initialization
[   14.423667] ivtv-alsa: module loading...
[   16.673626] ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[   16.872156] ivtv0: Encoder revision: 0x02060039

```

---

### Post by MartyBuntu on 2015-10-22
What is the card connected to?

---

### Post by Dukenukemx on 2015-10-22
A Dreamcast for testing.  Both to S-Video and Composite.  Also an antenna for ATSC.

---

### Post by Dukenukemx on 2015-10-22
The computer is a Athlon II X4 and the motherboard is a Asus M2A-VM with a Radeon 6570 running Ubuntu 15.04, just in case if you're wondering.

---

### Post by MartyBuntu on 2015-10-22
I don't know about the Dreamcast, but I'm pretty sure the PVR-150 doesn't have a digital ATSC tuner. I have one currently installed in my machine, along with an HVR-1850.

---

### Post by Dukenukemx on 2015-10-22
Really?  Oh well, I have plenty of other tuners with ATSC, but I mainly bought it for S-Video and Composite input, which don't work.  MartyBuntu what did you do to get it working?  I'm just using the Dreamcast as a video source to test the picture.  Ultimately it's going to be hooked up to my cable box.

---

### Post by blm-ubunet on 2015-10-23
This might select mpeg encoder output & s-video input source:-

```
v4l2-ctl -d /dev/video0 -i 2
cat /dev/video0 > test-svideo.mpg

ffplay -i test-svideo.mpg
```

More info:
v4l2-ctl --info
v4l2-ctl --help-io

---

