---
title: "Linux Wacom Driver (temp) disable touch?"
date: 2010-03-18
forum: Hardware
---

### Post by nikosm on 2010-03-18
Hello,

I have a Lenovo X200t (tablet) and I have the following problem: when I write on [xournal]("http://xournal.sourceforge.net/") with the stylus and my palm is resting on the screen, there is a lag between writing and the "ink" appearing. It's not too much (maybe half a second), but enough to make it difficult to write precisely. Also, circles look a bit "edgy" when drawn with the palm resting on screen.

Is it possible to (temporarily) disable touch? Would that make the problem go away?

Thanks for any ideas,
Nikos

Info: Lenovo x200t, karmic, 2.6.31-20-generic kernel, linux-wacom-0.8.6-11 compiled from source using an fdi copied from user favux (thanks!)

---

### Post by nikosm on 2010-03-19
bump -anyone?

---

### Post by mcoleman44 on 2010-03-19
Off
```
xsetwacom set touch touch off
```

On
```
xsetwacom set touch touch on
```

---

### Post by nikosm on 2010-03-20
mcoleman44, thank you for your reply!

However this doesn't completely solve the problem. Indeed touch is turned off, but there is still a lag between writing and the ink appearing, which makes the handwriting less precise (it even misses some points in the stroke, e.g. circles look like polygons).

Any ideas of how to get touch ignored (maybe on a hardware level)?

Thanks again!
Nikos

---

### Post by mcoleman44 on 2010-03-20
Which hid-ntrig patch are you using? I had this problem with one of the older hid-ntrig.ko but when I used the newest one it took care of the problem.

---

### Post by mcoleman44 on 2010-03-20
And if you want touch ignored then just comment out that section of xorg.conf. You use # to comment out a line.

---

### Post by nikosm on 2010-03-20
Hi again mcoleman44,

Lenovo doesn't have ntrig but wacom. I didn't patch anything, instead I followed the instructions of [this post]("http://ubuntuforums.org/showthread.php?t=1038949") and used the fdi by favux in [this post]("http://ubuntuforums.org/showpost.php?p=8507244&postcount=4").

I don't use xorg for anything except the trackpoint. Could you share the fdi you are using? Maybe that has something to do with it.

Thanks!
Nikos

---

### Post by mcoleman44 on 2010-03-20
What version of wacom are you using? And I use an xorg.conf not an .fdi.

---

### Post by nikosm on 2010-03-20
> **mcoleman44 said:**
> What version of wacom are you using? And I use an xorg.conf not an .fdi.

0.8.5-11 . I am trying to see if there is any change using the other fdi's that favux put in his how-to and that I had overlooked before. I'll let you know.

---

### Post by mcoleman44 on 2010-03-20
You can try that, but I dont really think its the fdi. It sounds more like the module just isnt working well. You might want to try an earlier version of wacom. 0.8.5-10 maybe. I say this because -11 still has some bugs where it was just released -10 may have less problems.

---

### Post by nikosm on 2010-03-20
You are right, changing the fdi didn't do anything (except that touch stopped working all together, but the lag was still there). I will install an older linux wacom when I have more time.

Thanks for your help!
Nikos

---

### Post by ahdlm on 2010-09-13
> **mcoleman44 said:**
> Off
```
xsetwacom set touch touch off
```

On
```
xsetwacom set touch touch on
```
where is this code entered for it to take effect?  I tried to just add it to
xorg.conf, but that didn't work.  I don't know if it needed to be inside a section,
or in a section of its own.

---

### Post by nikosm on 2010-09-13
hi ahdlm,

you have to enter these commands into a terminal, not in the xorg.conf. Go to Applications > Accessories > Terminal and enter the command there.

hope this helps,
Nikos

---

### Post by sephiroth_slash on 2011-04-19
For me I have a wacom Pen & Touch, After managing to Install it using the official LinuxWacom tutorial , I use the [FONT=Courier New][SIZE=2]xsetwacom [FONT=Arial]to enable disable the Touch pad, here's how ( commands )  : 

[FONT=Courier New]$ xsetwacom list dev

[FONT=Arial]it should return something like ( for my case ) : [/FONT]

Wacom BambooFun 2FG 4x5 Finger pad PAD       
Wacom BambooFun 2FG 4x5 Finger touch TOUCH         [FONT=System][SIZE=1]<== we're intrested in this [/SIZE][/FONT]
Wacom BambooFun 2FG 4x5 Pen eraser ERASER    
Wacom BambooFun 2FG 4x5 Pen stylus STYLUS 

[FONT=Arial]then use : [/FONT]

$ xsetwacom "[/FONT][/FONT][/SIZE][/FONT][FONT=Courier New][SIZE=2][FONT=Arial][FONT=Courier New]Wacom BambooFun 2FG 4x5 Finger touch" Touch off [FONT=Arial]( disable it )[/FONT]

[/FONT][/FONT][/SIZE][/FONT][FONT=Courier New][SIZE=2][FONT=Arial][FONT=Courier New]$ xsetwacom "[/FONT][/FONT][/SIZE][/FONT][FONT=Courier New][SIZE=2][FONT=Arial][FONT=Courier New]Wacom BambooFun 2FG 4x5 Finger touch" Touch on [FONT=Arial]( enable it )[/FONT][/FONT][/FONT][/SIZE][/FONT]

Note that you should use the string describing the device WITHOUT the last uppercase word ( [FONT=Courier New]TOUCH[/FONT] ), and so with other devices ( [FONT=Courier New]ERASER, STYLUS ...[/FONT])

Hope it helps
[FONT=Courier New][SIZE=2][FONT=Arial][FONT=Courier New]



[/FONT][/FONT][/SIZE][/FONT]

---

