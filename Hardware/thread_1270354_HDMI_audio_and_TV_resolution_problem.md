---
title: "HDMI audio and TV resolution problem"
date: 2009-09-19
forum: Hardware
---

### Post by XeroXer on 2009-09-19
Hi all!

I am trying to get ubuntu with XBMC to work on my HTPC connected to my Panasonic Viera TX-P42X10Y.
So far I have two problems, HDMI audio and the resolution. Both these before I have installed XBMC.

The resolution problem is that the ubuntu/nvidia area overflows the TV view area. I have tried changing the aspect ratio on the television with no result.

The audio problem is that for some reason I get no sound through the HDMI connection. I have followed a few guides and tutorials but the problem persists

aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

aplay -L
```
front:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    Front speakers
surround40:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Digital
    IEC958 (S/PDIF) Digital Audio Output
hdmi:CARD=NVidia,DEV=0
    HDA NVidia, NVIDIA HDMI
    HDMI Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)
```

cat /proc/asound/devices
```
  2:        : timer
  3:        : sequencer
  4: [ 0- 3]: digital audio playback
  5: [ 0- 2]: digital audio capture
  6: [ 0- 1]: digital audio playback
  7: [ 0- 0]: digital audio playback
  8: [ 0- 0]: digital audio capture
  9: [ 0]   : control
```

Any help would be greatly appreciated.

**UPDATE WITH RESOLUTION PROBLEM:**
To show what I mean with "the ubuntu/nvidia area overflows the TV view area" I uploaded two pictures. One is taken as a print screen in Ubuntu and shows what I should see. The other is a camera picture of the TV and what I DO see.
As you can see the all the edges gets cut-off.


*Print screen from the Ubuntu HTPC:*
[IMG]http://ubuntuforums.org/picture.php?albumid=1375&pictureid=4757[/IMG]
*Camera Picture of the TV with the Ubuntu HTPC:*
[IMG]http://ubuntuforums.org/picture.php?albumid=1375&pictureid=4758[/IMG]

---

### Post by elmagique on 2009-10-10
exact same problem here. If I find something to solve it I'll tell ya

---

### Post by AppleBonker on 2009-10-10
I can't help much with the audio problem as I have never owned hardware that supported audio over HDMI from the PC.

Wow, I'm slow.  I just realized you have the tv model listed in the OP.  Have you ever connected a different PC to that TV?  I'm just wondering if it is an overscan issue.  I'll have to look into that particular tv model.

---

### Post by AppleBonker on 2009-10-10
I'm actually not to familiar with that model.  Is that a 720p set?  It looks like it is an overseas model of the US version TC-P42X1 set.  What resolution do you have your video card set to display.  Also, what screen format are you using (press the format button on the remote).

---

### Post by t-timmy on 2009-10-30
Exact same video problem here.

I have a samsung 37'' lcd screen, and an HP DV4 1220us laptop.

The resolution <---- I started this sentence to specify the resolution of the screen, but now I'm happy I have a different way to finish it ----> was to enable the restricted drivers under System -> Administration -> Hardware Drivers.

After a reboot the edges are now fine.

---

