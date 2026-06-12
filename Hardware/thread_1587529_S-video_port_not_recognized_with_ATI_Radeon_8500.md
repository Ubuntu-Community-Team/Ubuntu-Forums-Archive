---
title: "S-video port not recognized with ATI Radeon 8500"
date: 2010-10-03
forum: Hardware
---

### Post by chiron80 on 2010-10-03
I just did a clean install of Mythbuntu Maverick RC on a computer with an ATI Radeon 8500 video card with a VGA, DVI and S-video port. According to all the sources I can find, TV-out should be supported on that card (R200). No matter what I can do, I can't get the drivers to detect/show the S-video port.

The card (identified by lspci) is:

```
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon R200 QL [Radeon 8500 LE]
```

When I type "xrandr", the output does not show "S-video".

```
$ xrandr
Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 4096 x 4096
VGA-0 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 376mm x 301mm
   1280x1024      60.0*+   75.0  
   1152x864       75.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1  
DVI-0 disconnected (normal left inverted right x axis y axis)
$
```

Initially my xorg.conf was nonexistent, but I've attempted modifying it to be the following:

```
Section "Screen"
        Identifier      "Default Screen"
        DefaultDepth    24
EndSection

Section "Device"
        Identifier      "Default Device"
        Driver  "radeon"
        Option  "ATOMTvOut" "true
        Option  "TVDACLoadDetect" "true"
        Option  "TVStandard" "ntsc"
#       Option  "monitor-S-video" "TV-monitor"
        Option  "ForceTVOut" "true"
EndSection
```

However, that had no effect in the output of xrandr. The Xorg.0.conf shows:

```
[  1334.935] (WW) RADEON(0): Option "ATOMTvOut" is not used
[  1334.935] (WW) RADEON(0): Option "TVDACLoadDetect" is not used
[  1334.935] (WW) RADEON(0): Option "ForceTVOut" is not used
```

I can't think what to try next (short of finding another video card). Does anybody have any suggestions?

- Ben

References:
[http://www.x.org/wiki/radeonTV](http://www.x.org/wiki/radeonTV)
[http://wiki.archlinux.org/index.php/ATI#TV_out](http://wiki.archlinux.org/index.php/ATI#TV_out)

man radeon says:
```
TV-out support (only on R/RV/RS1xx, R/RV/RS2xx, R/RV/RS3xx. Experimental support on R/RV5xx, R/RV6xx, and R/RV7xx through the ATOMTvOut option);
```

---

### Post by chiron80 on 2010-10-18
For those that may find this post in the future:

I posted this same question to the forums over at Phoronix, and I was informed that S-video out is not supported on this particular card. It seems that s-video out is not supported on any R100 or R200 cards that use a separate (rather than integrated) TV-out chip. You can read more details there:

[http://www.phoronix.com/forums/showthread.php?t=26267](http://www.phoronix.com/forums/showthread.php?t=26267)

---

### Post by iconoclast hero on 2011-09-05
I assume in the nearly one year since the original post nothing new on this has developed?  From the link you posted it appears that it is possible to port the code but it hadn't been done at that point...  Any luck getting it done?

---

### Post by chiron80 on 2011-09-06
> **iconoclast hero said:**
> I assume in the nearly one year since the original post nothing new on this has developed?  From the link you posted it appears that it is possible to port the code but it hadn't been done at that point...  Any luck getting it done?

I got a different (nVidia) card from a friend, and haven't looked into the matter since. If I recall correctly, someone in the linked post said they updated the documentation to make it clear that TV-Out on this card wasn't supported. I would be very surprised if the situation has changed since, but I don't know myself.

---

