---
title: "Weird Compiz Dual Screen Problem"
date: 2008-11-03
forum: General Help
---

### Post by MrSootentai on 2008-11-03
I'm trying to figure out how to fix this little problem I've been having with my Dual Monitor setup.

Whenever I have dual-monitor and compiz enabled I get this random black area to the right of my screen. This black area acts kind of like a black hole whenever a window rolls over it, the image lingers behind. Can anybody tell me how to fix this??

---

### Post by loomsen on 2008-11-04
Been strugglin hard with a similar issue. 
I found that disabling not only nautilus, but also gnome from drawing a background was the problem in my case.
[[img]http://img255.imageshack.us/img255/7899/screenshot55rl9.th.png[/img]](http://img255.imageshack.us/img255/7899/screenshot55rl9.png)


But your screener looks like you didn't do that eh?

What kind of dual layout do you use, separate X-Screens or TwinView?

If you're using TwinView disable the detect output option in CCSM->General Options
[[img]http://img354.imageshack.us/img354/6657/screenshot57qu7.th.png[/img]](http://img354.imageshack.us/img354/6657/screenshot57qu7.png)

Better to let X specify which options to use rather than compiz.

---

### Post by MrSootentai on 2008-11-04
Thanks but nothing helped.
I have an Intel video card, no nvidia so I just used the standard resolution settings on the 'Screen Resolution' area.
Any other ideas??

---

### Post by toddfx on 2008-11-20
I had the same problem (funky blank spot on the right of my second screen).

If you don't already have it install "CompizConfig Settings Manager" and launch it.
In the upper right confirm that you're on the problem screen.   In my case it was "Screen 1".
Click through to "General Options" -> "Display Settings".
Uncheck "Detect Outputs" and select the output below and click edit.
Set it to your screens resolution (mine is "1920x1080+0+0").

Close the settings manager, cross you fingers, say a prayer and restart X (control-alt-backspace).  With any luck you've reclaimed the blighted area.

Hope this helps.

---

### Post by MrSootentai on 2008-11-20
Thanks for the reply I'm sure it would've helped but no for some reason my Intrepid Ibex doesn't even detect the monitor when it is plugged in. For some reason after a kernel update the the Screen Resolution doesn't do anything when I click 'Detect Displays'.
But if I ever get it working again, I still thank thee.

---

