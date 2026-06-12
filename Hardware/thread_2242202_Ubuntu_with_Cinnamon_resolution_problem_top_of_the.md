---
title: "Ubuntu with Cinnamon resolution problem top of the screen cut off"
date: 2014-08-31
forum: Hardware
---

### Post by dangerfirebob on 2014-08-31
Lenovo Thinkpad edge 15 with a new 250 GB ssd and a dual boot of Ubuntu-Studio and Windows 7.

With Ubuntu-Studio 14.04 installed the resolution works perfectly (using the xfce desktop) but Supertuxkart in fullscreen doesn't stretch to fill the screen leaving large black areas on both sides, other games have difficulties with fullscreen too maybe because this laptop has such a wide screen. As I have installed the Ubuntu dual boot for a friend who normally uses Windows 7 I have chosen Cinnamon as a good transitional desktop for her to use but for some reason the top of the screen has been cut of by half an inch, thus the menu selection loses its first entry. Not good.

 I have been using xrandr as indicated here: [http://ubuntuforums.org/showthread.php?t=1490464&p=9418202#post9418202 ]("http://ubuntuforums.org/showthread.php?t=1490464&p=9418202#post9418202")to change the vertical resolution but it just moves the screen upwards leaving a black bar underneath my menu bar making the situation worse. Here is the xrandr output:

Screen 0: minimum 320 x 200, current 1360 x 768, maximum 32767 x 32767
LVDS1 connected primary 1360x768+0+0 (normal left inverted right x axis y axis) 344mm x 193mm
   1366x768       60.0 +   50.0  
   1360x768       59.8*    60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
   1360x720_59.90   59.9  
   "1360x768_60.00"   59.8  
   "1360x700_60.00"   60.0  
VGA1 disconnected (normal left inverted right x axis y axis)
   1360x720_59.90   59.9  
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)
VIRTUAL1 disconnected (normal left inverted right x axis y axis)
  1920x1200_60.00 (0x11a)  193.2MHz
        h: width  1920 start 2056 end 2256 total 2592 skew    0 clock   74.6KHz
        v: height 1200 start 1203 end 1209 total 1245           clock   59.9Hz

What to do next? Any ideas would be great,  Thank you in advance.:guitar:

---

