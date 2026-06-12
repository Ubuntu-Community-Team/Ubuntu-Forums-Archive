---
title: "Setting up a Toshiba Tecra M4"
date: 2011-08-18
forum: Hardware
---

### Post by robertahilljr on 2011-08-18
Hi everyone,

Could someone please help me with setting up my Toshiba Tecra M4, The pen works on the screen right from live cd, but only works for left click except in xournal, in which the eraser works. When I open grandr, I can rotate the screen, but the pen doesnt rotate at all, and also auto rotation doesnt work. Now I've heard people getting it all working, but I'm struggling to put all that I find online together to get it all working, so was wondering if anyone on here has had any luck with it and could I have some help with it please, I'm not a complete newbie with ubuntu and linux, but somethings I'm still a little slow at grasping on my own, hope I can get some help.

Kind regards,

Rob

*edit* P.S. I am running Ubuntu 10.04.

---

### Post by Nachtholm on 2012-04-03
The trick is in writing a script which will rotate the display with xrandr as well as the wacom input with xsetwacom.

copy the following into gedit and save them as "rotate[insert direction].sh"

down
```

#!/bin/sh

xrandr -o inverted
xsetwacom set "Serial Wacom Tablet stylus" rotate half
xsetwacom set "Serial Wacom Tablet eraser" rotate half
;;
esac

```

up
```

#!/bin/sh

xrandr -o normal
xsetwacom set "Serial Wacom Tablet stylus" rotate none
xsetwacom set "Serial Wacom Tablet eraser" rotate none
;;
esac

```

left
```

#!/bin/sh

    # rotate to the left
    xrandr -o left
    xsetwacom set "Serial Wacom Tablet stylus" rotate cw
    xsetwacom set "Serial Wacom Tablet eraser" rotate cw
    ;;
esac

```

right
```

#!/bin/sh
    #rotate to the right
    xrandr -o right
    xsetwacom set "Serial Wacom Tablet stylus" rotate ccw
    xsetwacom set "Serial Wacom Tablet eraser" rotate ccw
    ;;
esac

```

Then use the keyboard settings window to bind these scripts to the little stick via application shortcuts.

If all works well, you will have a Tecra that rotates both screen and wacom input simultenaously at the push of a button!

---

### Post by robertahilljr on 2012-04-08
Hi Nachtholm, 

Thanks for the reply, Ive not set up key shortcuts yet as now using KDE and still learning my way round it but got shortcuts to the scripts on my desktop and works a treats, so thank you!

Do you mind if I write a document somewhere on how to set up touchscreen on the Tecra M4 using your scripts?

Rob

---

