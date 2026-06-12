---
title: "Problem with 9.04, keyboard key repeat, Wine and City of Heroes."
date: 2009-05-02
forum: Installation &amp; Upgrades
---

### Post by ThePenciler on 2009-05-02
Here's a post on the WineHQ forums that has all the info so far. Hopefully I won't have to repeat myself. But I'll summarize after the jump.

[http://forum.winehq.org/viewtopic.php?t=4709&start=0&postdays=0&postorder=asc&highlight=](http://forum.winehq.org/viewtopic.php?t=4709&start=0&postdays=0&postorder=asc&highlight=)

Essentially:

Played CoH in Wine/Crossover Games for a couple years with no keyboard problems until I upgraded to 9.04
PS/2 105 key US keyboard
Wine 1.1.20 (before and after the upgrade)
Problem: When using the keys on the keyboard, for instance the WASD keys, if I press one key to move it repeats as if I'm hitting the key rapidly making the character do a stop/start dance until I tap another key while holding the first key down and then the first key acts as it should, moving the character smoothly. I've confirmed this is a problem with other keys as well, not just the WASD keys. I've also used another PS/2 keyboard as well as a USB keyboard (no software mods to get the multimedia keys to work, just plugged it in and used it as is). This problem existed before I used the USB keyboard and I haven't used the USB keyboard with Ubuntu until just now troubleshooting the problem.

---

### Post by ThePenciler on 2009-05-03
Bump just in case nobody saw it. :)

---

### Post by esemario on 2009-05-04
Same problem here. It only happens from 9.04, with 8.10 (same Wine version) everything goes fine. (32-bit versions both)

I've tried with World of Warcraft.

Meanwhile, I've just disabled the key repetition while playing games... :)

---

### Post by ubuntu1sttimer on 2009-05-12
Almostt gladdd to see that I am not thee only onee. Not correcting this so you can see what it looks like. 

Had 8.04 and upgraaded to 8.10 and it staaarted. Upgraaadedd to 8.10 and it still did it. Staarted overr with a clean install of 8.10 and it still does it.

Now deleting extra letters. Using this keyboard on several machines via a KVM. Ubuntu is only one that does it until I use Ubuntu. Then it happens on all machines so Ubuntu must be reprograming the keyboard. 

Am not using WINE. Any one with an idea?

---

### Post by chrismo on 2009-06-13
jep, same problem (but tested with wow), since i have upgraded to Jaunty.

only fix to this i have found is manually disable key repeat when playing games and enable when working e.g. in eclipse. 

System -> Preferences -> Keyboard -> Key Repeat

a littlebit annoying :)

i think someone messed keydown/up events in xorg or something like that...

---

### Post by Gen2ly on 2009-06-13
Yeah, had this problem with wow.  Has to do with the new xorg server.  One solution was to make a bash script that changed keyboard repeat and then launch wow:

```
#!/bin/bash
# wow launch

xset -r 24
xset -r 25
xset -r 26
xset -r 38
xset -r 39
xset -r 40
wine "C:\Program Files\World of Warcraft\WoW.exe"
```

---

### Post by Joe222 on 2009-06-16
For those of you comfortable with compiling wine, the key repeat problem under wine can be fixed with the attached patch for version 1.1.22. Will probably apply just fine to other versions as well.

Change to wine directory and use patch -p1 -i auto22.txt to apply.

---

### Post by ubuntu1sttimer on 2009-06-22
A few days ago the kernel in 9.04 was updated. Since that time I have not had any problems with the keyboard repeat issue. Appears that we were not the only ones having the problem and it got fixed.

In any case, it's a good job done on that issue.

---

### Post by JMuffin on 2009-06-24
My system is up to date and I am still experiencing this problem in World of Warcraft. Am I the only one?

---

### Post by Rody on 2009-06-24
+1


> **chrismo said:**
> jep, same problem (but tested with wow), since i have upgraded to jaunty.

Only fix to this i have found is manually disable key repeat when playing games and enable when working e.g. In eclipse. 

System -> preferences -> keyboard -> key repeat

a littlebit annoying :)

i think someone messed keydown/up events in xorg or something like that...

---

### Post by P.Arthur on 2009-06-26
I've got the same problem with key repeat not stopping from time to time, also with newest kernel installed.
But even worse, my keyboard and mouse are interfering badly like this:
When using keyboard only, everything's fine (exept for odd key repeat hangs), but when using touchpad, the keyboard's dead after, only plotting the key last hit when using touchpad again. Doing this a couple of times: pressing one key, moving mouse to make it appear on screen, hitting next key, moving mouse,..., then at some point, the keyboard is suddenly working fine again until next touchpad use.
Problem didn't occur with ubuntu 7.10 and 8.04 before. I did a fresh install from live cd for 9.04.
Please could anyone try helping me, because my notebook is close to unuseable like this.
P.S.: It's a MSI 635m notebook

---

### Post by t.rei on 2009-07-18
I have the same key-repeat issue, also I am disabling it via systemsettings to play games. 

Hopefully wine will see an upgrade some day to fix this.

On the other hand, it's probably more of an xorg thing.

---

### Post by Brebs on 2009-07-20
Joe222's patch [fixes the keyboard repeat in Thief 2](http://bugs.winehq.org/show_bug.cgi?id=18885), so I suggest you give it a try, then provide some decent feedback ;)

Edit:  Same patch is on [this wine bug](http://bugs.winehq.org/show_bug.cgi?id=18296) about keyboard auto-repeat.

---

### Post by t.rei on 2009-07-22
[http://bugs.freedesktop.org/show_bug.cgi?id=22515](http://bugs.freedesktop.org/show_bug.cgi?id=22515)

It's a X.org bug, known, and hopefully a fix is on it's way. yay.

Now to get wine to accept all my mouse Buttons on my MX Revolution (wheel tilt at last)

> Just confirmed in current git.
I'm not in the position to increase this bugs Priority, but IMO it should be
changed to high. This is now hitting mainstream distributions (eg Ubuntu 9.04)
and quite some apps may be affected, possibly in some subtle ways.
The problem is understood and Daniel seems to have a fix in his repo, so I hope
this will be resolved soon.

---

### Post by Kallewoof on 2010-01-03
Yeah, have it as well..

---

### Post by Kernelius on 2010-02-10
The same here.
Karmic Koala 64 bit fresh installation and the bug still affects it.

It is particularly clear in Gimp and Inkscape. You can't panning images with spacebar pressed because when repeat key press function starts you lose control over the panning, very bad.[-X

Wonder when this will be fixed.....

---

### Post by seebs on 2010-03-04
[http://bugs.freedesktop.org/show_bug.cgi?id=22515](http://bugs.freedesktop.org/show_bug.cgi?id=22515)

Known bug, fixed in upstream, no one has backported the fix or updated to a version of the X server which includes the fix.  I'd volunteer, but:
1.  Limited time.
2.  "Oh, I'll just upgrade the X server, that shouldn't cause any problems" <= too stupid for even me.

But that's the problem; it's an X server bug, there's a known fix.  If you can interest someone in backporting it, great.

---

