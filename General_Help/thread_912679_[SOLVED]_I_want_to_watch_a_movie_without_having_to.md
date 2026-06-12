---
title: "[SOLVED] I want to watch a movie without having to touch the mouse."
date: 2008-09-07
forum: General Help
---

### Post by SZF2001 on 2008-09-07
As in (what the title says), I want to watch a movie all the way through on my computer setup without having to be watching the movie, be twenty minutes in, the screen falls asleep, so I need to get up and move the mouse to continue the movie.

It's weird. It does it in totem, mplayer, xine, so I could only assume that it would be something to do with the Screen Saver settings and stuff, right? I turn off my screen saver and told the computer to be regarded as 'idle' after two hours. Still, with the screen saver basically off and idle set for two hours, twenty minutes later I'll be moving the mouse.

I go to the power manager (System -> Preferences -> Power Management) and set the bars to "Never" under "On AC" tab and the default settings under the "General" tab.

I don't know what to do at this point. It'd be nice to just finish a movie without having to move the mouse around every twenty minutes.

---

### Post by Pelham123 on 2008-09-07
Take a look at this thread...

[http://ubuntuforums.org/showthread.php?p=5738131](http://ubuntuforums.org/showthread.php?p=5738131)

---

### Post by SZF2001 on 2008-09-07
Hm... Alright, did that and started up a movie to see if it would surpass the 20 minute mark from last time before changing the settings.

Now it only got to ten minutes and it blacked. :(

---

### Post by Shazaam on 2008-09-07
Try this...
Backup xorg.conf. Then add this to it....
```
Section "ServerFlags"
    Option         "BlankTime" "0"
    Option         "StandbyTime" "0"
    Option         "SuspendTime" "0"
    Option         "OffTime" "0"
EndSection
```

---

### Post by kerry_s on 2008-09-07
before you play your movie, in term: xset -dpms
will turn off the energy stuff

xset +dpms = to turn back on

---

### Post by stinger30au on 2008-09-07
> **SZF2001 said:**
> As in (what the title says), I want to watch a movie all the way through on my computer setup without having to be watching the movie, be twenty minutes in, the screen falls asleep, so I need to get up and move the mouse to continue the movie.



i use VLC

out of the box it disables the screen saver and works a treat

---

### Post by SZF2001 on 2008-09-08
Tried out VLC.

Tried out a lot more media players.

Dammit ALL this screen just goes to sleep anyway.

---

### Post by rossjman1 on 2008-09-08
Did you uncheck dim screen on idle option in the power settings?

---

### Post by SZF2001 on 2008-09-08
> **rossjman1 said:**
> Did you uncheck dim screen on idle option in the power settings?

I don't see an option for that. Where you are talking about would be under System -> Preferences -> Power Management, correct?

---

### Post by rossjman1 on 2008-09-08
> **SZF2001 said:**
> I don't see an option for that. Where you are talking about would be under System -> Preferences -> Power Management, correct?
yes.

---

### Post by SZF2001 on 2008-09-08
> **rossjman1 said:**
> yes.

yikes

---

### Post by ad_267 on 2008-09-08
I think that option is only for laptops.

---

### Post by ryanhaigh on 2008-09-09
There is an applet you can add to your panel to supress power management, I am on windows at the moment so I can't be sure but I think it is called the inhibit applet. I haven't needed to use this before so I can't attest to its usefulness but its worth a shot.

---

### Post by mc4man on 2008-09-09
I have one box that behaves just like yours at the same settings (never, never in power management, screensaver off, regard computer as idle after 2hrs. (the others behave correctly

Still after 20 minutes or so the display goes to sleep.

What 'solved' it was to leave - screensaver off, never, never in power man. and set regard computer as idle to well **below** the time till display was going to sleep ( I set it to 4 min.
 
Now it never goes to sleep (tested to 28+hrs

I based it on this

> As soon as the session is marked at idle, GNOME Power Manager starts its own 'system' timer.
When the timeout set in gnome-power-preferences is reached, and the CPU load is idle, then the idle action is performed, which is usually to turn off the screen, or to suspend or hibernate.

To make this clearer, the sliders in gnome-power-preferences
are set to start at the value of the session-timeout + 1 minute, as we cannot logically trigger before the session is marked as idle.
If you adjust the value of the 'session idle' timeout in gnome-screensaver-preferences then the start of the sliders in gnome-power-preferences will change accordingly.

My warped theory being the display was going to sleep **before** power management had a chance to kick in (ie. the never setting) (idle time (120) + 1 min. till it could.
So now after 4+1 min. power management kicks in the never setting before the display is put to sleep (by what I'm not sure - hardware, bios combo maybe?

You may also want to try above mentioned applet

screen shows inhibit applet and when it's active, ie. the red circle and x mean the applet is off, not that power management is inhibited (i think

---

### Post by SZF2001 on 2008-09-09
> **ad_267 said:**
> I think that option is only for laptops.

Weird, that option is not on my laptop either. Straaaange.

> **ryanhaigh said:**
> There is an applet you can add to your panel to supress power management, I am on windows at the moment so I can't be sure but I think it is called the inhibit applet. I haven't needed to use this before so I can't attest to its usefulness but its worth a shot.

Installed it (think it was under the guise of emac plugins) and left it running at home, I'll get back to you guys if it works (if I get home and my screensaver is still going and is locked or when I watch a movie).

---

### Post by SZF2001 on 2008-09-09
update: Screen still idled with screensaver (had to lock computer). Will this be different with a movie? Anything else I should try?

---

### Post by SZF2001 on 2008-09-09
last update: messing with xorg like the previous post said works so I'll just close this thread now thanks for the help guys

---

