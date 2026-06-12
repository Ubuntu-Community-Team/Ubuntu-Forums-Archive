---
title: "Wacom touch configuration GUI?"
date: 2013-09-18
forum: Hardware
---

### Post by Bucky Ball on 2013-09-18
Hi all,

Just bought a secondhand Wacom Bamboo Pen & Touch, model 661/s. Plugged it in to my 12.04 LTS laptop and, voila, it just works! For clarity, I am running a minimal install with xfce4 as desktop environment and just the apps I like/need/want.

So I have been hunting high and low for a Linux configuration GUI for the Bamboo, but not finding. Yep, I could spend some hours that I can't afford to on nutting out how to do it with /usr/share/X11/xorg.conf.d but a simple GUI is what I need right now. 

Can anyone point me in the right direction? I'm kind of enjoying using the touch function to navigate but am getting a bit of a headache from the learning curve. I have never used a touch device before (ok, call me old-fashioned) so the taps and gestures are all new. But I'm getting there and can see how it could speed things up ... eventually, when the muscle memory kicks in (let's not debate the existence or non- of muscle memory, that would be off-topic). 

When I've got more time I'll delve into using the pen and doing some graphics stuff (it worked straight up with Gimp and everything else I've tried, I love Ubuntu), but for now, a config GUI, anyone?

Cheers and tnx in advance ... ;)

---

### Post by Bucky Ball on 2013-09-19
Well, kinda found a solution, and it was right under my nose. Apps>Settings>Settings Manager>Mouse & Touchpad, and there it is, the Wacom is 'in the frame' and there are some options. I'll need to fiddle around a bit but they look fairly limited.

---

### Post by Favux on 2013-09-20
Hi Bucky Ball,

No real gui right now.  The in driver supported 2 finger gestures were grandfathered in and there are no plans to add 3 or 4 finger gestures.  So the Gnome System Settings Wacom gui applet is not likely to incorporate any touch stuff.  Don't know what the plan for the KDE applet is.  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=External_applications#Graphical_Configuration_Tools](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=External_applications#Graphical_Configuration_Tools)  XFCE unfortunately doesn't help your options.

You can read some of my deathless prose on gestures in the Wacom manual, i.e. **man wacom** in a terminal.  And more prose sure to stand the test of time on the multitouch wiki page:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Multitouch](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Multitouch)  How to change the feel with the acceleration profile and other goodies there.  Unfortunately the BambooPT HOW TO continues to become more dated:  [http://ubuntuforums.org/showthread.php?t=1515562](http://ubuntuforums.org/showthread.php?t=1515562)

---

