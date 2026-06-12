---
title: "Graphics tablet and dual monitors"
date: 2011-01-10
forum: Hardware
---

### Post by elnaureth on 2011-01-10
I'm running Lucid on a laptop, and I just bought another monitor. I'm having a problem that has been mentioned a few times, which is that the area that my graphics tablet (a Genius MousePen 8x6) corresponds to is stretched across both monitors, so when I try to draw a circle, it comes out as a very stretched ellipse. [This thread]("http://ubuntuforums.org/showthread.php?t=1456359") says that someone found a solution by adjusting the TopX, BottomX, TopY, and BottomY values, but I don't understand how that fixes it; it seems to me like those values refer to coordinates on the tablet, not on the screen(s).

I'm using GIMP, and the idea [here]("http://forum.meetthegimp.org/index.php?action=printpage;topic=94.0") of setting the input mode to "Window" looked promising, but when I do that, GIMP's "fake" mouse pointer mostly behaves the way I want it to but the actual mouse pointer still acts like the tablet is mapped across both monitors, and GIMP will only recognize a click if the pen starts in a place on the tablet that corresponds to a place inside the GIMP window.

Can anyone help me out?

---

### Post by Favux on 2011-01-10
Hi elnaureth,

Welcome to Ubuntu forums!

I think we've managed to figure it out if you have Xorg 1.9 (Maverick), see:  [http://ubuntuforums.org/showthread.php?t=1656089](http://ubuntuforums.org/showthread.php?t=1656089)

Since you have Xorg 1.7, if you are using the Wizard Pen driver maybe Fwirt's [post #20]("http://ubuntuforums.org/showpost.php?p=10294043&postcount=20") & #24 will help.

---

### Post by elnaureth on 2011-01-12
Thanks! I decided to upgrade to Maverick. After I [reinstalled the wizardpen driver]("http://doctormo.org/2010/10/15/wizardpen-now-works-in-maverick/"), it worked fine.

---

### Post by Favux on 2011-01-12
Great!

Could I ask what worked fine?  The tablet or your dual monitor setup or both?

If you have the time could you summarize what you did?  And how is it working in Gimp?

---

### Post by elnaureth on 2011-01-12
Everything works fine. I was able to make the tablet area map to only the right monitor by using the [transformation matrix technique]("http://ubuntuforums.org/showthread.php?t=1656089"). Since both my monitors are widescreen, I also decided to [restrict the active area of the tablet]("http://ubuntuforums.org/showpost.php?p=10294492&postcount=24") to be similar (in the geometric sense) to my right monitor. (Note that in Maverick the configuration file in question is /usr/share/X11/xorg.conf.d/70-wizardpen.conf.)

This works fine in GIMP - I set the input mode for the tablet to "Screen," and tracing a circle actually gives me a circle.

---

### Post by Favux on 2011-01-12
Outstanding!  We have a workable method for all tablets it looks like.  Thanks for taking the time to summarize.

---

