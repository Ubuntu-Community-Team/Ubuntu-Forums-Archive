---
title: "LCD works, Mitsubishi 2060u does not (Intel 945G)"
date: 2009-09-14
forum: Hardware
---

### Post by rextwelve on 2009-09-14
My Dell LCD monitor works great with 9.04. When I connect my Mitsubishi Diamond Pro 2060u CRT, X displays garbage. I'm using on board Intel graphics hardware (945G). 

Here is what happens:

On starting the computer the CRT shows the bios stuff as you would expect. Then the graphic comes up with progress indicator and that displays fine. After that the video is either completely distorted or there might just be a couple flickering horizontal lines. I can ctrl-alt-f1 to get the text login. It seems like I need to edit xorg.conf but (1) I'm not really sure how (clock, hdisp, hsyncstart hsyncend htotal, vdisp, ... ????) and (2) everything I read says that I shouldn't have to.

If I should edit xorg.conf, does anyone know what the ModeLine should be? Is there a better (right) way to fix this? I'm sure that 9.05 should work with this monitor and I would really appreciate any help.


Here some information on the Mitsubishi Diamond Pro 2060u:


```
Size: 22"
Aperture grille pitch: 0.24mm
Phosphor pitch: 0.25mm

Input Signal
Video: 0.7p-p analog RGB
Sync: Seperate H, V sync., Composite sync., or Sync on Green

Scanning Frequency
Horizontal: 30 - 121kHz
Frequency: 50 - 160Hz
Resolution (HxV): 2048 dots x 1536 lines Non-Inerlaced maximum addressable resolution format at 75Hz
Blanking Time
Horizontal: >= 2.0 usec (typ.)
Vertical: >= 400 usec (typ.)


    PRESET                     Polarity
    TIMING       Fh(kHz)  Fv (Hz) H V 
 640 x 480  N.I.    31.5     60.0 – – 
 800 x 600  N.I.    46.8     75.0 + + 
1024 x 768  N.I.    60.0     75.0 + + 
1024 x 768  N.I.    68.7     85.0 + + 
1280 x 1024 N.I.    80.0     75.0 + + 
1280 x 1024 N.I.    91.1     85.0 + + 
1600 x 1200 N.I.    93.8     75.0 + + 
1600 x 1200 N.I.   106.3     85.0 + + 
1920 x 1440 N.I.   112.5     75.0 – + 
1800 x 1350 N.I.   120.4     85.0 – –

```

---

