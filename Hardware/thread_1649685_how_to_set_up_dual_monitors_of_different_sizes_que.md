---
title: "how to set up dual monitors of different sizes question?"
date: 2010-12-20
forum: Hardware
---

### Post by jungleexplorer on 2010-12-20
I just bought a new 55" LCD TV. I have my laptop connected to it so I can watch internet content.  My problem is that Ubuntu will not let me set the screen resolution for the TV to the correct wide screen resolution.  I can boot my laptop up with XP and it allows me to set the resolution to 1280 X 720, which is the perfect resolution for my TV since I am sitting quite a distance from the unit. So I know my video card can handle the right resolution.  But Ubuntu will only allow me to set the screen resolution to 1024 X 768.  Is there anything I can do about this?  I was running Hardy 8.04 but I upgraded to the latest (10.10 lts) today. I was hoping it would have better support for dual displays or display cloning, but it is pretty much the same.

Thanks for the help.

---

### Post by IcarusR on 2010-12-20
You can use xrandr to setup the resolution you want. Then it is possible to create a script to check if TV is connected & if so set it to the new resolution.

Info on how to use xrandr here

[http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html]("http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html") 

This is a script, run at login, I use to set my external screen to a resolution ubuntu refuses to set as default.

```
#!/bin/bash
EXTERNAL_OUTPUT="VGA1"
INTERNAL_OUTPUT="LVDS1"

xrandr --newmode  "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync # this sets new resolution mode line
xrandr --addmode VGA1 "1280x1024_60.00" # sets new mode to ext moniter

xrandr |grep $EXTERNAL_OUTPUT | grep " connected " # checks to see if ext moniter is connected
if [ $? -eq 0 ]; then
    xrandr --output $INTERNAL_OUTPUT --off --output $EXTERNAL_OUTPUT --mode 1280x1024_60.00 # if ext moniter is connected switches internal screen off
else
    xrandr --output $INTERNAL_OUTPUT --auto --output $EXTERNAL_OUTPUT --off # if ext moniter not connected switches internal screen to auto
fi
```

---

