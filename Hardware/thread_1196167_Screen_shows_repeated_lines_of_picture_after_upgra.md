---
title: "Screen shows repeated lines of picture after upgrade"
date: 2009-06-24
forum: Hardware
---

### Post by ajmurmann on 2009-06-24
I am running Ubuntu Jaunty on my Sony VGN-FZ240E. Everything was running fine under Hardy. After I upraded from Hardy to Jaunty Compiz wasn't working correctly anymore. The Cairo-Dock had a black box around it and the unction that's lik OS X's Expose wasn't working anymore. Since I was very busy lately I didn't look into that.
However I just installed a bunch of updates that were released during the last days and which required a reboot. After that the screen just showed two repeated, alternating lines, one of which was just white and the other one shows a snippet from what's going on. I can move the mouse in it and log in (without seeing what I am doing). I am usually more of a GUI person and am therefore pretty helpless now. I already tried to fix the graphic setting automatically from the rescue menu.

I know it would be helpful to know which upgrades I insalled, but the list was huge and I didn't look at everything. I however remember there was a Compiz update in there.

Here is a photo of what's going on:

[IMG]http://personel.s3.amazonaws.com/screen_problem.jpg[/IMG]

Thank you very much for all help!

---

### Post by ajmurmann on 2009-06-24
Ok, I installed the old 2.4 drivers from Intrepid using [this]("https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4") manual.
Now the repeated lines are gone. The login screen is all normal. However when I login selecting Gnome for the session, the music plays and then the screen flickers a few times and I am back at the login screen. So I am once again clueless what to do but really need this thing to work.

---

### Post by ajmurmann on 2009-06-25
Ok, the problem turned out to be caused by mesa drivers 7.5 from xorg-edgers PPA. After I unistalled that it all worked again.

(Although the process of getting there was "a little" more complicated)

---

