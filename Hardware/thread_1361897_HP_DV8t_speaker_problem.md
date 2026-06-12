---
title: "HP DV8t speaker problem"
date: 2009-12-22
forum: Hardware
---

### Post by aklyatne on 2009-12-22
I'm running 9.10 Karmic, and having a pretty annoying problem with my speakers.  This is a pretty new computer, and has two kinds of speakers; the normal laptop tweeters in a bar below the screen, and a very tiny subwoofer on the underside of the case.  Ubuntu, however, seems to only recognize the woofer.  This is a problem.  Sound is being passed through nothing but the woofer.  I've looked for fixes, and found something about disabling the modem.  That didn't work.  Any help?

---

### Post by aklyatne on 2009-12-23
Bump.  Oh also, I believe that I'm using 64bit, if it makes a difference.

---

### Post by ironhorse7 on 2010-02-14
I am having the same trouble as well! 64 bit Ubuntu just outputs sound to the sub.

---

### Post by Toolbelt on 2010-03-18
This is not a 64-bit problem, I loaded 32-bit on my machine to avoid having to get Lightscribe 4L to work and a couple other programs.  My speakers are also non-functional.

---

### Post by bherrmann7 on 2010-04-01
Seems like there is a workaround for the sound problem

      [http://www.linlap.com/wiki/hp+pavilion+dv8t+quad](http://www.linlap.com/wiki/hp+pavilion+dv8t+quad)

[INDENT] Sound:
Problem: Only the Subwoofer-Speaker was working.
Solution: Installing the most recent ALSA-Drivers with the ALSA Upgrade Script.
[http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810) 
 Problem2: After the Upgrade, it still does not recognise when a Headphone etc. is plugged in. As a workaround, I created a shortcut of alsamixer on the panel, where you can mute Speakers (0-9 keys) 
[/INDENT]  
-bob

---

