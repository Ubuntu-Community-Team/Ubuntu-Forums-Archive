---
title: "ATi Rage Mobility M4 on Gateway solo9500 Laptop"
date: 2006-12-20
forum: Hardware &amp; Laptops
---

### Post by sque on 2006-12-20
Hi!

I am having an old laptop, a Gateway Solo 9500 with [http://support.gateway.com/s/Mobile/Solo_Series/P9500/P950002.shtml]("these") specifications. 

I install Edgy and my problem is the screen resolution is 800x600.
My video card is ATi Rage M4 Mobility. By default, xorg was setted up with "ati" driver
```
Section "Device"
        Identifier      "ATI Technologies, Inc. Rage Mobility M4 AGP"
        Driver          "ati"
        BusID           "PCI:1:0:0"
        Option "DRI" "true"
End Section

```
Is this the right driver? How can I fix the resolution?? ](*,) The display supports at least 1024x768 and even maybe 1280x1024.

---

### Post by drg on 2006-12-27
How coincidental that we'd both be installing ubuntu on the same, old laptop within a week of each other?  Unfortunately, I installed Dapper instead of Edgy.

However, changing Driver to "vesa" worked for me.  If it doesn't work for you, try also commenting out "Option" "DRI" "true" line.  By "comment out", I mean placing a '#' at the beginning of the line.

That's not a perfect solution; as far as I know, the vesa driver does not support acceleration in either 2d or 3d.   If I find a more suitable configuration that uses the hardware to better advantage, I'll post it here. 

For onlookers, the laptop I have has an ATI Rage Mobility M4 AGP, and the screen supports 1280x1024 resolution (which was all set up correctly during install).  However, the 'ati' driver caused odd segmentation of the screen in X.  Suggestions appreciated.

-drg

---

### Post by drg on 2006-12-28
I cheated a little and used a Mepis LiveCD to get a working xorg.conf.  But I'm pleased to report that this works, including 3d acceleration:

```

Section "ServerLayout"
  Identifier "DefaultLayout"
  Screen 0 "Screen0" 0 0
  InputDevice "Keyboard0" "CoreKeyboard"
  InputDevice "USB Mouse" "CorePointer"
EndSection

Section "ServerFlags"
  Option "AllowMouseOpenFail" "true"
EndSection

Section "Files"
# Xorg 7.0 font paths
    FontPath 	"/usr/share/X11/fonts/misc:unscaled"
    FontPath 	"/usr/share/X11/fonts/cyrillic"
    FontPath 	"/usr/share/X11/fonts/Type1"
    FontPath 	"/usr/share/X11/fonts/util"

# Legacy font paths
    FontPath 	"/usr/X11R6/lib/X11/fonts/misc:unscaled"
    FontPath 	"/usr/X11R6/lib/X11/fonts/cyrillic"
    FontPath 	"/usr/X11R6/lib/X11/fonts/Type1"
    FontPath 	"/usr/X11R6/lib/X11/fonts/util"

# Other font paths
    FontPath 	"/usr/share/fonts/truetype/ttf-lucida"
    FontPath 	"/usr/share/fonts/truetype/arphic"
    FontPath 	"/usr/share/fonts/truetype/freefont"
    FontPath 	"/usr/share/fonts/truetype/kochi"
    FontPath 	"/usr/share/fonts/truetype/latex-xft-fonts"
    FontPath 	"/usr/share/fonts/truetype/openoffice"
    FontPath 	"/usr/share/fonts/truetype/ttf-bitstream-vera"
    FontPath 	"/usr/share/fonts/type1/gsfonts"
    FontPath 	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath 	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"

EndSection

Section "Module"
  Load "GLcore"
  Load "bitmap"
  Load "dbe"
  Load "ddc"
  Load "dri"
  Load "extmod"
  Load "freetype"
  Load "glx"
  Load "int10"
  Load "record"
  Load "type1"
  Load "v4l"
  Load "vbe"
EndSection

Section "InputDevice"
  Identifier "Keyboard0"
  Driver "keyboard"
  Option "CoreKeyboard"
  Option "XkbModel" "pc105"
  Option "XkbLayout" "us"
  Option "XKbOptions" ""
EndSection

Section "InputDevice"
  Identifier "USB Mouse"
  Driver "mouse"
  Option "Device" "/dev/input/mice"
  Option "Protocol" "ExplorerPS/2"
  Option "ZAxisMapping" "4 5"
  Option "Buttons" "5"
EndSection

Section "Monitor"
  Identifier "Monitor0"
  VendorName "unknown"
  ModelName "unknown"
 #Option "DPMS" "true"
  HorizSync    30.0 - 75.0 # Warning: This may fry old Monitors
  VertRefresh  50.0 - 70.0 # Very conservative. May flicker.
  Modeline "640x480"     25.175 640  664  760  800   480  491  493  525 #60Hz
  Modeline "800x600"     40.12  800  848  968 1056   600  601  605  628 #60Hz
  Modeline "1024x768"    75    1024 1048 1184 1328   768  771  777  806 -hsync -vsync
  Modeline "1024x768"    85    1024 1056 1152 1360   768  784  787  823
  ModeLine "1152x864"    65    1152 1168 1384 1480   864  865  875  985 Interlace
  Modeline "1152x864"    92    1152 1208 1368 1474   864  865  875  895
  Modeline "1152x864"   110    1152 1240 1324 1552   864  864  876  908
  Modeline "1152x864"   135    1152 1464 1592 1776   864  864  876  908
  Modeline "1152x864"   137.65 1152 1184 1312 1536   864  866  885  902 -HSync -VSync
  Modeline "1280x1024"   80    1280 1296 1512 1568  1024 1025 1037 1165 Interlace
  Modeline "1280x1024"  110    1280 1328 1512 1712  1024 1025 1028 1054
  Modeline "1280x1024"  126.5  1280 1312 1472 1696  1024 1032 1040 1068 -HSync -VSync
  Modeline "1280x1024"  135    1280 1312 1456 1712  1024 1027 1030 1064
  Modeline "1280x1024"  135    1280 1312 1416 1664  1024 1027 1030 1064
  Modeline "1280x1024"  157.5  1280 1344 1504 1728  1024 1025 1028 1072 +HSync +VSync
  Modeline "1280x1024"  181.75 1280 1312 1440 1696  1024 1031 1046 1072 -HSync -VSync
EndSection

Section "Device"
  Identifier  "Card0"
  Driver "ati"
  BoardName "unknown"
EndSection

Section "Screen"
  Identifier "Screen0"
  Device "Card0"
  Monitor "Monitor0"
  DefaultColorDepth 24
  
  SubSection "Display"
    Depth 8
    Modes "1280x1024" "1024x768" "800x600" "640x480"
  EndSubSection

  SubSection "Display"
    Depth 16
    Modes "1280x1024" "1024x768" "800x600" "640x480"
  EndSubSection
  
  SubSection "Display"
    Depth 24
    Modes "1280x1024" "1024x768" "800x600" "640x480"
  EndSubSection
EndSection

Section "DRI"
  Mode 0666
EndSection


```

---

### Post by JohnBoy55 on 2007-01-21
[http://ubuntuforums.org/images/smilies/eusa_wall.gif](http://ubuntuforums.org/images/smilies/eusa_wall.gif) I read your post about 2 weeks ago. I'm in the same situation, got a gateway 9500 laptop I picked up at auction. Installed Edgy and got a split, ghost-like display upon boot-up. After MUCH experimentation, including setting the driver to vesa, I'm finally down to installing 'Dapper'. It's an older distro, but at least the vesa driver gives a decent image. For some reason, the vesa driver gave a decent image in 'Edgy', but when I scrolled up or down, it was so SLOW you could actually watch it re-write the screen. The vesa driver does not do that in 'Dapper'. Aren't they the same driver? In addition, the only resolution that worked under the vesa driver was the 1024X768. That's livable, but at my age, the old eyeballs aren't going to get any better.

As it stands, I'll run 'Dapper' and hope and pray that the issue is fixed in 'Feisty'. I've tried at least 20 (yes, 20) different linux distro installations and frankly, I'm tired. 'Dapper' is older, but at least it works.

---

### Post by hsteckylf on 2007-02-13
JohnBoy55, what exactly would I need to do to use the vesa driver. I have a friend who is having this same problem with the default install of Ubuntu Edgy on a gateway laptop and I have never had to play with any of the graphics drivers on my own. I can help him use Dapper instead once I know how to help him use the vesa driver. thanks!

---

### Post by jquigley2 on 2007-11-21
I have the same problem as well split screen and it makes it near impossible to read. How can I change from ATI since it is no longer supported by AMD/ATI to the vesa driver. I have used the 7.10 Live CD to do my install, it didn't ask for any information it just ran and now I can't read my screen. :frown:
Thank you for any help.

---

