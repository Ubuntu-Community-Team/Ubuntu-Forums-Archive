---
title: "disable touchpad permanently"
date: 2015-06-18
forum: Hardware
---

### Post by V Boti on 2015-06-18
I have a touchpad problem on my laptop, if the touch pad is on, sometimes the mouse start moving randomly on the screen and clicking randomly, this is not an Ubuntu problem, because this is happening on windows to, so it must be a hardware problem, that`s why I have to disable the touchpad, I have created a launcher button with this script:  xinput set-prop 15 "Device Enabled" 0, and its` working, partially. the problem is that after a short time: 10 - 20 minutes the the touchpad re-enables by himself, so every time I have to re-disable the touchpad. There is a way to permanently disable the touchpad? 
Thank you.

---

### Post by dino99 on 2015-06-18
a touchpad works by 'sensitivity' and 'pressure'; so everything disturbing these 'electrical' contact features can cause the trouble you get. To get a better experience the 'touchpad' needs to be often cleaned.
i suppose the bios can deal with that hardware: activating/deactivating/touchpad settings

---

### Post by sudodus on 2015-06-18
You can also disable the touchpad temporarity with a command line

```
synclient touchpadoff=1
```

and to re-activate it

```
synclient touchpadoff=0
```

See more in ```
man synaptics
```

```
       Option "TouchpadOff" "integer"
              Switch off the touchpad.  Valid values are:

              0   Touchpad is enabled
              1   Touchpad is switched off
              2   Only tapping and scrolling is switched off
              Property: "Synaptics Off"

```

And something between those extremes: Add the  touchpadoff command to autostart or make it easy to use it, for example with an alias.

*Edit:* this works in Lubuntu and Xubuntu, while standard Ubuntu and Kubuntu have GUI applications for the corresponding tasks.

---

