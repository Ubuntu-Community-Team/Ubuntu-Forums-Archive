---
title: "AutoDetect External Monitor"
date: 2009-12-16
forum: Hardware
---

### Post by shekshek on 2009-12-16
Hey,

So I'm running ubuntu 9.10 on my acer laptop and I want to connect an external monitor to it...which I have done and everything works fine.
My question is...how would I automatically switch to the monitor's display as soon as it is plugged in. Right now I run this script:

```
#!/bin/bash
 
EXTERNAL_OUTPUT="VGA1"
INTERNAL_OUTPUT="LVDS1"
 
xrandr | grep $EXTERNAL_OUTPUT | grep " connected "

if [ $? -eq 0 ]; then

    xrandr | grep $EXTERNAL_OUTPUT | grep " connected 1"
    if [ $? -eq 0 ]; then	
        xrandr --output $INTERNAL_OUTPUT --auto --output $EXTERNAL_OUTPUT --off
    else
        xrandr --output $INTERNAL_OUTPUT --off --output $EXTERNAL_OUTPUT --auto
    fi
else
    xrandr --output $INTERNAL_OUTPUT --auto --output $EXTERNAL_OUTPUT --off
fi
```

So I connect the monitor and instead of going to the menu and stuff I just run this script and it toggles between the external monitor and my laptop.

But out of curiousity and even more laziness I'd like to do this automatically as soon as I plug in the monitor cable or take it out. Is there any way to run event driven scripts like that? I wouldn't want to do some kinda spin checking thing...like run a script every 5 seconds forever or something. I would like to detect the new monitor's presence (or absence) and only run a script at the time of change.
Is this even possible? Is such an event OS managed or completely hardware managed? Is the information even stored as an "event" or just as a "state?"

Thanx a lot.

---

