---
title: "problem on tablet pc screen rotation"
date: 2008-10-30
forum: Hardware
---

### Post by viru on 2008-10-30
I have a hp 2710p tablet and finally got the tablet pen working.
However the it does not rotate to tablet mode when I flip the screen over, so I was thinking about add a button in the pannel that can swtich screen rotation and stylus rotation at one time.

I come out with following code.

```
orientation=`xsetwacom get stylus rotate`
if [ "$orientation" = "0" ]; then
    /usr/bin/X11/xrandr --orientation right
    xsetwacom set stylus rotate CW
else
    /usr/bin/X11/xrandr --orientation normal
    xsetwacom set stylus rotate
fi
```

everything works perfectly when i run this under termial, but after I put it on the panel, problem occurs.

if I click the button for about two times (eg switch to normal and then switch back to clock-wise rotation), everything will crash. the system will kick me back to the login screen after a few seconds.

anybody please help me. everything is ok if i run it in terminal, no matter how many times.

---

### Post by royalCS on 2008-11-30
same for me...

but: it seems to work with the desktop effects disabled.

Now I would really like to have the xrandr screen rotation and compiz at the same time.

---

