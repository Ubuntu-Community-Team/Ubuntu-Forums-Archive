---
title: "xwinwrap on both monitors"
date: 2008-09-10
forum: General Help
---

### Post by rune0077 on 2008-09-10
Did anyone ever get xwinwrap to span across both monitors instead of just running on one of them? And if so, how to go about it?

---

### Post by overdrank on 2008-09-10
> **rune0077 said:**
> Did anyone ever get xwinwrap to span across both monitors instead of just running on one of them? And if so, how to go about it?

Hi and I just installed xwinwrap on my only dual monitor system with nvidia graphics and it spans both screens. I am **not** using separate x configuration.

---

### Post by rune0077 on 2008-09-10
> **overdrank said:**
> Hi and I just installed xwinwrap on my only dual monitor system with nvidia graphics and it spans both screens. I am **not** using separate x configuration.

Funny, I have a nvidia card as well, and xwinwrap only opens on my main monitor. Weird! I'm using normal TwinView as well, no seperate x screen.

---

### Post by overdrank on 2008-09-10
> **rune0077 said:**
> Funny, I have a nvidia card as well, and xwinwrap only opens on my main monitor. Weird! I'm using normal TwinView as well, no seperate x screen.

I once had a similar issue onces on a intel graphics but I do not know what happened to the issue at the moment. Try moving the terminal to another virtual desktop and then start xwinwrap. Just throwing out ideas :)

---

### Post by rune0077 on 2008-09-10
> **overdrank said:**
> I once had a similar issue onces on a intel graphics but I do not know what happened to the issue at the moment. Try moving the terminal to another virtual desktop and then start xwinwrap. Just throwing out ideas :)

Yeah I tried that already. It still opens on the other screen :) Are you running a screensaver with xwinwrap or a video? Since I'm running a video-file, it may actually be mplayer's fault, not xwinwrap. I'll try running a screensaver instead.

---

### Post by rune0077 on 2008-09-10
Nope. It made no difference, screensaver also only ran on one screen.

---

### Post by wmatthews on 2010-01-13
Anyone ever figure this out?

---

### Post by Sofsip on 2010-01-19
Hello! The closest I came to make it work on a dual screen is with the following bash script:

#!/bin/sh

killall xwinwrap

gnome-terminal --command="xwinwrap -g 1600x900 -ni -o 0.20 -fs -s -sp -st -b -nf -- /usr/lib/xscreensaver/glmatrix -window-id WID"
gnome-terminal --command="xwinwrap -g 1600x900+1+0 -ni -o 0.20 -fs -s -sp -st -b -nf -- /usr/lib/xscreensaver/glmatrix -window-id WID"



I know it's not truly dual screen; the script  launches two terminal running Xwinwrap in each individual screen but it's as close I could get with all my knowledge of bash programming ( I'm a bit new to it) so if anyone can improve the way it works I'd be glad to learn!

I'm also using Nvidia configured in TwinView.

 I hope it helps!

---

### Post by Krazie316 on 2011-04-06
> **Sofsip said:**
> Hello! The closest I came to make it work on a dual screen is with the following bash script:

#!/bin/sh

killall xwinwrap

gnome-terminal --command="xwinwrap -g 1600x900 -ni -o 0.20 -fs -s -sp -st -b -nf -- /usr/lib/xscreensaver/glmatrix -window-id WID"
gnome-terminal --command="xwinwrap -g 1600x900+1+0 -ni -o 0.20 -fs -s -sp -st -b -nf -- /usr/lib/xscreensaver/glmatrix -window-id WID"



I know it's not truly dual screen; the script  launches two terminal running Xwinwrap in each individual screen but it's as close I could get with all my knowledge of bash programming ( I'm a bit new to it) so if anyone can improve the way it works I'd be glad to learn!

I'm also using Nvidia configured in TwinView.

 I hope it helps!
Sweet work man, I have a triple screen setup and was wondering if you knew how to modify the code to show up on the third screen.  I just started using Ubuntu Sunday so I tried modding the command you gave for a third monitor and am having no luck.  I have no clue where to start or what to change really, lol.

I'm Using an XFX ATI Radeon HD 6870

---

