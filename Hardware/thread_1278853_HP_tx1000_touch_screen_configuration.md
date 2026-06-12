---
title: "HP tx1000 touch screen configuration"
date: 2009-09-30
forum: Hardware
---

### Post by beastrace91 on 2009-09-30
Hey There,

So I just obtained a shiny new(ish) HP tx1000 tablet, I promptly installed Ubuntu on it and I am finding alot of the tablet features do not work. I got the basic pen working but a few other features I was wondering if are possible in Ubuntu/Linux regarding the touch screen

1.) Screen Auto flipping to the proper view when you flip the screen around over the keyboard

2.) Finger touch support? Right now only the pen is working.

3.) Multi-touch? This one is not a big deal but would be super nice to have.

4.) Is there a way I can right click while using the pen?

5.) On screen keyboard? Where is it located?

If someone could answer any/all of these questions that would be awesome, or point me to a how to perhaps.

Thanks,
~Jeff

---

### Post by beastrace91 on 2009-09-30
I hate to bump threads that are only a few hours old but I really need some of this functionality :( I am also lacking click and hold, which is a feature I need to write on the screen (instead of just clicking things)

I'm installing Vista on a computer I own for the first time in almost year. Hopefully I can get most of the above working in Ubuntu at some point, but for now I really need the touch screen to just work so I can use the computer to take notes.

~Jeff

---

### Post by Favux on 2009-09-30
Hi beastrace91,

To get it working see this thread:  [http://ubuntuforums.org/showthread.php?t=1040872&highlight=tx1000](http://ubuntuforums.org/showthread.php?t=1040872&highlight=tx1000)

Also for rotation:  [http://ubuntuforums.org/showthread.php?p=6274392](http://ubuntuforums.org/showthread.php?p=6274392)

For an on screen keyboard (CellWriter) see post #5 here:  [http://ubuntuforums.org/showthread.php?t=1259154](http://ubuntuforums.org/showthread.php?t=1259154)

For gestures see avel's post #418 re: Easystroke here:  [http://ubuntuforums.org/showthread.php?t=837032&page=42&highlight=tablet](http://ubuntuforums.org/showthread.php?t=837032&page=42&highlight=tablet)

And you'll most likely want Xournal.

Hope this helps.

---

### Post by beastrace91 on 2009-09-30
Thanks for the threads! How about a click and hold with the pen? So I could for example use the pen to move windows around or scroll up and down.

~Jeff

---

### Post by Favux on 2009-09-30
Hi beastrace91,

I'm not that familiar with the TX1000.   I think you should be able to do that.  I seem to dimly remember that was something Tom Jaeger (the Easystroke author) fixed with his patch(es).  Or maybe you could do it through EasyStroke?

Anyway it'll probably be faster for you to read through the stuff rather that rely on me.  Especially since you now know the keywords to search.  Let me know if you figure it out.

Edit:  I actually remembered!  That's what they're talking about starting in aoubt post #14 in the first link I gave you.  And then qhimq in post #16 shows you the terminal commands to fix it.  There may be newer stuff by now.  So read up before you do anything.

---

### Post by Favux on 2009-10-01
Hi Jeff,

I accidently gave you the old Cairo Dock ppa.  Here's the new one:  [https://launchpad.net/~cairo-dock-team/+archive/ppa](https://launchpad.net/~cairo-dock-team/+archive/ppa)  That should get you 2.1.  It's pretty good.

More links:

[https://wiki.ubuntu.com/LaptopTestingTeam/HPPaviliontx1220ca](https://wiki.ubuntu.com/LaptopTestingTeam/HPPaviliontx1220ca)

[http://kellyandsopho.com/tiki/tiki-index.php?page=LinuxOnHpPaviliontx1000z#_Touch_Screen](http://kellyandsopho.com/tiki/tiki-index.php?page=LinuxOnHpPaviliontx1000z#_Touch_Screen)

[http://ubuntuforums.org/showthread.php?t=442483](http://ubuntuforums.org/showthread.php?t=442483)  Then if you use the Search This Thread feature top right you'll get posts like:
[http://ubuntuforums.org/showpost.php?p=4241341&postcount=579](http://ubuntuforums.org/showpost.php?p=4241341&postcount=579)  which links to this script:
[http://ubuntuforums.org/showpost.php?p=3857097&postcount=427](http://ubuntuforums.org/showpost.php?p=3857097&postcount=427)  Which as you can see is similar to the rotation scripts I referred you to, minus the xsetwacom lines.

And here's another similar script on the same thread:  [http://ubuntuforums.org/showthread.php?p=2963073&highlight=rotation#post2963073](http://ubuntuforums.org/showthread.php?p=2963073&highlight=rotation#post2963073)

---

