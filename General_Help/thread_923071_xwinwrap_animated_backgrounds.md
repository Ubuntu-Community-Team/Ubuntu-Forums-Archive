---
title: "xwinwrap animated backgrounds"
date: 2008-09-18
forum: General Help
---

### Post by 0xdeadc0de on 2008-09-18
hello all, I'm trying to use xwinwrap to make my compiz-fusion background an animated screensaver. It works just fine, that is, when I launch it in a console, but when I try with a gnome panel button it fails. I made a simple bash script:
```

killall xwinwrap
case $1 in
matrix)
        /usr/bin/xwinwrap -ni -argb -fs -s -st -sp -nf -b -- /usr/lib/xscreensaver/glmatrix -window-id WID
;;
lattice)
        /usr/bin/xwinwrap -ni -argb -fs -s -st -sp -nf -b -- /usr/lib/xscreensaver/lattice -window-id WID
;;
skyrocket)
        /usr/bin/xwinwrap -ni -argb -fs -s -st -sp -nf -b -- /usr/lib/xscreensaver/skyrocket -window-id WID
;;
fspot)
        /usr/bin/xwinwrap -ni -argb -fs -s -st -sp -nf -b -- /usr/lib/gnome-screensaver/gnome-screensaver/f-spot-screensaver -window-id WID
;;
slideshow)
        /usr/bin/xwinwrap -ni -argb -fs -s -st -sp -nf -b -- /usr/lib/xscreensaver/glslideshow -window-id WID
;;
esac

```

to make it easier to change it up, and made the launchers to run the script (named launchWinWrap)

The problem is, it fails to start from the launchers.
Now if I wrap the launcher in say
xterm -e '/home/user/bin/launchWinWrap matrix' it works, but I have that nasty little xterm window

What's the proper way to launch this without ending up with a terminal? 

When I launch the script using alt+f2 and type it in, it works just fine

---

### Post by easybake on 2008-09-18
> **0xdeadc0de said:**
> hello all, I'm trying to use xwinwrap to make my compiz-fusion background an animated screensaver. It works just fine, that is, when I launch it in a console, but when I try with a gnome panel button it fails. I made a simple bash script:

to make it easier to change it up, and made the launchers to run the script (named launchWinWrap)

The problem is, it fails to start from the launchers.
Now if I wrap the launcher in say
xterm -e '/home/user/bin/launchWinWrap matrix' it works, but I have that nasty little xterm window

What's the proper way to launch this without ending up with a terminal? 

When I launch the script using alt+f2 and type it in, it works just fine

What are the launcher commands you use? If you are using 4 different launchers already, then you could just make a script for each one instead of trying to have all the commands in one script. 

Sometimes launchers can't handle commands the exact way terminals do, I have no idea why.

You could try to make a toggle script that would cycle through each of them instead if you wanted to only make one script. 

Your best bet would be to just make 4 different scripts for your launchers.

---

### Post by 0xdeadc0de on 2008-09-22
well, making seperate scripts didn't help:confused:, turns out it worked some of the time the way it was, but not always.. don't know why, but after adding a sleep 1 after the killall statement, it appears to now be working every time from the launchers:guitar:

```

killall xwinwrap

sleep 1
echo $1 > /home/deadc0de/bin/temp

case $1 in
matrix)
        /usr/bin/xwinwrap -ni -argb -fs -s -st -sp -nf -b -- /usr/lib/xscreensaver/glmatrix -window-id WID
;;
lattice)
        /usr/bin/xwinwrap -ni -argb -fs -s -st -sp -nf -b -- /usr/lib/xscreensaver/lattice -window-id WID
;;
skyrocket)
        /usr/bin/xwinwrap -ni -argb -fs -s -st -sp -nf -b -- /usr/lib/xscreensaver/skyrocket -window-id WID
;;
fspot)
        /usr/bin/xwinwrap -ni -argb -fs -s -st -sp -nf -a -- /usr/lib/gnome-screensaver/gnome-screensaver/f-spot-screensaver
;;
slideshow)
        /usr/bin/xwinwrap -ni -argb -fs -s -st -sp -nf -b -- /usr/lib/xscreensaver/glslideshow -window-id WID
;;
esac

```

Note however: Slideshow background is blank, and fspot doesn't work as a background - it creates it's own little window.:popcorn:


You can see it in action here for those interested:
[http://www.youtube.com/watch?v=BU7sofxyy30](http://www.youtube.com/watch?v=BU7sofxyy30)
(Just uploaded will take a few minutes to process)
Recorded with gtk-recordmydesktop

---

