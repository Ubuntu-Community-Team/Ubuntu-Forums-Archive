---
title: "Dual Monitor Problems"
date: 2009-08-22
forum: Hardware
---

### Post by qedprigmosynois on 2009-08-22
HI,
So I am a complete "noob" of linux [I switched yesterday and I must admit I love it :) ]
I was trying to set up dual monitors with my toshiba satellite a105 s2051 laptop to my samsung syncmaster 151s monitor. I have a ATI graphics card.
I dont remember what I did but I did enter quite a few commands into the terminal.
What ended up happening was that my computer would only run ubuntu onto the samsung. I used sudo dpkg-reconfigure -phigh xserver-xorg and it worked fine. Although just for reference, my troubles started when I ran aticonfig --enable-monitor=crt1,crt1.
Then I installed the driver again and enabled it through system=>administration=>hardware devices to enable it, every time I start up, once again my computer will only run on the samsung monitor. I can always adjust it by going through ubuntu's safemode and then having it fix the x script, but then my ati driver gets disabled [which requires me to restart, aka this is a loop]
Anybody know what is going on?

---

### Post by robobart on 2009-08-24
I think I am having a very similar problem. 

Basically - at each boot I need to set up my monitors fresh - which I do through:

System => Prefs => Display

I don't know why it won't "stick"

---

### Post by mercules2178 on 2009-08-24
Are you using the drivers for video chip?
I am using nvidia and I had the same problem. You as the user do not have permissions to save the info. I had to add my second monitor in the "screen section". I have one flat screen as analog and the other as dvi. 

code:

sudo pico /etc/X11/xorg.conf

This is what mine looks like:

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "CRT: 1280x1024 +1280+0, DFP: 1280x1024 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection

---

### Post by robobart on 2009-08-24
Ok - it sounds like you are doing the same thing I am - I am using vga for one monitor and dvi for the other.

Unfortunately I do not really understand the xorg.conf file. Here is what my current file looks like:

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        SubSection "Display"
                Virtual 2560 1024
        EndSubSection
EndSection

Section "Device"
        Identifier      "Configured Video Device"
EndSection


Tips on how I should modify this to make it work? 

Also I should point out that I am using a laptop - which I would like to work normally when I don't have it docked.

Thanks!

---

### Post by robobart on 2009-08-27
Got it working!

[http://www.thinkwiki.org/wiki/Xorg_RandR_1.2](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2)

helped quite a bit:

Dual Displays in Ubuntu 9.04, Dell E4300 Laptop - docked
(Intel driver)


1) Modify the Screen section of /etc/X11/xorg.conf to include the
lines:

        SubSection "Display"
                Virtual 2560 1024
        EndSubSection

My complete Screen section looks like:

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        SubSection "Display"
                Virtual 2560 1024
        EndSubSection
EndSection

2) Added the following file: /etc/X11/Xsession.d/85custom_xrandr-settings 
 
-- begin file --
# If an external monitor is connected, place it with xrandr
# Use xrandr -q to determine choices for outputs
DEFAULT_OUTPUT="LVDS"
MAIN_OUTPUT="HDMI-1"
AUX_OUTPUT="VGA"
# AUX_LOCATION may be one of: left, right, above, or below
AUX_LOCATION="right"
 
case "$AUX_LOCATION" in
       left|LEFT)
               AUX_LOCATION="--left-of $MAIN_OUTPUT"
               ;;
       right|RIGHT)
               AUX_LOCATION="--right-of $MAIN_OUTPUT"
               ;;
       top|TOP|above|ABOVE)
               AUX_LOCATION="--above $MAIN_OUTPUT"
               ;;
       bottom|BOTTOM|below|BELOW)
               AUX_LOCATION="--below $MAIN_OUTPUT"
               ;;
       *)
               AUX_LOCATION="--left-of $MAIN_OUTPUT"
               ;;
esac
 
xrandr |grep $MAIN_OUTPUT | grep " connected "
if [ $? -eq 0 ]; then
    xrandr --output $DEFAULT_OUTPUT --off --output $MAIN_OUTPUT --auto --output $AUX_OUTPUT --auto $AUX_LOCATION
else
    xrandr --output $DEFAULT_OUTPUT --auto --output $MAIN_OUTPUT --off --output $AUX_OUTPUT --off
fi
-- end file --

3) Now for the voodoo, under

System => Startup Applications

I added the command:

xrandr --output VGA --auto --right-of HDMI-1


reboot and it works!

---

### Post by joebrueske on 2009-09-21
I've been working with my Toshiba's ATI Mobility X600 VGA out for a while as the LCD screen is on the fritz. However, I've recently noticed that the LCD image is rather pixelated as if there's an aliasing problem. Everything is a little more pixely. I noticed this today when I turned the LCD back on as I use the CRT as my primary display.

I had NO issue with Gnome or xrandr recognizing BOTH monitors and I had no problems with being able to setup the dual display. Please note that the picture on the CRT is perfect. As soon as dual monitor is setup, the displays reset, and the LCD becomes pixely. To get it back to normal a new or backup conf file must be used. My guess is this has something to do with the virtual display.

Any thoughts?

```
Section "Monitor"
	Identifier	"Configured Monitor"
	Gamma		1.8
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	1440 1668
	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"		"true"
EndSection
```

---

