---
title: "atitvout was working before todays update.... not anymore"
date: 2009-02-03
forum: Installation &amp; Upgrades
---

### Post by aczar on 2009-02-03
I just ran the update manager today, and if I remember right the ati drivers were updated... now my s-video stopped working.
because i'm using an rf modulator, i need to be able to force the s-video detection. i did this with 

```
sudo xrandr --output S-video --set load_detection 1
```

and then used the atitvout tool to enable/switch to TV or LCD mode. It was all working beautifully until today, and I can't figure out why. This is what I get if I run detect with atitvout

```
alex@alex-laptop:/etc/X11$ sudo atitvout -f detect
[sudo] password for alex: 
Forcing Rage Mobility/Rage 3D Pro LT mode
LCD is attached.
TV is attached via S-Video.

```

but then if i try to switch modes it doesnt do anything at all. how can I find out what version my ati drivers are? how can i check if they were updated today? if they were, and that is the problem.... how do i go back?? 
thanks in advance....
alex

---

### Post by aczar on 2009-02-03
I've made some progress I think. I've been playing around with xrandr and have managed to get the tv flickering, but nothing is really visable. This is what I've done:

```
xrandr --output S-video --set load_detection 1
xrandr --output S-video --set tv_standard ntsc
xrandr --addmode S-video 800x600
xrandr --output S-video --same-as LVDS
xrandr --output S-video --mode 800x600
```

The light on the rf modulator goes on, and the tv goes from the normal static to a lot of crazy flickering. 

some more info..

```
alex@alex-laptop:/etc/X11$ xrandr --verbose
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 1024 x 1024
VGA-0 disconnected (normal left inverted right x axis y axis)
        Identifier: 0x4c
        Timestamp:  40002
        Subpixel:   no subpixels
        Clones:    
        CRTCs:      0 1
        load_detection: 0 (0x00000000) range:  (0,1)
LVDS connected 1024x768+0+0 (0x4f) normal (normal left inverted right x axis y axis) 0mm x 0mm
        Identifier: 0x4d
        Timestamp:  40002
        Subpixel:   horizontal rgb
        Clones:    
        CRTC:       0
        CRTCs:      0
                scaler: full
        backlight: 255 (0x000000ff) range:  (0,255)
  1024x768 (0x4f)   65.0MHz
        h: width  1024 start 1040 end 1688 total 1344 skew    0 clock   48.4KHz
        v: height  768 start  771 end  777 total  806           clock   60.0Hz
  1024x768 (0x50)   65.0MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock   48.4KHz
        v: height  768 start  771 end  777 total  806           clock   60.0Hz
  800x600 (0x51)   40.0MHz +HSync +VSync
        h: width   800 start  840 end  968 total 1056 skew    0 clock   37.9KHz
        v: height  600 start  601 end  605 total  628           clock   60.3Hz
  640x480 (0x52)   25.2MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock   31.5KHz
        v: height  480 start  490 end  492 total  525           clock   59.9Hz
S-video connected 800x600+0+0 (0x53) normal (normal left inverted right x axis y axis) 0mm x 0mm
	Identifier: 0x4e
	Timestamp:  40002
	Subpixel:   no subpixels
	Clones:    
	CRTC:       1
	CRTCs:      0 1
		tv_standard: ntsc
	tv_vertical_position: 0 (0x00000000) range:  (-5,5)
	tv_horizontal_position: 0 (0x00000000) range:  (-5,5)
	tv_horizontal_size: 0 (0x00000000) range:  (-5,5)
	load_detection: 0 (0x00000000) range:  (0,1)
  800x600 (0x53)   38.2MHz -HSync +VSync
        h: width   800 start  832 end  912 total 1024 skew    0 clock   37.4KHz
        v: height  600 start  603 end  607 total  624           clock   59.9Hz
  800x600 (0x51)   40.0MHz +HSync +VSync
        h: width   800 start  840 end  968 total 1056 skew    0 clock   37.9KHz
        v: height  600 start  601 end  605 total  628           clock   60.3Hz

```

ideas anyone?

---

### Post by aczar on 2009-03-24
bump

---

