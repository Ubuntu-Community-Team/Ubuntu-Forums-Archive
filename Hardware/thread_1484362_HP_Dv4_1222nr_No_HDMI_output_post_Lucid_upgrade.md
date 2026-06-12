---
title: "HP Dv4 1222nr No HDMI output post Lucid upgrade"
date: 2010-05-15
forum: Hardware
---

### Post by jstalnak on 2010-05-15
Upgraded my Dv4 yesterday. All appears to be working very well except HDMI output. Both audio and Monitor controls recognize the HDMI hardware. I can attach an HDMI cable to my Sharp HD TV and the system correctly detects that there is a device attached (though the system says it's a 37" rather than a 32" monitor). I can manipulate the Monitors values for the display and enable/disable it. But, there is no output to the display. It remains blank. For video xrandr output shows:

<quote>
nak@eregion ~>xrandr
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 2640 x 800
VGA-0 disconnected (normal left inverted right x axis y axis)
HDMI-0 connected 1360x768+1280+32 (normal left inverted right x axis y axis) 820mm x 460mm
   1360x768       60.0* 
   1024x768       75.0     70.1     60.0  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     59.9  
   720x400        70.1  
LVDS connected 1280x800+0+0 (normal left inverted right x axis y axis) 303mm x 190mm
   1280x800       60.0*+
   1280x720       59.9  
   1152x768       59.8  
   1024x768       59.9  
   800x600        59.9  
   640x480        59.4 
</quote>

This is correct.  For audio, aplay shows:

<quote>
nak@eregion ~>aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
</quote>

That is also correct.

HDMI output worked under Karmic, though with a quirk. Under Karmic plugging in the HDMI cable automatically mirrored desktop and that was my only option (I was never able to get an extended desktop enable successfully). I'm running:

<quote>
nak@eregion ~>uname -a
Linux eregion 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64 GNU/Linux
</quote>

Anyone with any ideas?  I've searched the Ubuntu forums but no one seems to have this issue (that is, what appears to be correctly identified hardware yet without expected output).

---

