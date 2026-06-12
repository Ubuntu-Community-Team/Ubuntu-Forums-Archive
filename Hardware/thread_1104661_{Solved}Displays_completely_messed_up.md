---
title: "{Solved}Displays completely messed up"
date: 2009-03-23
forum: Hardware
---

### Post by linuxuser21 on 2009-03-23
Help!  I have dual monitors set up with the fglrx drivers.  I just got a 1gb RAM stick, put it in and turned my computer on.  When it turned on, the loading screen was good on both monitors; however when it got to my main desktop screen, my left monitor said "PC Settings Correct?" as if the resolution or the refresh rate was too much for it.  Along with that, my right screen's resolution had changed dramatically and was really screwed up.  Please help.  I need both screens working.

---

### Post by linuxuser21 on 2009-03-23
Would it help to reinstall the fglrx drivers possibly?

---

### Post by linuxuser21 on 2009-03-24
Okay, I got the dual monitors working again; however, now the left screen's resolution is really tiny and it's difficult to even read anything on it.  Is there any way to change the resolution of just the one screen?  While I'm at it, the refresh rate seems to be off as well.

---

### Post by Neo_The_User on 2009-03-24
Go into Catalyst and move the screens around. It's probably set up as "Big desktop right of Display 2" or something like that in the display manager of the Catalyst control center. Try messing with the settings for a bit, then hit Control Alt Backspace after you applied the wrong display settings. Log back in, go back into Catalyst, configure the settings the way you want again, then see if its still messed up. Reinstalling the drivers will not help as Ubuntu never forgets anything. ;)

You can change the resolution of that one screen by hand if you want by going into Catalyst > Display Manager. You should see 1 and 2. One is red and the other should be black or white, I forget. Click on the number of the display you would like to change the resolution on, then if you look down a bit right under the 2 numbers, you should see "Display Size" or something like that.

Cheers!

P.S. Post sooner on my visitor messages next time. You don't need to be this patient hahaha.

---

### Post by linuxuser21 on 2009-03-24
> **Neo_The_User said:**
> You can change the resolution of that one screen by hand if you want by going into Catalyst > Display Manager. You should see 1 and 2. One is red and the other should be black or white, I forget. Click on the number of the display you would like to change the resolution on, then if you look down a bit right under the 2 numbers, you should see "Display Size" or something like that.

In the Display Manager, I am unable to change anything.  I know that the reason for the screen not being able to display it is because of the screen itself.  When I plug in the other monitor to its head, it works fine.  I'm not quite sure how it did it before.

---

### Post by Neo_The_User on 2009-03-24
what do you mean plug the monitor into its head, and it not being able to display due to the screen itself?

---

### Post by linuxuser21 on 2009-03-25
Okay, I have two different monitors because I don't have have the money or need to just buy two new ones.  One is newer than the other.  The newer one must not be able to handle a big resolution.  If I disable dual monitors settings and adjust that display individually, I can set it to a lower one and it works fine.  The dual monitor setting sets the resolutions to ones that the one monitor cannot handle.

---

### Post by Neo_The_User on 2009-03-25
Ahhh! 2 different resolutions at the same time. My dad did it a long time ago reading the man pages or something for aticonfig. He combined like 6 strings of the aticonfig commands and rebooted, worked fine.

Example:
```

man aticonfig (then read all the stuff)
sudo aticonfig --output --left-of-display-VGA --initial -f --force -yes --then-you-just--keep --mixing --it-up -until --you-have -it -set--up -the-way--you -want

```

---

### Post by linuxuser21 on 2009-03-25
Actually, I don't even need it to be separate resolutions.  I just need them both to be at (1280 X 1024).  Instead, when I have the desktop stretched, they're at the biggest resolution possible.  Something like (1600 X 1200) probably.

---

### Post by Neo_The_User on 2009-03-27
well for independant displays, man aticonfig

for big desktop:

catalyst > display manager > the 2nd tab > click the screen 1 > big desktop left of display 2.

That way its like [1] [2] instead of vice versa.

---

### Post by linuxuser21 on 2009-03-27
Actually, I have to have it on "Big Desktop left of desktop 1" because of my one screen not being able to handle the resolution....  Wow, I have this thing messed up, whatever though I guess.  lol.  Regardless of the resolution issue, it's working on both screens and I guess I'm content with that until we figure it out.  Now, I've just got to find out why my dock doesn't like the idea of working when I do have dual monitors.

---

### Post by linuxuser21 on 2009-03-27
Why am I getting this?
```
~$ man aticonfig
No manual entry for aticonfig
See 'man 7 undocumented' for help when manual pages are not available.
```

---

### Post by linuxuser21 on 2009-03-27
Check this out.  This is what is wrong with my desktop.  Both of those applications are maximized and take up the whole screens; however, there is that space below the application on the left screen and space to the right on the right screen that doesn't even show up on the monitors.  Ugh.

---

### Post by Neo_The_User on 2009-03-28
are you able to manually drag the window down lower by hand and expand it further? if not, its a driver issue. 9.3 came out a few days ago.

[http://ubuntuforums.org/showthread.php?t=1097993](http://ubuntuforums.org/showthread.php?t=1097993)

Replace the 9.2 in the wget link to 9.3.

---

### Post by linuxuser21 on 2009-03-28
I did everything you said; but, still no go.  It's nice to have updated drivers and an updated Catalyst Control Center though.  I am able to manually expand windows further down; so, I guess that wasn't the issue anyways.

---

### Post by Neo_The_User on 2009-03-28
maybe it detects toolbar(s) underneath the window making it not able to fully expand automatically. try moving the toolbars around, adding, removing, etc.

---

### Post by linuxuser21 on 2009-03-28
I have but one small panel at the top for force quit, update notifications, stuff like that.  I got rid of them for the most part when I got Cairo Dock.  I don't want windows to maximize all the way because then, they'll be off the screen.  They maximize just enough to fill the screen perfectly.
Not much of a problem then I guess, it just screws up the wallpaper on the left screen (it's zoomed in & cut off).  That & until recently, the rightmost dock was hidden.  I have the bottom dock moved over to the right screen (hopefully temporarily) because it too, was hidden.

---

### Post by linuxuser21 on 2009-03-29
Can anyone help me please?!  To shorten it up; when I have dual monitors, both Catalyst & Screen Resolution say that my resolution is 3200 X 1200.  I need it at 2560 X 1024.  I think at one time, I edited a file with Gedit and changed some resolution settings around.  I'm pretty sure that it was for the login screen though.  Can the same thing be done with the desktop?

---

### Post by linuxuser21 on 2009-03-29
Bump.

---

### Post by linuxuser21 on 2009-03-29
Bumping.

---

### Post by linuxuser21 on 2009-03-30
Still bumping...

---

### Post by linuxuser21 on 2009-04-04
Bump again.

---

### Post by linuxuser21 on 2009-04-09
I finally just got frustrated enough to where I just bought a new monitor.  My plan was to get a monitor that could handle 1600 X 1200 resolution.  So, I did, plugged it in and of course it worked.  The part that made me roll my eyes was when I looked at the resolution, it was... 2560 X 1024, the resolution I *needed* all along.  I don't know how that works, where it just suddenly changes (to a smaller resolution) when I get a monitor that can handle bigger than what I need, whatever though, I'm not complaining.  I really hope these kind of things are fixed with 9.04.

It works :guitar:

---

