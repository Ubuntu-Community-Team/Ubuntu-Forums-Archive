---
title: "ati drivers for karmic koala?"
date: 2009-11-19
forum: Hardware
---

### Post by proevofanatik on 2009-11-19
hi i have a radeon x1800 gto graphics card. are there any drivers for kubuntu 9.10 karmic? i want to be able to play games and watch movies thanks

---

### Post by Yellow Pasque on 2009-11-19
The drivers should work "out of the box" and allow you to do those things.

---

### Post by RedSingularity on 2009-11-19
Look in System>Admin>Hardware Drivers for a driver to activate.

---

### Post by Yellow Pasque on 2009-11-19
> **RedSingularity said:**
> Look in System>Admin>Hardware Drivers for a driver to activate.
No, the X1800 is too old for that.

---

### Post by Melcar on 2009-11-19
Proprietary drivers will not work with that card.  The open source drivers are loaded by default and should provide both 2D and 3D acceleration for that card. Gaming and movie watching should be more than possible; though for 3D you will be limited to OpenGL1.5, so some stuff will not work (many games with WINE, advance OpenGL2.x features like GLSL, etc.).

---

### Post by proevofanatik on 2009-11-20
i cant get my screens full resolution with is 1680x1050.

how do i get that resolution? im stuck with 1280x1024

---

### Post by realzippy on 2009-11-20
run **xrandr -q   **in terminal and post the output please...

---

### Post by proevofanatik on 2009-11-20
Screen 0: minimum 640 x 400, current 1280 x 1024, maximum 1280 x 1024
default connected 1280x1024+0+0 0mm x 0mm
   1280x1024       0.0*
   1152x864        0.0
   1024x768        0.0
   800x600         0.0
   640x480         0.0
   720x400         0.0

---

### Post by realzippy on 2009-11-20
So 1680x1050 does not exist.Sure your monitor can handle it?
If,create new modeline by typing

**cvt 1680 1050**

and post output (modeline only ;-))

---

### Post by proevofanatik on 2009-11-20
# 1680x1050 59.95 Hz (CVT 1.76MA) hsync: 65.29 kHz; pclk: 146.25 MHz
Modeline "1680x1050_60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync

yes m8 my monitor is a samsung pebble. i get 1680 x 1050 on xp

---

### Post by realzippy on 2009-11-20
Terminal:

**xrandr --newmode "1680x1050_60.00" 146.25 1680 1784 1960 2240 1050 1053 1059 1089 -hsync +vsync**

when done,go to displaysettings to check if it is now available.

---

### Post by proevofanatik on 2009-11-20
no m8 still the same i also tried rebooting

---

### Post by proevofanatik on 2009-11-20
do i have to edit the x11 file? sorry xorg.conf?

---

### Post by realzippy on 2009-11-20
To make it permanent,yes.But do you have one?

---

### Post by proevofanatik on 2009-11-20
where is it kept again. sorry im still quite new to linux.

---

### Post by realzippy on 2009-11-20
edit:

[B]xrandr --addmode 1680x1050_60.00
[/B]
or 

[B]xrandr --addmode default 1680x1050_60.00
[/B]

---

### Post by realzippy on 2009-11-20
> **proevofanatik said:**
> where is it kept again. sorry im still quite new to linux.

usually:

/etc/X11/xorg.conf

but in karmic there is none until you create it.But try above first..

---

### Post by proevofanatik on 2009-11-20
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

---

### Post by proevofanatik on 2009-11-20
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

---

### Post by proevofanatik on 2009-11-20
sorry i posted twice. i dont know what happened there.

---

### Post by realzippy on 2009-11-20
problem is that I cannot see your output name from xrandr -q
There is *default* instead of (so I expected) LVDS,DVI,or DVI-0.

I have to check this out.
Meanwhile,if no xorg.conf file,try to create one:

**sudo dpkg-reconfigure xserver-xorg**

I do not know if this still works under Karmic,so test it.

---

### Post by proevofanatik on 2009-11-20
it asked for a password. i put it in then nothing. it just went to next line on terminal

---

### Post by realzippy on 2009-11-20
> **proevofanatik said:**
> it asked for a password. i put it in then nothing. it just went to next line on terminal


Thats ok.Check if this command created a xorg.conf file ...(in /etc/X11/)

---

### Post by proevofanatik on 2009-11-20
yes it did heres what it says inside

Section "Module"
	Load	"dri"
	Load	"GLcore"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"vesa"
EndSection

---

### Post by proevofanatik on 2009-11-20
i forgot to say my refresh rate is 0.0 Hz

---

### Post by Melcar on 2009-11-20
That's all your xorg.conf has in it?  When I create one with *Xorg -configure* it writes pretty much every option available for my devices.  However, since that file is no longer needed you will be fine with just a few sections.
It's odd that is says **vesa**.  You should be using **radeon**, so change that entry.  You should be able to get rid of the other section, so just delete it (or comment the lines out by putting a # in front).  Save the file and reboot.  Now that you're using the correct driver you should be able to select additional resolutions for your monitor.

---

### Post by realzippy on 2009-11-20
You should get the free "ATI" (radeon) video driver to
work first.This xorg loads "vesa".Check if ati is installed:

**sudo apt-get install xserver-xorg-driver-ati**

then backup xorg.conf:

**sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup**

then open it:

[B]gksudo kate /etc/X11/xorg.conf
[/B]

change: driver "vesa" *to* "ati"

Restart (X)

Hope that it works.If not,alt+ctrl+F1:

sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf

Restart (X)

---

### Post by proevofanatik on 2009-11-20
> **Melcar said:**
> That's all your xorg.conf has in it?  When I create one with *Xorg -configure* it writes pretty much every option available for my devices.  However, since that file is no longer needed you will be fine with just a few sections.
It's odd that is says **vesa**.  You should be using **radeon**, so change that entry.  You should be able to get rid of the other section, so just delete it (or comment the lines out by putting a # in front).  Save the file and reboot.  Now that you're using the correct driver you should be able to select additional resolutions for your monitor.


that fixed it m8 thank you so much also thanks for your help zippy

---

