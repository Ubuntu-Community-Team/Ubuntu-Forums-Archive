---
title: "Switching primary monitor"
date: 2010-03-05
forum: Hardware
---

### Post by ntucker on 2010-03-05
Hi, I've just upgraded from hardy to jaunty, and I've run into a problem that I can't figure out a solution for.

I'm running on a laptop (Lenovo X61T in case anyone cares; Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller), and when I'm at my desk, I plug in a large external monitor and use that as my primary display, with the laptop off to the side as a secondary display.  On hardy, I had a little hotkey script that would toggle between the two-monitor desktop config and the one-monitor walking around config.  The script simply called xrandr to enable/disable the external monitor as appropriate and set the monitor position(s).

Unfortunately, on jaunty, I have two problems:  first, I can't seem to find any way at all to make the external monitor the primary monitor where the panels show up.  Having my task bar on the secondary monitor is kind of annoying.  Second, xrandr doesn't seem to work at all anymore. My script has no effect on the positions or enabled/disabled status of the screens.

For the primary monitor setting, I have seen many suggestions to edit my xorg config file, but I would like to stress that this is highly undesirable, because I don't want to restart X every time I sit down at my desk, nor was this necessary in hardy.

Anybody have any suggestions?

---

### Post by ntucker on 2010-03-05
Aw, my first ubuntu forums question and I answer it myself 15 minutes later.

To anyone else looking for this, the answers are: the names of the outputs in xrandr changed (formerly VGA and LVDS, now VGA1 and LVDS1), so my script needed to be updated,  and xrandr now has a "--primary" option that lets you specify the primary screen.

So now my extra monitor toggler just needs to do:

```

xrandr --output VGA1 --primary --pos 0x0 --mode 1600x1200 --output LVDS1 --pos 1600x150

```or

```

xrandr --output VGA1 --off

```

Edit to add: It would sure be nice if the monitor control panel would let you designate a primary monitor, by the way.

---

