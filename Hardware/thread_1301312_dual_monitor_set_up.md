---
title: "dual monitor set up"
date: 2009-10-25
forum: Hardware
---

### Post by rinrada on 2009-10-25
I have a eeePC1000HE and use a 24" LCD screen (Samsung P2450H) in the office.
The netbook screen works fine on its own. But as a dual display, my netbook screen is too small (800 x 600) and while the picture fills my large screen but has the wrong resolution.

GNOME Preferences>Display shows two screens of equal size. Attempts to change the resolution apparently do something in that I am asked to authenticate the changes, but when I restart I am back at square one.

Previously I was able to run both screens simply commenting out the subsection "Display" lines in my xorg.conf (as per an earlier thread). However, I updated my settings recently when trying to sort out a problem with the webcam. Now my webcame works fine but I cannot sort out my screens. My xorg.conf looks like this (after trying to implement the changes through GNOME).

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    SubSection "Display"
        Virtual    2944 1080
    EndSubSection
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Option        "UseFBDev"        "true"
EndSection

I realise this may be rather basic, I am new to LINUX, but I would greatly appreciate it if some one can coach me. Thanks.

---

### Post by rinrada on 2009-10-27
Not much response but managed to get somewhere myself

Using the information on [http://www.thinkwiki.org/wiki/Xorg_RandR_1.2](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2) 

I am able to set up my screens one above the other with:-
$ xrandr --output LVDS --mode 1024x600 --pos 0x1080 --output VGA --mode 1920x1080 --pos 0x0

Following the instructions on the page I edited an /etc/X11/Xsession.d/45custom_xrandr-settings file as follows:-
-file begin-
# If an external monitor is connected, place it with xrandr
 
# External output may be "VGA" or "VGA-0" or "DVI-0" or "TMDS-1"
EXTERNAL_OUTPUT="VGA"
INTERNAL_OUTPUT="LVDS"
# EXTERNAL_LOCATION may be one of: left, right, above, or below
EXTERNAL_LOCATION="above"
 
case "$EXTERNAL_LOCATION" in
       left|LEFT)
               EXTERNAL_LOCATION="--left-of $INTERNAL_OUTPUT"
               ;;
       right|RIGHT)
               EXTERNAL_LOCATION="--right-of $INTERNAL_OUTPUT"
               ;;
       top|TOP|above|ABOVE)
               EXTERNAL_LOCATION="--above $INTERNAL_OUTPUT"
               ;;
       bottom|BOTTOM|below|BELOW)
               EXTERNAL_LOCATION="--below $INTERNAL_OUTPUT"
               ;;
       *)
               EXTERNAL_LOCATION="--left-of $INTERNAL_OUTPUT"
               ;;
esac
 
xrandr |grep $EXTERNAL_OUTPUT | grep " connected "
if [ $? -eq 0 ]; then
    xrandr --output $INTERNAL_OUTPUT --mode 1024x600 --pos 0x1920 --output $EXTERNAL_OUTPUT --mode 1920x1080 --pos 0x0 $EXTERNAL_LOCATION
    # Alternative command in case of trouble:
    # (sleep 2; xrandr --output $INTERNAL_OUTPUT --auto --output $EXTERNAL_OUTPUT --auto $EXTERNAL_LOCATION) &
else
    xrandr --output $INTERNAL_OUTPUT --auto --output $EXTERNAL_OUTPUT --off
fi
-file end-

But is did not execute auotmatically when logging in.
How do I get it to execute automatically?

---

