---
title: "Acer laptop and HDMI output"
date: 2015-04-24
forum: Hardware
---

### Post by ubuntubrian on 2015-04-24
I am trying to get HDMI output so I can show video or slides. The HDMI port is detected but turned off. I tried using Grandr to set multiple displays but I only have one choice, eDP. No other displays are listed. Here's the output from xrandr

```
~$ xrandr
Screen 0: minimum 320 x 200, current 1366 x 768, maximum 8192 x 8192
VGA-0 disconnected (normal left inverted right x axis y axis)
eDP connected primary 1366x768+0+0 (normal left inverted right x axis y axis) 344mm x 194mm
   1366x768       60.0*+
   1280x720       59.9  
   1152x768       59.8  
   1024x768       59.9  
   800x600        59.9  
   848x480        59.7  
   720x480        59.7  
   640x480        59.4  
HDMI-0 disconnected (normal left inverted right x axis y axis)

```

Any help is greatly appreciated.

Thanks!!

---

### Post by weatherman2 on 2015-04-24
Instead of trying xrandr, have you tried using the System Settings -> Displays to try to enable the HDMI display?  (Must be plugged in first.)  That assumes you are running Ubuntu Desktop edition...

---

### Post by ubuntubrian on 2015-04-24
> **weatherman2 said:**
> Instead of trying xrandr, have you tried using the System Settings -> Displays to try to enable the HDMI display?  (Must be plugged in first.)  That assumes you are running Ubuntu Desktop edition...

Thanks Weatherman2
I was able to get the HDMI display to show my wallpaper and then I was able to rearrange the displays in the "Displays" settings. At that point all my desktop icons showed up and a dialog asking if I wanted to keep the changes. My pointer was not working on the projected display but I hit enter. Nothing really happened except some flickering and a return to my desktop with icons in the projected display. The mouse pointer was no gone on my primary display so I couldn't reall see if slides or a video would show up but the terminal window I had open did not. So I'm making progress, sort of. More help is very welcome!

---

