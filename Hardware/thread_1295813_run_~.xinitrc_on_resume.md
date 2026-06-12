---
title: "run ~/.xinitrc on resume?"
date: 2009-10-19
forum: Hardware
---

### Post by bcw on 2009-10-19
Hello,

My tablet pc is misaligned on startup.  I captured the 'xsetwacom' lines to correct this in .xinitrc.

On boot-up, this file is accessed when I log in and the settings are put in place - the tablet alignment is correct.

Resuming from suspend or hibernate does not invoke this file.  How can I do this?  I have tried a script in /etc/pm/sleep.d, and the log shows this:
```
...
Tue Oct 20 16:06:22 NZDT 2009: Running hooks for resume
/etc/pm/sleep.d/calibrate-tablet resume suspend: Failed to open display ()
Failed to open display ()
Failed to open display ()
Failed to open display ()
Failed to open display ()
Failed to open display ()
Failed to open display ()
Failed to open display ()
Returned exit code 1.
/etc/pm/sleep.d/action_wpa resume suspend: success.
...
```

.xinitrc contains:
```
xsetwacom set eraser bottomy "24625"
xsetwacom set eraser bottomx "18425"
xsetwacom set eraser topy "85"
xsetwacom set eraser topx "45"
xsetwacom set stylus bottomy "24625"
xsetwacom set stylus bottomx "18425"
xsetwacom set stylus topy "85"
xsetwacom set stylus topx "45"
# run the primary system script
. /etc/X11/xinit/xinitrc
```

Fujitsu ST5112 tablet, with Xubuntu AMD64 Jaunty.

Thanks,
bcw

---

