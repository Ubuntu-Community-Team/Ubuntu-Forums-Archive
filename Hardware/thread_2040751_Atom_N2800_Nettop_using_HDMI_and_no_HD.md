---
title: "Atom N2800 Nettop using HDMI and no HD"
date: 2012-08-11
forum: Hardware
---

### Post by matthewh3 on 2012-08-11
Hi I've just got Atom N2800 Nettop and installed Xubuntu.  I'm using the HDMI lead on my 32" 1080P HDTV and the best resolution I can get is 1024x768.  Why can't I get the native HDTV resolution of 1900x1080:confused:

---

### Post by cwsnyder on 2012-08-11
Your HDTV is probably not supplying a good EDID to your Nettop.  You can add the resolution you wish by using xrandr, xorg.conf, or a custom EDID (in order of complexity).

---

### Post by matthewh3 on 2012-08-11
> **cwsnyder said:**
> Your HDTV is probably not supplying a good EDID to your Nettop.  You can add the resolution you wish by using xrandr, xorg.conf, or a custom EDID (in order of complexity).

The TV has done 1900x1080 for other PC's fine once I've added Nvidia or ATI drivers.  I've tried using "Resolution Switcher" and "ARandR" from the software centre to no avail.  Can you help me change the resolution to 1900x1080 if possible?

---

### Post by cwsnyder on 2012-08-11
A good guide is [http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html](http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html)

First run xrandr by itself and find out what your system name for your monitor is.  This is found at the beginning of the second line displayed following the command entry. This is <displayname>.

Second, run cvt 1900 1080
Sample output:
# 1904x1080 59.93 Hz (CVT) hsync: 67.12 kHz; pclk: 170.75 MHz
Modeline "1904x1080_60.00"  170.75  1904 2024 2224 2544  1080 1083 1093 1120 -hsync +vsync

Third, enter ```
xrandr --newmode "1904x1080" 170.75  1904 2024 2224 2544  1080 1083 1093 1120 -hsync +vsync
xrandr --addmode <displayname> 1904x1080
xrandr --output <displayname> --mode 1904x1080
```If this works, go on and follow the guide to add it to your system permanently.

---

### Post by matthewh3 on 2012-08-11
> **cwsnyder said:**
> A good guide is [http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html](http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html)

First run xrandr by itself and find out what your system name for your monitor is.  This is found at the beginning of the second line displayed following the command entry. This is <displayname>.

Second, run cvt 1900 1080
Sample output:
# 1904x1080 59.93 Hz (CVT) hsync: 67.12 kHz; pclk: 170.75 MHz
Modeline "1904x1080_60.00"  170.75  1904 2024 2224 2544  1080 1083 1093 1120 -hsync +vsync

Third, enter ```
xrandr --newmode "1904x1080" 170.75  1904 2024 2224 2544  1080 1083 1093 1120 -hsync +vsync
xrandr --addmode <displayname> 1904x1080
xrandr --output <displayname> --mode 1904x1080
```If this works, go on and follow the guide to add it to your system permanently.


I entered -


*xrandr --newmode "1904x1080" 170.75  1904 2024 2224 2544  1080 1083 1093 1120 -hsync +vsync*


and got 


*xrandr: Failed to get size of gamma for output default*


Is that OK and when I entered 


[I]$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm[/I]


So is my screen name 


*Screen 0*


Thanks.

---

### Post by cwsnyder on 2012-08-11
You may need quotes around 'Screen 0' because of the space in the name.

My monitor always gets the 'no gamma' error also.  This means that the EDID is probably not valid from your display.

---

### Post by matthewh3 on 2012-08-11
Just entered the following and nothing happened 

[I]$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768        0.0* 
   800x600         0.0  
   640x480         0.0  
  1904x1080 (0x2c8)  170.8MHz
        h: width  1904 start 2024 end 2224 total 2544 skew    0 clock   67.1KHz
        v: height 1080 start 1083 end 1093 total 1120           clock   59.9Hz
matt@matt-desktop:~/cpuminer$ xrandr --newmode "1904x1080" 170.75  1904 2024 2224 2544  1080 1083 1093 1120 -hsync +vsync
xrandr: Failed to get size of gamma for output default
X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  149 (RANDR)
  Minor opcode of failed request:  16 (RRCreateMode)
  Serial number of failed request:  19
  Current serial number in output stream:  19
matt@matt-desktop:~/cpuminer$ xrandr --addmode Screen 0 1904x1080
usage: xrandr [options]
  where options are:
  -display <display> or -d <display>
  -help
  -o <normal,inverted,left,right,0,1,2,3>
            or --orientation <normal,inverted,left,right,0,1,2,3>
  -q        or --query
  -s <size>/<width>x<height> or --size <size>/<width>x<height>
  -r <rate> or --rate <rate> or --refresh <rate>
  -v        or --version
  -x        (reflect in x)
  -y        (reflect in y)
  --screen <screen>
  --verbose
  --current
  --dryrun
  --nograb
  --prop or --properties
  --fb <width>x<height>
  --fbmm <width>x<height>
  --dpi <dpi>/<output>
  --output <output>
      --auto
      --mode <mode>
      --preferred
      --pos <x>x<y>
      --rate <rate> or --refresh <rate>
      --reflect normal,x,y,xy
      --rotate normal,inverted,left,right
      --left-of <output>
      --right-of <output>
      --above <output>
      --below <output>
      --same-as <output>
      --set <property> <value>
      --scale <x>x<y>
      --transform <a>,<b>,<c>,<d>,<e>,<f>,<g>,<h>,<i>
      --off
      --crtc <crtc>
      --panning <w>x<h>[+<x>+<y>[/<track:w>x<h>+<x>+<y>[/<border:l>/<t>/<r>/<b>]]]
      --gamma <r>:<g>:<b>
      --primary
  --noprimary
  --newmode <name> <clock MHz>
            <hdisp> <hsync-start> <hsync-end> <htotal>
            <vdisp> <vsync-start> <vsync-end> <vtotal>
            [+HSync] [-HSync] [+VSync] [-VSync]
  --rmmode <name>
  --addmode <output> <name>
  --delmode <output> <name>
matt@matt-desktop:~/cpuminer$ xrandr --output Screen 0 --mode 1904x1080
usage: xrandr [options]
  where options are:
  -display <display> or -d <display>
  -help
  -o <normal,inverted,left,right,0,1,2,3>
            or --orientation <normal,inverted,left,right,0,1,2,3>
  -q        or --query
  -s <size>/<width>x<height> or --size <size>/<width>x<height>
  -r <rate> or --rate <rate> or --refresh <rate>
  -v        or --version
  -x        (reflect in x)
  -y        (reflect in y)
  --screen <screen>
  --verbose
  --current
  --dryrun
  --nograb
  --prop or --properties
  --fb <width>x<height>
  --fbmm <width>x<height>
  --dpi <dpi>/<output>
  --output <output>
      --auto
      --mode <mode>
      --preferred
      --pos <x>x<y>
      --rate <rate> or --refresh <rate>
      --reflect normal,x,y,xy
      --rotate normal,inverted,left,right
      --left-of <output>
      --right-of <output>
      --above <output>
      --below <output>
      --same-as <output>
      --set <property> <value>
      --scale <x>x<y>
      --transform <a>,<b>,<c>,<d>,<e>,<f>,<g>,<h>,<i>
      --off
      --crtc <crtc>
      --panning <w>x<h>[+<x>+<y>[/<track:w>x<h>+<x>+<y>[/<border:l>/<t>/<r>/<b>]]]
      --gamma <r>:<g>:<b>
      --primary
  --noprimary
  --newmode <name> <clock MHz>
            <hdisp> <hsync-start> <hsync-end> <htotal>
            <vdisp> <vsync-start> <vsync-end> <vtotal>
            [+HSync] [-HSync] [+VSync] [-VSync]
  --rmmode <name>
  --addmode <output> <name>
  --delmode <output> <name>[/I]

When I used *"Screen 0"* or *'Screen 0'* It said *xrandr: cannot find output "Screen 0"*

---

### Post by matthewh3 on 2012-08-11
Although whent I enter this 

[I]$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768        0.0* 
   800x600         0.0  
   640x480         0.0  
  **1904x1080** (0x2c8 )  170.8MHz
        h: width  1904 start 2024 end 2224 total 2544 skew    0 clock   67.1KHz
        v: height 1080 start 1083 end 1093 total 1120           clock[/I]

But the resolution hasn't changed and 1080 is not in any settings?

---

### Post by matthewh3 on 2012-08-11
I tried changing *Screen 0* to *default* and got 

[I]$ xrandr --addmode default 1904x1080
xrandr: Failed to get size of gamma for output default
matt@matt-desktop:~/cpuminer$ xrandr --output default --mode 1904x1080
xrandr: Failed to get size of gamma for output default
xrandr: Configure crtc 0 failed[/I]

---

### Post by matthewh3 on 2012-08-11
> **matthewh3 said:**
> Although whent I enter this 

[I]$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768        0.0* 
   800x600         0.0  
   640x480         0.0  
  **1904x1080** (0x2c8 )  170.8MHz
        h: width  1904 start 2024 end 2224 total 2544 skew    0 clock   67.1KHz
        v: height 1080 start 1083 end 1093 total 1120           clock[/I]

But the resolution hasn't changed and 1080 is not in any settings?

Tried

[I]$ xrandr -s 1904x1080
Failed to change the screen configuration![/I]

---

### Post by matthewh3 on 2012-08-11
Now I get 

[I]xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 1024 x 768, maximum 1904 x 1080
default connected 1024x768+0+0 0mm x 0mm
   1024x768        0.0* 
   800x600         0.0  
   640x480         0.0  
   1904x1080      59.9[/I]


[I]$ xrandr -s 1904x1080
Failed to change the screen configuration!
matt@matt-desktop:~/cpuminer$ xrandr -s 1904x1080_59.9
Failed to change the screen configuration![/I]

---

### Post by matthewh3 on 2012-08-11
> **matthewh3 said:**
> Now I get 

[I]xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 1024 x 768, maximum 1904 x 1080
default connected 1024x768+0+0 0mm x 0mm
   1024x768        0.0* 
   800x600         0.0  
   640x480         0.0  
   1904x1080      59.9[/I]


[I]$ xrandr -s 1904x1080
Failed to change the screen configuration!
matt@matt-desktop:~/cpuminer$ xrandr -s 1904x1080_59.9
Failed to change the screen configuration![/I]


And 1904x1080 is in Xubuntu default screen settings but selecting the value doesn't change the resolution:confused:

---

