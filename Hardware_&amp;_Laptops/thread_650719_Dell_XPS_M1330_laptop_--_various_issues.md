---
title: "Dell XPS M1330 laptop -- various issues"
date: 2007-12-26
forum: Hardware &amp; Laptops
---

### Post by ethanay on 2007-12-26
as a preface -- please forgive and bear with me, as I am a complete Linux beginner (just switched from Windows), if I am doing something contrary or leaving out info, etc etc...

I think I (mostly)  have 7.10 working with my Dell XPS M1330 laptop, but there are some outstanding issues:

1) Suspend function (to memory) doesn't work -- functions same as "lock screen."  So instead of suspending, I just get the normal lock screen dialog...very weird.  Like the function got completely remapped or something? :confused:

Here's an update:  initiating "suspend" (which locks screen) and then closing the lid returns "action forbidden:  policy timeout is not valid.   Please wait a few seconds and try again."

2) Laptop lid close does not blank/turn off screen, even though it is set to do that.  Blank screen works on idle timer (at 11 minutes).

2) Internal microphone doesn't work.

3) HDD load_cycle_count increases at several times/minute (one ~10-15 seconds) with a hdparm -B <254. Tried ubuntu_demon's fix, but it seemed to have no effect.  I have no idea what is accessing the hdd so often, but a) i don't want to burn through my  hdd that fast and b) the click is FRIGGING ANNOYING (surprised that no one mentioned how annoying the click is).  I would like to have some bump protection (and longer battery life)... :confused:

Right now, with a 9-cell battery I get about 3.5-5 hrs of work use, meaning e-mail, typing/office apps, file management, etc (no music/movies/cd/dvd access).  

Much appreciated if anyone can offer any support, etc

thanks,
Ethan

---

### Post by erginemr on 2007-12-27
Other problems aside, for the suspend / resume problem, please read the following post and check out the links I have given in my post there:

[http://ubuntuforums.org/showthread.php?t=608426](http://ubuntuforums.org/showthread.php?t=608426)

---

### Post by ethanay on 2007-12-27
thanks for the suggestions -- I followed them but with no noticeable change.

hibernate stopped working, so now I am working on getting both s2disk/s2both and s2ram working via uswsusp.

s2disk/both seems to work now, but for some reason s2ram isn't showing up as a valid command.

furthermore, using uswsusp seems to have reset the (temporary) fixes that i've made to prolong the life of my hdd -- so resuming from them cause hdparm to be set back to <254, which means several clicks (load/unload cycles) per minute on my hdd. 

 suggestions on how to keep the 254 value on resume from suspend using uswsusp?  (until of course i figure out how to have bump protection/powersave w/o constant unnecessary writes to my hdd)

---

### Post by jespdj on 2007-12-28
For the internal microphone, see [bug # 147682]("https://bugs.launchpad.net/dell/+bug/147682") (a fix is available there).

For the hard disk load cycle problem (which is not specific to the M1330), see [this thread](http://ubuntuforums.org/showthread.php?t=591503).

---

### Post by ethanay on 2007-12-30
Ok, here's an update:

for some reason, suspend (to ram) is now working.  No clue why or how.  On resume, I have to manually:
1) restart my networking (to get wireless back)
2) re-enter the hdparm -B 254 to stop the hdd clicking
3) restart alsa soundsystem

and i have no clue what to do about the fact that the screen brightness is locked into the dimmest setting and no longer controllable (via buttons or power manager) until reboot

I have tried the fixes for the networking and the hdd and they work on shut-down/power-on/reboot but apparently not for resume?

Ethan

---

