---
title: "Sore eyes: can't change refresh rate on external monitor"
date: 2007-11-10
forum: Hardware &amp; Laptops
---

### Post by raindog on 2007-11-10
I am running a hp pavilion ze5345US.  It has an ati 300m graphics card.  I am running the default driver from Gutsy for it.  Also, I am using an external monitor (ASTVision 7L) as my brother damaged the laptop's LCD screen and it has large areas of it that are unviewable.  Now, here's my problem.  I can't get the monitor to run at a proper refresh rate.  I've tried in both ubuntu and Kubuntu to adjust the screen settings and when i attempt to I get only a 640x480 display on the external monitor and then the app for changing the settings quits and no changed settings will persist.  Also, after doing this the external monitor only will flicker and distort a bit until I restart X.  I've had this problem since Breezy but the flicker and distortions have only started since Gutsy.  (Also, in Gutsy visualizations in Rhythmbox or playing a DVD don't display on the external monitor anymore, but they appear normally on the damaged LCD screen.)

I really need to get this issue fixed as my eyesight is being effected by the low refresh rates and I cannot afford to build a new desktop machine right now.  I've searched high and low for remedies without success.  If you can provide any suggestions or help I would be greatly appreciative...and my eyes wouldn't hurt so much.

---

### Post by matthewcraig on 2007-11-10
Sorry to hear you are having trouble.  Have you tried to set your resolution and refresh rates with the new Screens and Graphics tool in Gutsy?

---

### Post by raindog on 2007-11-10
Yes.  When I select the correct monitor and attempt to change the resolution and refresh rates the settings app closes without any changes taking effect.  This happens in both Ubuntu and Kubuntu.  I'm currently researching adding a custom modeline to my xorg.conf but I'm hesitant as I know incorrect values can damage your monitor and your graphics card.  Thanks for the input though.

---

### Post by raindog on 2007-11-11
bump

---

### Post by kelvin spratt on 2007-11-11
Your problem may be down to your external monitor not matching the graphics card

---

### Post by raindog on 2007-11-11
I've had the same issue with 4 separate monitors.  Also, why does the screens & monitors app in both Ubuntu and Kubuntu close unexpectedly and not let me save changes?

If I had enough money I'd just ditch this laptop and build a new desktop, but that is not an option.  A new LCD for the laptop would run me $250-300 as well.  

I think it has something to do with the opensource ati driver.

---

### Post by raindog on 2007-11-12
I've read the radeon man pages as well as info on xrandr.

From [here]("https://help.ubuntu.com/community/RadeonDriver") I found this:

> Since Ubuntu 7.10, the "ati" driver has support for xrandr 1.2, and xrandr is now the preferred way to set up dual-head. See [WWW] [http://wiki.debian.org/XStrikeForce/HowToRandR12](http://wiki.debian.org/XStrikeForce/HowToRandR12) for detailed documentation, or [WWW] [http://www.intellinuxgraphics.org/dualhead.html](http://www.intellinuxgraphics.org/dualhead.html) for more examples.

I am using an RS200 Radeon IGP345M with the 'ati' opensource driver.

> xrandr --verbose
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 1280 x 1200
VGA-0 connected 1024x768+0+0 (0x51) normal (normal left inverted right) 0mm x 0mm
        Identifier: 0x4c
        Timestamp:  894096741
        Subpixel:   no subpixels
        Clones:
        CRTC:       1
        CRTCs:      0 1
        load_detection: 1 (0x00000001) range:  (0,1)
  1280x768 (0x4f)   80.1MHz
        h: width  1280 start 1344 end 1480 total 1680 skew    0 clock   47.7KHz
        v: height  768 start  769 end  772 total  795           clock   60.0Hz
  1152x768 (0x50)   65.0MHz +HSync +VSync
        h: width  1152 start 1178 end 1314 total 1472 skew    0 clock   44.2KHz
        v: height  768 start  771 end  777 total  806           clock   54.8Hz
  1024x768 (0x51)   65.0MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock   48.4KHz
        v: height  768 start  771 end  777 total  806           clock   60.0Hz
  800x600 (0x52)   40.0MHz +HSync +VSync
        h: width   800 start  840 end  968 total 1056 skew    0 clock   37.9KHz
        v: height  600 start  601 end  605 total  628           clock   60.3Hz
  800x600 (0x53)   36.0MHz +HSync +VSync
        h: width   800 start  824 end  896 total 1024 skew    0 clock   35.2KHz
        v: height  600 start  601 end  603 total  625           clock   56.2Hz
  640x480 (0x54)   25.2MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock   31.5KHz
        v: height  480 start  490 end  492 total  525           clock   59.9Hz
LVDS connected 1024x768+0+0 (0x55) normal (normal left inverted right) 0mm x 0mm
        Identifier: 0x4d
        Timestamp:  894096741
        Subpixel:   horizontal rgb
        Clones:
        CRTC:       0
        CRTCs:      0
                scaler: full
        backlight: 255 (0x000000ff) range:  (0,255)
  1024x768 (0x55)   65.0MHz
        h: width  1024 start 1040 end 1176 total 1344 skew    0 clock   48.4KHz
        v: height  768 start  770 end  776 total  806           clock   60.0Hz
  1024x768 (0x51)   65.0MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock   48.4KHz
        v: height  768 start  771 end  777 total  806           clock   60.0Hz
  800x600 (0x52)   40.0MHz +HSync +VSync
        h: width   800 start  840 end  968 total 1056 skew    0 clock   37.9KHz
        v: height  600 start  601 end  605 total  628           clock   60.3Hz
  640x480 (0x54)   25.2MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock   31.5KHz
        v: height  480 start  490 end  492 total  525           clock   59.9Hz
S-video disconnected (normal left inverted right)
        Identifier: 0x4e
        Timestamp:  894096741
        Subpixel:   no subpixels
        Clones:
        CRTCs:      0 1
                tv_standard: ntsc
        tv_vertical_position: 0 (0x00000000) range:  (-5,5)
        tv_horizontal_position: 0 (0x00000000) range:  (-5,5)
        tv_horizontal_size: 0 (0x00000000) range:  (-5,5)
        load_detection: 0 (0x00000000) range:  (0,1)

I'm still desparate to find the way to set my external monitor to a higher refresh rate as my eyes can't take this anymore.  If you can offer some assistance please do.  I would be terribly grateful.

---

### Post by raindog on 2007-11-16
bump

---

### Post by shelbydz on 2007-12-05
I had a similar problem. I checked my xorg.conf file and found that there were two lines defining the refresh rate for my resolution. One was 60Hz and the other was 72Hz. I commented out the line that had 60Hz and then the settings in KDE finally let me change the refresh rate. 

If you need more specifics, let me know.

---

