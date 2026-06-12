---
title: "external screen resolution on laptop"
date: 2009-06-09
forum: Hardware
---

### Post by tokyoahead on 2009-06-09
Hi,

I am running a Samsung 970p on a Acer 3810T Laptop with the latest Ubuntu. 
The native resolution of the Samsung is 1280x1024, the one of the laptop is 1366x768. The Laptop resolution works fine when the ext. screen is unplugged, when it's plugged in, I get only 1024x768 on the Samsung.

When I run xrandr I get the following:

```
# xrandr
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 1900 x 1200
VGA connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1360x768       59.8  
   1152x864       60.0  
   1024x768       60.0* 
   800x600        60.3  
   640x480        59.9  
LVDS connected (normal left inverted right x axis y axis)
   1366x768       60.0 +
   1360x768       59.8  
   1024x768       85.0     75.0     70.1     60.0  
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1  
HDMI-1 disconnected (normal left inverted right x axis y axis)
TV disconnected (normal left inverted right x axis y axis)

```

this is my xorg.conf

```

Section "Monitor"
        Identifier      "Internal Monitor"
EndSection

Section "Screen"
        Identifier      "Internal Screen"
        Monitor         "Internal Monitor"
        Device          "Video Card (Primary)"
        SubSection "Display"
                Virtual         1900 1200
                Modes           "1900x1200" "1366x768" "1280x1024"
        EndSubSection
EndSection

Section "Device"
        Identifier      "Video Card (Primary)"
EndSection

```

Now I tried to add a new video mode with xrandr to the LVDS:

```

# gtf 1280 1024 60.0
  # 1280x1024 @ 60.00 Hz (GTF) hsync: 63.60 kHz; pclk: 108.88 MHz
  Modeline "1280x1024_60.00"  108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync
# xrandr --newmode "1280x1024_60.00"  108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync

```

which gives me an additional line in xrandr being

```
  1280x1024_60.00 (0xf0)  108.9MHz
        h: width  1280 start 1360 end 1496 total 1712 skew    0 clock   63.6KHz
        v: height 1024 start 1025 end 1028 total 1060           clock   60.0Hz

```

but when I try to add the mode to the LVDS, I get:

```
# xrandr --addmode LVDS 1280x1024_60.00
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  150 (RANDR)
  Minor opcode of failed request:  18 ()
  Serial number of failed request:  27
  Current serial number in output stream:  28

```
And I have NO idea what to do with this error. Can someone help me in the direction I have to work here? I am quite lost what to do.

---

### Post by tokyoahead on 2009-06-09
Sorry, I just realized that I can add it to the VGA and when I set it to VGA, it also uses it for the external screen.

So please ignore that post.I would have deleted it if I knew how.

---

### Post by wamukota on 2009-06-09
> **tokyoahead said:**
> So please ignore that post.I would have deleted it if I knew how.

Rename the subject of the first message to:
 [Solved] [ubuntu] external ....

That way readers know it

---

